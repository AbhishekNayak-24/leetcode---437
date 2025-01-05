# leetcode---437
Path Sum III
// CODE IN JAVA
class Solution {
    public int pathSum(TreeNode root, int targetSum) {
        if (root == null) return 0;

        // Count paths starting from the current node
        int pathsFromRoot = countPathsFromNode(root, targetSum);

        // Count paths in the left and right subtrees
        int pathsInLeftSubtree = pathSum(root.left, targetSum);
        int pathsInRightSubtree = pathSum(root.right, targetSum);

        // Total paths
        return pathsFromRoot + pathsInLeftSubtree + pathsInRightSubtree;
    }

    private int countPathsFromNode(TreeNode node, long targetSum) {
        if (node == null) return 0;

        int paths = 0;

        // Check if the current node's value matches the target sum
        if (node.val == targetSum) {
            paths++;
        }

        // Recursively check for paths in the left and right subtrees
        paths += countPathsFromNode(node.left, targetSum - node.val);
        paths += countPathsFromNode(node.right, targetSum - node.val);

        return paths;
    }
}
