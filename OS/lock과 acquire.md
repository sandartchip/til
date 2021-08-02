
- lock과 acquire를 사용해서, Blocking 큐를 구현함.
- working 쓰레드를 새로 생성 후, 쓰레드 리스트에 추가 함. 
- 각 working 쓰레드에서 연산을 수행하고 나면, 쓰레드 풀 객체에서, 해당 쓰레드를 쓰레드 리스트에서 제거함.  
- 현재 쓰레드 "큐"가 아닌 이유는, FIFO구조가 아님.
- First In된게 First out되는게 아니라, 어떤 Job이 큐에 먼저 들어왔더라도 먼저 끝나면 먼저 빠짐.
- 따라서, FIFO나 LIFO와 같은 특정한, 순서가 없는 자료구조라고 할 수 있음.
- 

```python 
import threading
MAXTHREAD = 2
from queue import Queue
import threading
import time

class WorkerThread(threading.Thread):
    def __init__(self, parent, second): # 여기서 parent는, worker thread를 생성한 쓰레드 풀 객체 .
        super().__init__()
        self.second = second
        self.parent = parent

    def run(self):
        print("sub thread start {}".format(self.second))
        print(" --processing!!!!----- {}".format(self.second))
        time.sleep(self.second) # 각 쓰레드에서 처리하는 함수 적어주기.
        print("sub thread end ")

        self.parent.finish_new_thread(self) # 쓰레드 풀 pool 객체에 자신을 전달해서, 쓰레드 풀의 working queue에서 remove 시킴
```

```python
class WorkingThreadPool(object):
    def __init__(self):
        # 쓰레드 전체 정보 관리하는, 쓰레드 풀 역할 하는 클래스.
        self.thread_list = []
        self.max_thread = MAXTHREAD
        self.lock = threading.Lock()

    def get_thread_state(self):
        print("쓰레드 전체 갯수", self.max_thread)

    def make_and_run_new_thread(self, second):
        print("job submit 요청에 대응하는 새로운 쓰레드 만들기")
        new_thread = WorkerThread(self, second) # 새로운 스레드 생성.

        # self.lock.acquire()
        self.thread_list.append(new_thread)
        print("현재 쓰레드풀:[[", self.thread_list, "]] 추가 할 쓰레드:",  new_thread)
        # self.lock.release()

        new_thread.start()

    def finish_new_thread(self, finished_thread):

        #self.lock.acquire()
        print("현재 쓰레드풀:[[", self.thread_list, "]]  제거 할 쓰레드:", finished_thread)

        self.thread_list.remove(finished_thread)

        print("연산후 쓰레드풀:", self.thread_list)
        #self.lock.release()


if __name__ == "__main__":
    pool = WorkingThreadPool()

    pool.make_and_run_new_thread(4)
    pool.make_and_run_new_thread(4)
    pool.make_and_run_new_thread(4)

```

### 결과

![image](https://user-images.githubusercontent.com/15938354/127854483-901012bf-74ca-4ed3-be7c-3970c41d360a.png)


- 첫 번째 pop 적용 할 때, 현재 쓰레드풀에 thread2를 제거 했는데, 
- 다음 phase의 현재 쓰레드풀에 thread2이 남아 있음. 
- 쓰레드1, 쓰레드2, 쓰레드3은 끝나는 시점이 거의 동일하기 때문에, **거의 동시에** 쓰레드풀의 finish_new_thread 를 호출함.
- 따라서, 첫 번째 제거 phase의  현재도 쓰레드 풀에 쓰레드가 3개 있었고 두 번째 제거 phase의 쓰레드 풀에도 쓰레드가 3개 있음.
- 동시에 쓰레드 여러개에서 thread_list 변수에 접근 하기 때문에 쓰레드 리스트의 변화 과정이 이상하게 보임.
- 동시에 여러 쓰레드의 영향을 받는 전역 변수는, lock을 걸어 줘야 함.
 

## lock 사용 
 
```python
 
    def make_and_run_new_thread(self, second):
        print("job submit 요청에 대응하는 새로운 쓰레드 만들기")
        new_thread = WorkerThread(self, second) # 새로운 스레드 생성.

        self.lock.acquire()
        
        self.thread_list.append(new_thread)
        print("현재 쓰레드풀:[[", self.thread_list, "]] 추가 할 쓰레드:",  new_thread)
        self.lock.release()

        new_thread.start()

    def finish_new_thread(self, finished_thread):

        self.lock.acquire()
        print("현재 쓰레드풀:[[", self.thread_list, "]]  제거 할 쓰레드:", finished_thread)

        self.thread_list.remove(finished_thread)

        print("연산후 쓰레드풀:", self.thread_list)
        self.lock.release() # release를 하지 않으면,  처음 제거 작업 수행 한 쓰레드가 해당 코드를 점유하여, 다음 phase로 나가지 않음.
        
        

if __name__ == "__main__":
    pool = WorkingThreadPool()

    pool.make_and_run_new_thread(4)
    pool.make_and_run_new_thread(4)
    pool.make_and_run_new_thread(4)

```

## release 하지 않으면
![image](https://user-images.githubusercontent.com/15938354/127859271-5f7d40d3-5a04-485f-90c0-253e8375d326.png)

이 상태에서 무한 대기.


## 정상 작동 결과

![image](https://user-images.githubusercontent.com/15938354/127858113-93520051-3c20-49bb-a3a1-8b1bbf90d550.png)


## 의문
- 쓰레드를 새로 만들고, run하는 과정도 거의 동시에 시작되었는데, lock을 걸어주지 않아도 동기화가 제대로 된다.
- 이유가 있을까? 
- 뇌피셜로는, 쓰레드를 만드는 데 많은 자원을 소모하기 때문에, 즉, WorkerThread() 호출 자체에 시간이 소모되어, 미묘한 시간차가 생겨 쓰레드 리스트가 동시에 제어되지 않아서 정상적으로 동작하는 것 처럼 보이는 게 아닐까 함.
- 하지만 혹시 모르니 쓰레드 추가 작업에서도 쓰레드 리스트를 lock을 사용하는게 순서 상 더 명확하지 않을 까 함.
