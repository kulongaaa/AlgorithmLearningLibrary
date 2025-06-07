# 题目描述
给定一个二叉搜索树的根节点 root ，和一个整数 k ，请你设计一个算法查找其中第 k 小的元素（从 1 开始计数）。

 

示例 1：


![Binary Tree](https://assets.leetcode.com/uploads/2021/01/28/kthtree1.jpg)
输入：root = [3,1,4,null,2], k = 1
输出：1
示例 2：

![Binary Tree](https://assets.leetcode.com/uploads/2021/01/28/kthtree2.jpg)

输入：root = [5,3,6,2,4,null,null,1], k = 3
输出：3



# 答案

```

function kthSmallest(root: TreeNode | null, k: number): number {
    const stack: TreeNode[] = [];
    let current: TreeNode | null = root;
    let count = 0;

    while (current !== null || stack.length > 0) {
        // 遍历到最左节点
        while (current !== null) {
            stack.push(current);
            current = current.left;
        }

        // 访问当前节点
        current = stack.pop()!;
        count++;

        if (count === k) {
            return current.val;
        }

        // 转向右子树
        current = current.right;
    }

    // 若树中节点数少于k，返回-1（根据题意，k始终有效，此情况不会发生）
    return -1;
}

```