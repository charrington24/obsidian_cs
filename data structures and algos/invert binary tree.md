#algorithm
#leetcode
#interviewprep
#tree
#binarytree


### question/problem: 
- given the root of a binary tree, invert it
### idea:
- recursive approach: for each node in the tree, replace its left child with an inverted right child and its right child with an inverted left child
- base case: no node, return
- at the end, return the node (this will echo up the call stack)
### time complexity:
- O(n) where n is the number of nodes
### space complexity:
- temp variable used for swapping so like O(n) but really sm like n/2

### working code:
``` python
def invertTree(self, root):

if not(root):
	return

temp = root.left
root.left = self.invertTree(root.right)
root.right = self.invertTree(temp)

return(root)
```

