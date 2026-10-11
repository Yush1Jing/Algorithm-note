# 1. Two Sum

- **链接**：<https://leetcode.com/problems/two-sum/>
- **套路**：哈希表
- **难度**：Easy

## 三问

1. **暴力解是什么？** 两层循环，枚举所有两个数的组合，O(n²)
2. **暴力慢在哪？** 每到一个数，都要从头再找一遍“另一个数”
3. **用什么办法去掉重复？** 用哈希表记住见过的数和下标，每个数只需查一次“`target - x` 见过没有”，O(n)

## 代码

```python
def twoSum(nums, target):
    seen = {}                      # 值 -> 下标
    for i, x in enumerate(nums):
        if target - x in seen:
            return [seen[target - x], i]
        seen[x] = i                # 先查再存，避免自己配自己
    return []
```

## 复杂度

- 时间：O(n)
- 空间：O(n)

## 卡点

- 先查再存的顺序：如果先存，`nums = [3]`、`target = 6` 时会把 3 和自己配成一对
