# 98. Validate Binary Search Tree

### Approach:
We can create a recursive helper method isValid to verify if the given binary tree is a valid Binary Search Tree (BST). The helper method takes three parameters: the current node (curr), a lower bound (min), and an upper bound (max). The function enforces the BST property by ensuring that every node's value lies within the appropriate range defined by its ancestors. Specifically, for a node to be valid, its value must be greater than the min value and less than the max value. The algorithm traverses the tree recursively: it first checks the current node against its bounds, then moves to the left subtree (updating the upper bound to the current node's value), and then to the right subtree (updating the lower bound to the current node's value). If at any point the node's value violates the BST property, the function immediately returns false.

The base case for the recursion is when the curr node is null, which indicates that the traversal has reached the end of a branch. At this point, the function returns true, meaning all nodes along that path are valid. The algorithm ultimately returns true only if all recursive calls return true, confirming that every node in the tree satisfies the BST property.

### Code:
```
class Solution {
    public boolean isValidBST(TreeNode root) {
        return isValid(root, null, null);
    }
    private static boolean isValid(TreeNode curr, Integer min, Integer max) {
        if (curr == null) {
            return true;
        }
        if ((min != null && curr.val <= min) || (max != null && curr.val >= max)) {
            return false;
        }
        return isValid(curr.left, min, curr.val) && isValid(curr.right, curr.val, max);
    }
}
```