#algorithm
#linkedlist
#leetcode
#interviewprep

[[linked list]]

### question/problem: 
- reverse a linked list; return the head

### idea:
- keep three cursors

### time complexity:
- o(n)

### space complexity:
- no extra space

### working code:
``` python
def reverseList(self, head):
	front = head
	behind = None
	cur = head
	
	while(front):
		cur = front
		front = front.next
		cur.next = behind
		behind = cur
	
	return cur
```

