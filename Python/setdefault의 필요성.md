### 일반적인 사전 기본값 처리
아래 코드는 주어진 단어에 들어있는 각 알파벳 글자의 수를 세어서 사전에 저장해주는 함수입니다.

```python 
def countLetters(word):
    counter = {}
    for letter in word:
        if letter not in counter:
            counter[letter] = 0
        counter[letter] += 1
    return counter
````

for 루프 안에 if 조건절을 통해서 counter 사전에 어떤 글자가 키(key)로 존재하지 않는 경우, 해당 키에 대한 기본값을 0으로 세팅해주고 있는데요. 이러한 코딩 패턴은 파이썬에서 사전을 사용할 때 상당히 자주 접할 수 있는데, 코드 가독성 측면에서는 이렇게 사소한 처리가 주요 흐름을 파악을 하는데 방해가 되기도 합니다.

##### 나은 방법: dict.setdefault
위와 같은 if 조건절을 피할 수 있도록 파이썬의 사전(dictionary) 자료구조는 setdefault 함수를 제공합니다. 첫번째 인자로 키(key)값, 두번째 인자로 기본값(default value)를 넘기면 되는데요.

```python
def countLetters(word):
    counter = {}
    for letter in word:
        counter.setdefault(letter, 0)
        counter[letter] += 1
    return counter
```
