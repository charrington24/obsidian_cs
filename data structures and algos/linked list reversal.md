#algorithm
#linkedlist
#leetcode
#interviewprep

[[linked list]]

### question/problem: 
- reverse a linked list; return the head

### idea:
- keep three cursors: a front, back, and middle/current
- initialize back to null and front to head
- while front is defined, 
- move current up to front
- route current's next to the back cursor
- increment front and back by one (front to front.next and back to current)
- when front runs out of bounds, current should be the new head aka end of the old list

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

