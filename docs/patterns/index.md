# 算法套路

每个套路记：**识别信号**（看到什么就该想到它）、**模板**、**代表题**。

| 套路 | 识别信号 | 代表题 |
|---|---|---|
| 双指针 | 有序数组、两端逼近、原地修改 | Two Sum II、Container With Most Water |
| 滑动窗口 | 连续子数组 / 子串、“最长 / 最短满足条件” | Longest Substring Without Repeating Characters |
| 二分查找 | 有序、单调、“最小的满足条件的值” | Binary Search、Koko Eating Bananas |
| BFS | 最短步数、层序 | Binary Tree Level Order Traversal、Rotting Oranges |
| DFS / 回溯 | 列出所有方案、排列组合 | Subsets、Permutations |
| 动态规划 | 求最值 / 方案数，问题可拆成重叠子问题 | Climbing Stairs、House Robber |
| 单调栈 | “下一个更大 / 更小的元素” | Daily Temperatures |
| 拓扑排序 | 依赖关系、先修课程 | Course Schedule |
| 并查集 | 连通性、分组 | Number of Provinces |

## 模板示例：滑动窗口

```python
def sliding_window(s):
    window = {}
    left = 0
    best = 0
    for right, ch in enumerate(s):
        window[ch] = window.get(ch, 0) + 1          # 右边扩
        while window[ch] > 1:                        # 不满足条件就收缩
            window[s[left]] -= 1
            left += 1
        best = max(best, right - left + 1)           # 更新答案
    return best
```
