#algorithm
#leetcode
#interviewprep
#slidingwindow

### question/problem: 
- given an array of numbers representing stock price on each day, return the max profit you can make from buying one day and selling at a later date
### idea:
- brute force: we can nest loops and check every difference where i < j
	- this is O(n^2) though so not optimal
- sliding window: one pass. We know that the lowest number will be the best day to buy, so we store the lowest number we've encountered so far. We also store our largest profit so far. We check the difference between each new price and the current lowest, updating profit if the difference is greater than the stored largest one. 

### time complexity:
- O(n) with the sliding window/one pass approach

### space complexity:

### working code:
``` python

lowest = prices[0]
profit = 0

for i in range(len(prices)):
if(prices[i] < lowest):
lowest = prices[i]
if((prices[i] - lowest) > profit):
profit = (prices[i] - lowest)
return profit```

