#algorithm
#linkedlist
#leetcode
#interviewprep

### idea:
- traverse list
- push each value to a stack  
- read from stack
- compare

### time complexity:
- O(n)- iterating through list

### space complexity:
- O(n)- constructing a stack

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

https://www.geeksforgeeks.org/function-to-check-if-a-singly-linked-list-is-palindrome/
