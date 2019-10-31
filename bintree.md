# bintree

- 二叉树初始化

递归初始化二叉树，如果左子树为空，则初始化左子树，如果左子树不为空，则将左子树递归传给初始化函数

```
public class BinTree {

    private TreeNode root = null;

    private class TreeNode {
        TreeNode leftChild;
        TreeNode rightChild;
        int data;

        public TreeNode(int data) {
            this.leftChild = null;
            this.rightChild = null;
            this.data = data;
        }
    }

    public void buildTree(TreeNode node, int data) {
        if (root == null) {
            root = new TreeNode(data);
        } else {
            if (data < node.data) {
                //如果没有这个节点，就创建
                if (node.leftChild == null) {
                    node.leftChild = new TreeNode(data);
                } else {
                    //如果已经有这个节点，则递归调用buildtree方法，接着往下层迭代
                    buildTree(node.leftChild, data);
                }
            } else {
                if (node.rightChild == null) {
                    node.rightChild = new TreeNode(data);
                } else {
                    buildTree(node.rightChild, data);
                }
            }
        }
    }

    public static void main(String[] args) {
        BinTree binTree = new BinTree();
        int[] arr = {10, 5, 4, 2, 5, 7, 8, 9, 10};
        for (int i = 0; i < arr.length; i++) {
            binTree.buildTree(binTree.root, arr[i]);
        }
    }

}
```

