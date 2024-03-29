#algorithm
#leetcode
#interviewprep

can be [[linked list]]
can be [[array]]
### question/problem: 
- given two sorted lists, merge them into one sorted list and return it
### idea:
- make an output list with a dummy head (if linked list; if array, just init an empty list)
- start a cursor at the beginning of each list
- add the cursor with the lower value to the output list and increment it
- if you hit the end of either list, attach the remainder of the remaining list to the output list
#### caution:
- insertion at beginning or end of list- avoid this edge case with a dummy node

### time complexity:
- o(n) where n is the length of the shorter list

### space complexity:
- o(n+m) additional space for output 

### working code:
``` python
	def mergeTwoLists(self, list1, list2):
	
	cur1 = list1
	cur2 = list2
	output = ListNode(None)
	outputHead = output
	
	while(cur1 and cur2):
		if(cur1.val < cur2.val):
			output.next = cur1
			cur1 = cur1.next
		else:
			output.next = cur2
			cur2 = cur2.next
			output = output.next
			
	if(cur1):
		output.next = cur1
	elif(cur2):
		output.next = cur2
	
	return outputHead.next
```

