
- lock과 acquire를 사용해서, Blocking 큐를 구현함.
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

        #self.lock.acquire()
        self.thread_list.append(new_thread)
        print("현재 쓰레드풀:[[", self.thread_list, "]] 추가 할 쓰레드:",  new_thread)
        #self.lock.release()

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
