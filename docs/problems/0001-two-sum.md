# 3.1 &nbsp; Two Sum

!!! question

    给定整数数组 `nums` 和目标值 `target`，找出和为 `target` 的两个数的下标。每组输入恰好只有一个答案，同一个元素不能用两次。

    [LeetCode 1. Two Sum](https://leetcode.com/problems/two-sum/){ .rounded-button }

## 3.1.1 &nbsp; 三问

1. **暴力解是什么？** 两层循环，枚举所有两个数的组合。
2. **暴力慢在哪？** 每到一个数，都要从头再找一遍“另一个数”。
3. **怎么去掉重复？** 用哈希表记住见过的数和下标，每个数只需查一次“`target - x` 见过没有”。

## 3.1.2 &nbsp; 代码实现

=== "Python"

    ```python title="two_sum.py"
    def two_sum(nums: list[int], target: int) -> list[int]:
        seen = {}  # 值 -> 下标
        for i, x in enumerate(nums):
            if target - x in seen:
                return [seen[target - x], i]
            seen[x] = i  # 先查再存，避免自己配自己
        return []
    ```

=== "Java"

    ```java title="TwoSum.java"
    int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> seen = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int need = target - nums[i];
            if (seen.containsKey(need)) return new int[]{seen.get(need), i};
            seen.put(nums[i], i);
        }
        return new int[0];
    }
    ```

=== "C++"

    ```cpp title="two_sum.cpp"
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> seen;
        for (int i = 0; i < nums.size(); i++) {
            int need = target - nums[i];
            if (seen.count(need)) return {seen[need], i};
            seen[nums[i]] = i;
        }
        return {};
    }
    ```

## 3.1.3 &nbsp; 复杂度分析

暴力解要比较所有数对，共 \( \frac{n(n-1)}{2} \) 次，时间复杂度 \( O(n^2) \)。

哈希表解法每个元素只访问一次：

- **时间复杂度** \( O(n) \)：遍历一次，哈希表查找和插入平均 \( O(1) \)。
- **空间复杂度** \( O(n) \)：最坏情况下哈希表存下所有元素。

!!! tip "卡点"

    一定要**先查再存**。如果先存，`nums = [3], target = 6` 时会把 3 和自己配成一对。

??? note "面试 follow-up"

    - 如果数组已排序？→ 双指针，空间降到 \( O(1) \)。
    - 如果要返回所有不重复的组合？→ 排序 + 双指针，跳过重复值。
