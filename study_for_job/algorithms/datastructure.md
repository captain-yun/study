## 00. 요세푸스 문제
>**Code** 📄
```python
n, k = map(int, input().split())  
alive = []  
answer = []  
  
for i in range(n):  
    alive.append(i+1)  
  
p = k - 1  
answer.append(str(alive.pop(p)))  
  
while len(alive) > 0:  
    p -= 1  
    p = (p + k) % len(alive)  
  
    answer.append(str(alive.pop(p)))  
  
print("<",", ".join(answer)[:],">", sep='')
```

## 01. 스택
>**Code** 📄
```python
from collections import deque  
import sys

n = int(sys.stdin.readline())  
cmd = []  
stack = deque()  
  
for _ in range(n):  
    cmd = sys.stdin.readline().split()  
    if cmd[0] == "push":  
        stack.append(cmd[1])  
    elif cmd[0] == 'pop':  
        if len(stack):  
            print(stack.pop())  
        else:  
            print(-1)  
    elif cmd[0] == 'size':  
        print(len(stack))  
    elif cmd[0] == 'empty':  
        if len(stack) > 0:  
            print(0)  
        else:  
            print(1)  
    elif cmd[0] == 'top':  
        if len(stack) > 0:  
            print(stack[-1])  
        else:  
            print(-1)
```

## 02. 괄호
>**Code** 📄
```python
import sys  
  
n = sys.stdin.readline()  
stack = []  
  
for _ in range(n):  
    s = sys.stdin.readline()  
    for i in range(len(s)):  
        if s[i] == '(':  
            stack.append(s[i])  
        else:  
            if stack:  
                stack.pop()  
            else:  
                print("NO")  
                break  
 if stack:  
        print("NO")  
    else:  
        print("YES")
```

## 03. 큐2 
>**Code** [📄](https://www.acmicpc.net/source/29224086) 
```python
from collections import deque  
import sys

n = int(sys.stdin.readline())  
cmd = []  
q = deque()  
  
for _ in range(n):  
    cmd = sys.stdin.readline().split()  
    if cmd[0] == "push":  
        q.append(cmd[1])  
    elif cmd[0] == 'pop':  
        if len(q):  
            print(q.popleft())  
        else:  
            print(-1)  
    elif cmd[0] == 'size':  
        print(len(q))  
    elif cmd[0] == 'empty':  
        if len(q) > 0:  
            print(0)  
        else:  
            print(1)  
    elif cmd[0] == 'front':  
        if len(q) > 0:  
            print(q[0])  
        else:  
            print(-1)  
    elif cmd[0] == 'end':  
        if len(q) > 0:  
            print(q[-1])  
        else:  
            print(-1)
```

## 04. 카드2
>**Code** [📄](https://www.acmicpc.net/source/29223257) 

```python
from collections import deque

n = int(input())
stack = deque()
answer = 0

for i in range(n, 0, -1):
    stack.append(i)

while stack:
    v = stack.pop()
    if len(stack) == 0:
        answer = v
        break
    v = stack.pop()
    stack.insert(0, v)

print(answer)
```
> How solved?
* (1) **Pop** the upper number from the stack.
* (2) **Move** the number at the top to the bottom.
	* Repeat it until stack becomes empty.

## 05. 덱
>**Code** [📄](https://www.acmicpc.net/source/29224571) 

```python
from collections import deque
import sys

n = int(sys.stdin.readline())
cmd = []
deq = deque()

for _ in range(n):
    cmd = sys.stdin.readline().split()
    if cmd[0] == "push_back":
        deq.append(cmd[1])
    elif cmd[0] == "push_front":
        deq.insert(0, cmd[1])
    elif cmd[0] == 'pop_back':
        if len(deq) > 0:
            v = deq.pop()
            print(v)
        else:
            print(-1)
    elif cmd[0] == 'pop_front':
        if len(deq) > 0:
            v = deq.popleft()
            print(v)
        else:
            print(-1)
    elif cmd[0] == 'size':
        print(len(deq))
    elif cmd[0] == 'empty':
        if len(deq) > 0:
            print(0)
        else:
            print(1)
    elif cmd[0] == 'front':
        if len(deq) > 0:
            print(deq[0])
        else:
            print(-1)
    elif cmd[0] == 'back':
        if len(deq) > 0:
            print(deq[-1])
        else:
            print(-1)
```
