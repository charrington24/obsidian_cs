#algorithm 
#interviewprep 
#search
#binarysearch
## iterative:

### code:
```python
low = 0
high = len(nums) - 1

while(low <= high):
	mid = low + ((high - low) // 2)
	if(nums[mid] == target):
		return mid
	if(nums[mid] < target):
		low = mid + 1
	elif(nums[mid] > target):
		high = mid -1

return -1
```

### time complexity:

### space complexity:

## recursive:
### idea:

### code:

### time complexity:

### space complexity:
