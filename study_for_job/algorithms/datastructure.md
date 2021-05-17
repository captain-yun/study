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

## 06. 스택 수열
>**Code** [📄 BoJ 1874번](https://www.acmicpc.net/source/29290296)
```python
import sys

stack = []
answer = []
n = int(sys.stdin.readline())

count = 1
for _ in range(n):

    target = int(sys.stdin.readline())

    while count <= target:
        stack.append(count)
        answer.append('+')
        count += 1

    if stack.pop() == target:
        answer.append('-')
    else:
        print("NO")
        exit()

for i in answer:
    print(i)
```
> How solved?
* Using stack
* At first glance, I thought it's gonna be solved with a specifically made the algorithm of how to push and pop the values.
> Refered Site
* https://assaeunji.github.io/python/2020-05-04-bj1874/

## 07. 후위 표기식2
>**Code** [📄 BoJ 1935번](https://www.acmicpc.net/submit/1935/29316682) 
```python
n = input()
expression = list(input())
ht = {}
stack = []

for e in expression:
    if e == '*':
        v1 = stack.pop()
        v2 = stack.pop()
        stack.append(v1 * v2)
    elif e == '/':
        v1 = stack.pop()
        v2 = stack.pop()
        stack.append(v2 / v1)
    elif e == '+':
        v1 = stack.pop()
        v2 = stack.pop()
        stack.append(v1 + v2)
    elif e == '-':
        v1 = stack.pop()
        v2 = stack.pop()
        stack.append(v2 - v1)
    else:
        if not ht.get(e):
            ht[e] = int(input())
            stack.append(ht[e])
        else:
            stack.append(ht[e])
print("%.2f" % stack[0])
```
> How solved?
* To get solve this problem, you should know how postfix works
* There are two common types of 

> Errors I ran into
* ValueError: invalid literal for int() with base 10: ''
	* ***ValueError*** is raised when an operation or function receives an argument that has the **right type** but **an inappropriate value**
		* int("2") returns 2
		* int("#") or int("A") or int(" ") raises ValueError exception because the each argument is an inappropriate value of which there is no way of expressing as Interger type.

> References https://en.wikipedia.org/wiki/Literal_(computer_programming)

## 08. 쇠막대기
>**Code** [📄 BoJ 10799번](https://www.acmicpc.net/source/29321259)
```python
s = input()
stack = []
answer = 0
for i in range(len(s)):
    if s[i] == '(':
        stack.append('(')
    elif s[i] == ')':
        if s[i-1] == '(':
            # it means it's a lazor, so cut the stick below.
            stack.pop()
            answer += len(stack)
        else:
            stack.pop()
            answer += 1
print(answer)
```
> How solved?
> 
## 09. 프린터 큐
>**Code** [📄 BoJ 1966번](https://www.acmicpc.net/source/29339409)
```
from collections import deque

def solution():

    how_many = int(input())
    ht = {}
    answer = 1

    for _ in range(how_many):
        n, m = map(int, input().split())

        priorities = deque(map(int, input().split()))
        answer = 1
        # 출력.
        while priorities:
            max_priority = max(priorities)
            val = priorities.popleft()
            if max_priority == val:
                # m이니?
                if m == 0:
                    print(answer)
                    break
                else:
                    answer += 1
                    m -= 1
            else:
                if m == 0:
                    m = len(priorities)
                else:
                    m -= 1
                priorities.append(val)

solution()
```



## 10. 풍선 터뜨리기
>**Code** [📄 BoJ 2346번](https://www.acmicpc.net/source/29329498)
```python
from collections import deque

def solution():
    n = int(input())
    balloons = deque()
    for i, val in enumerate(list(map(int, input().split()))):
        balloons.append([i+1, val])
    p = 0
    answer = []

    # i = 0, val = 1
    for _ in range(n):
        val = balloons[p][1]
        # 지우지말고 0으로
        answer.append(balloons[p][0])
        balloons[p][1] = 0
        if len(answer) == n:
            break
        # move
        if val > 0:
            p = move_right(balloons, p, val)
        elif val < 0:
            p = move_left(balloons, p, val)

    print(*answer)

def move_right(balloons, p, val):
    while val != 0:
        if p == len(balloons) - 1:
            p = 0
        else:
            p += 1
        if balloons[p][1] != 0:
            val -= 1
    return p

def move_left(balloons, p, val):
    while val != 0:
        if p == 0:
            p = len(balloons) - 1
        else:
            p -= 1
        if balloons[p][1] != 0:
            val += 1
    return p

solution()
```

## 11. 괄호의 값
>**Code** [📄 BoJ 2504번](https://www.acmicpc.net/submit/2504/29338609)
```python
def solution():  
    stack = []  
  
    pars = input()  
    for p in pars:  
        if p == ')':  
            if len(stack) == 0:  
                print(0)  
                exit(0)  
            top = stack.pop()  
            if top == '(':  
                stack.append(2)  
            elif top == '[':  
                print(0)  
                exit(0)  
            # numeric  
  else:  
                if stack:  
                    v = stack.pop()  
                else:  
                    print(0)  
                    exit(0)  
                if v == '(':  
                    stack.append(2 * top)  
                else:  
                    print(0)  
                    exit(0)  
        elif p == ']':  
            if len(stack) == 0:  
                print(0)  
                exit(0)  
            top = stack.pop()  
            if top == '[':  
                stack.append(3)  
            elif top == '(':  
                print(0)  
                exit(0)  
            # numeric  
  else:  
                if stack:  
                    v = stack.pop()  
                else:  
                    print(0)  
                    exit(0)  
                if v == '[':  
                    stack.append(3 * top)  
                else:  
                    print(0)  
                    exit(0)  
        else:  
            stack.append(p)  
  
        if len(stack) > 1:  
            if str(stack[-1]).isnumeric() and str(stack[-2]).isnumeric():  
                stack.append(stack.pop() + stack.pop())  
    answer = 0  
  for s in stack:  
        if not str(s).isnumeric:  
            print(0)  
        else:  
            answer += s  
    print(answer)  
  
solution()
```
> How solved?
> 

## 12. 괄호 제거
>**Code** [📄 BoJ 2800번]

## 13. 탑
>**Code** [📄 BoJ 2493번]

## 14. 후위 표기식
>**Code** [📄 BoJ 1918번]
