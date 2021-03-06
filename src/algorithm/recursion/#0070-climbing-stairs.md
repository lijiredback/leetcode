# 70.爬楼梯(easy)

## 题目描述

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

**注意**：给定 n 是一个正整数。

示例1:
```
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
```

示例2:
```
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶
```

## 解法

+ 思路1:
  - 第一级台阶: 1种方法(1)
  - 第二级台阶: 2种方法(11/2)
  - 第三级台阶: 3种方法(从第一级爬两级，也可以从第二级爬一级)
  - => f(n) = f(n-1) + f(n-2)

+ 思路2: 假设 n = 4，可以有两种选择
  - 先爬 1 级，还有 3 级要爬（因此，爬 3 级有几种方法）
  - 先爬 2 级，还有 2 级要爬（因此，爬 2 级有几种方法）
  - => f(4) = f(3) + f(2)
    

### 1. 递归

+ 复杂度分析
  - 时间复杂度: O(2^n)
  - 空间复杂度: O(n)

```
/**
 * @param {number} n
 * @return {number}
 */

var climbStairs = function(n) {
    // 终止条件
    if (n === 1) return 1
    if (n === 2) return 2

    // 处理当前层，下探到下一层
    return climbStairs(n - 1) + climbStairs(n - 2)
}
```

### 2. 动态规划