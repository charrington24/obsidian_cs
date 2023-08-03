#algorithm
#linkedlist
#leetcode
#interviewprep


### idea:


### working code:
``` python
def solution(l):
cur = l
stack = []
if(cur == None):
	return True

while(cur):
	stack.append(cur.value)
	cur = cur.next
	cur = l

while(cur.next):
	if (stack.pop() != cur.value):
		return False
	cur = cur.next

return True
```
