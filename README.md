本文件构建启发自 30-seconds-of-code，由 JS 文件打包生成 MD 文件

# CodeWars

- 非常好的刷题平台，面向测试用例编程，`cmd + s` 即可跑测试用例
- 题目有趣味且实用，习得的编码技巧很容易用到日常工作中
- 利用筛选条件例如【正则相关 + 好评度 + 难度】，能较为全面的掌握一个方向的知识
- 完成后发现更好的答案，重写一遍，有利于自己的编码习惯国际化

另一个刷题战场：[LeetCode](https://github.com/ringcrl/LeetCode)

# 个人主页

实时分数：

![](https://static.chenng.cn/api/dynamic_image/codewars)

https://www.codewars.com/users/ringcrl

# 刷题参数

- Sort By: Positive Feedback，>= 90%
- Language：JavaScript
- Status：Approved
- Progress：Kata I hava not completed
- Diffculty：To 6 kyu

[每日刷题](https://www.codewars.com/kata/search/my-languages?q=&xids=completed&beta=false&order_by=satisfaction_percent+desc%2Ctotal_completed+desc)

# 已刷题目

# 位运算

## 不用加减乘除做加法.js

```js
/**
 * 写一个函数，求两个整数之和，要求不得使用 +、-、*、/ 四则运算符号
 * 
 * a ^ b 表示没有考虑进位的情况下两数的和，(a & b) << 1 就是进位
 * 递归会终止的原因是 (a & b) << 1 最右边会多一个 0
 * 那么继续递归，进位最右边的 0 会慢慢增多，最后进位会变为 0，递归终止
 */
function Add(a, b) {
  return b == 0 ? a : Add(a ^ b, (a & b) << 1);
}

console.log(Add(2, 3));
```

## 二进制中1的个数.js

```js
/**
 * 输入一个整数，输出该数二进制表示中 1 的个数
 */
function numberOf1(n) {
  let cnt = 0;
  while (n !== 0) {
    cnt++;
    n &= (n - 1);
  }
  return cnt;
}

console.log(numberOf1(10));
// (10).toString(2) 1010
```

## 数组中只出现一次的数字.js

```js
/**
 * 一个整型数组里除了一个数字之外，其他的数字都出现了两次，找出这两个数
 * 
 * 1. 两个相同的数字 ^ 结果是 0
 * 2. 0 ^ n 结果是 n
 * 3. n ^ m ^ n 结果是 m
 */
const singleNumber = function (nums) {
  let diff = nums.reduce((prev, curr) => {
    return prev ^= curr;
  });
  return diff;
};

console.log(singleNumber([4, 1, 2, 1, 2]));
```

# 动态规划

## 丑数.js

```js
/**
 * 把只包含因子 2、3 和 5 的数称作丑数（Ugly Number）。
 * 例如 6、8 都是丑数，但 14 不是，因为它包含因子 7。
 * 习惯上我们把 1 当做是第一个丑数。
 * 求按从小到大的顺序的第 N 个丑数
 */
function getNUglyNumber(n) {
  if (n <= 6) {
    return n;
  }

  let i2 = 0;
  let i3 = 0;
  let i5 = 0;
  const dp = new Array(n).fill(0);
  dp[0] = 1;
  for (let i = 1; i < n; i++) {
    const next2 = dp[i2] * 2;
    const next3 = dp[i3] * 3;
    const next5 = dp[i5] * 5;
    dp[i] = Math.min(
      next2,
      Math.min(next3, next5),
    );
    if (dp[i] === next2) {
      i2++;
    }
    if (dp[i] === next3) {
      i3++;
    }
    if (dp[i] === next5) {
      i5++;
    }
  }
  return dp[n - 1];
}

console.log(getNUglyNumber(10));
```

## 变态跳台阶.js

```js

```

## 斐波那契数列.js

```js

```

## 正则表达式匹配.js

```js

```

## 矩阵覆盖.js

```js

```

## 跳台阶.js

```js

```

# 哈希

## 第一个只出现一次的字符位置.js

```js
/**
 * 在一个字符串中找到第一个只出现一次的字符，并返回它的位置
 */
function FirstNotRepeatingChar(str) {
  const cnts = Array(str.length).fill(0);
  for (let i = 0; i < str.length; i++) {
    cnts[str[i]]++;
  }
  for (let i = 0; i < str.length; i++) {
    if (cnts[str[i]] === 1) {
      return i;
    }
  }
  return -1;
}

console.log(FirstNotRepeatingChar([1, 2, 3, 4, 3, 2, 1]));
```

# 回溯

## 机器人的运动范围.js

```js

```

## 矩阵中的路径.js

```js

```

# 堆

## 字符流中第一个不重复的字符.js

```js

```

## 数据流中的中位数.js

```js

```

## 最小的K个数.js

```js

```

## 滑动窗口的最大值.js

```js

```

# 字符串

## 字符串的排列.js

```js

```

## 字符流中第一个不重复的字符.js

```js

```

## 把数组排成最小数.js

```js

```

## 替换空格.js

```js

```

## 正则表达式匹配.js

```js
/**
 * 请实现一个函数用来匹配包括 '.' 和 '*' 的正则表达式。
 * 模式中的字符 '.' 表示任意一个字符，
 * 而 '*' 表示它前面的字符可以出现任意次（包含 0 次）。
 * 在本题中，匹配是指字符串的所有字符匹配整个模式。
 * 例如，字符串 "aaa" 与模式 "a.a" 和 "ab*ac*a" 匹配，
 * 但是与 "aa.a" 和 "ab*a" 均不匹配。
 * 
 * 这题的正解的 dp 方程，不过 JS 可以直接使用正则啊
 */
function match(s, p) {
  const reg = new RegExp(`^${p}$`);
  return reg.test(s);
}
```

## 表示数值的字符串.js

```js

```

# 排序

## 最小的K个数.js

```js

```

# 数组

## 二维数组的查找.js

```js
/**
 * 给定一个二维数组，其每一行从左到右递增排序，从上到下也是递增排序。
 * 给定一个数，判断这个数是否在该二维数组中。
 * 
 * Consider the following matrix:
 * [
 *  [1,   4,  7, 11, 15],
 *  [2,   5,  8, 12, 19],
 *  [3,   6,  9, 16, 22],
 *  [10, 13, 14, 17, 24],
 *  [18, 21, 23, 26, 30]
 * ]
 * 
 * Given target = 5, return true.
 * Given target = 20, return false.
 */
function matrixFind(target, matrix) {
  if (
    matrix === null ||
    matrix.length === 0 ||
    matrix[0].length === 0
  ) {
    return false;
  }

  let rows = matrix.length;
  let cols = matrix[0].length;
  let row = 0;
  let col = cols - 1;
  while (row <= rows - 1 && col >= 0) {
    if (target === matrix[row][col]) {
      return true;
    } else if (target > matrix[row][col]) {
      row++;
    } else {
      col--;
    }
  }
  return false;
}

const matrix = [
  [1, 4, 7, 11, 15],
  [2, 5, 8, 12, 19],
  [3, 6, 9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30],
]

console.log(matrixFind(5, matrix));
```

## 把数组排成最小的数.js

```js
/**
 * 输入一个正整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个。
 * 例如输入数组 {3，32，321}，则打印出这三个数字能排成的最小数字为 321323
 * 
 * 可以看成是一个排序问题，在比较两个字符串 S1 和 S2 的大小时
 * 应该比较的是 S1+S2 和 S2+S1 的大小
 * 如果 S1+S2 < S2+S1，那么应该把 S1 排在前面，否则应该把 S2 排在前面
 */

function printMinNumber(nums) {
  if (nums === null || nums.length === 0) {
    return '';
  }

  for(let i = 0; i < nums.length; i++) {
    nums[i] = nums[i] + '';
  }
  nums.sort((s1, s2) => (s1 + s2) - (s2 + s1));
  return nums.reduce((prev, curr) => {
    return prev + curr;
  }, '');
}

console.log(printMinNumber([3, 32, 321]));
```

## 数组中重复的数字.js

```js
/**
 * 在一个长度为 n 的数组里的所有数字都在 0 到 n-1 的范围内。
 * 数组中某些数字是重复的，但不知道有几个数字是重复的，也不知道每个数字重复几次。请找出数组中任意一个重复的数字。
 * 
 * Input:
 * {2, 3, 1, 0, 2, 5}
 * 
 * Output:
 * 2
 */

/**
 *
 * @param {Array} nums 
 */
function duplicate(nums) {
  if (nums === null || nums.length === 0) { return false; }

  const map = {};

  for (let i = 0; i < nums.length; i++) {
    if (map[nums[i]]) {
      return nums[i];
    }
    map[nums[i]] = 1;
  }

  return false;
}

console.log(duplicate([2, 3, 1, 0, 2, 5]));
```

## 构建乘积数组.js

```js
/**
 * 给定一个数组 A[0, 1,..., n-1]，请构建一个数组 B[0, 1,..., n-1]
 * 其中 B 中的元素 B[i]=A[0]*A[1]*...*A[i-1]*A[i+1]*...*A[n-1]
 * 要求不能使用除法
 */
function multiply(arr) {
  const res = [];
  let product = 1;
  const len = arr.length;
  for (let i = 0; i < len; i++) {
    res[i] = product;
    product *= arr[i];
  }
  product = 1;
  for (let i = len - 1; i >= 0; i--) {
    res[i] *= product;
    product *= arr[i];
  }
  return res;
}

console.log(multiply([1, 2, 3, 4, 5]));
```

## 调整数组顺序使奇数位于偶数前面.js

```js
/**
 * 调整数组顺序使奇数位于偶数前面
 * 需要保证偶数和偶数之间的相对位置不变
 */
function reOrderArray(nums) {
  // 奇数个数
  let oddCount = 0;
  for (const num of nums) {
    if (num % 2 === 1) {
      oddCount++;
    }
  }

  let i = 0;
  let k = 0;
  j = oddCount;
  const res = [];
  while (k < nums.length) {
    const num = nums[k];
    if (num % 2 === 1) {
      res[i++] = num;
    } else {
      res[j++] = num;
    }
    k++;
  }

  return res;
}

console.log(reOrderArray([1, 2, 3, 4, 5]));
```

## 连续子数组的最大和.js

```js
/**
 * {6, -3, -2, 7, -15, 1, 2, 2}
 * 连续子数组的最大和为 8（从第 0 个开始，到第 3 个为止）
 */
function FindGreatestSumOfSubArray(nums) {
  if (nums === null || nums.length === 0) {
    return 0;
  }

  let greatestSum = Number.MIN_SAFE_INTEGER;
  let sum = 0;
  for (const num of nums) {
    sum = sum <= 0 ? num : num + sum;
    greatestSum = Math.max(greatestSum, sum);
  }

  return greatestSum;
}

console.log(FindGreatestSumOfSubArray([6, -3, -2, 7, -15, 1, 2, 2]));
```

## 逻辑运算.js

```js
/**
 * https://www.codewars.com/kata/logical-calculator/train/javascript
 * 
 * 逻辑运算
 * - 有点像 Ramda 模式
 * 
 * @param {array} array 
 * @param {'AND'|'OR'|'XOR'} op 
 */
function logicalCalc(array, op){
  const ops = {
    'AND': function (a, b) { return a && b; },
    'OR': function (a, b) { return a || b; },
    'XOR': function (a, b) { return a !== b; },
  }
  
  return array.reduce(ops[op]);
}
```

## 顺时针打印矩阵.js

```js
/**
 * 
 * [
 * [1, 2, 3, 4],
 * [5, 6, 7, 8],
 * [9, 10, 11, 12],
 * [13, 14, 15, 16],
 * ]
 * 
 * 矩阵顺时针打印结果为
 * 1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10
 */

const matrix = [
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9, 10, 11, 12],
  [13, 14, 15, 16],
]

function printMatrix(matrix) {
  const res = [];
  let r1 = 0;
  let r2 = matrix.length - 1;
  let c1 = 0;
  let c2 = matrix[0].length - 1;
  while (r1 <= r2 && c1 <= c2) {
    for (let i = c1; i <= c2; i++) {
      res.push(matrix[r1][c2]);
    }
    for (let i = r1 + 1; i <= r2; i++) {
      res.push(matrix[i][c2]);
    }
    if (r1 !== r2) {
      for (let i = c2 - 1; i >= c1; i--) {
        res.push(matrix[r2][i]);
      }
    }
    if (c1 !== c2) {
      for (let i = r2 - 1; i > r1; i--) {
        res.push(matrix[i][c1]);
      }
    }
    r1++;
    r2--;
    c1++;
    c2--;
  }
  return res;
}

console.log(printMatrix(matrix));
```

# 查找

## 二维数组的查找.js

```js

```

## 数字的排列数组中出现的次数.js

```js

```

## 旋转数组的最小数字.js

```js

```

# 栈

## 包含min函数的栈.js

```js

```

## 栈的压入弹出序列.js

```js

```

## 用两个栈实现队列.js

```js

```

# 树

## 二叉搜索树与双向链表.js

```js

```

## 二叉搜索树的后序遍历序列.js

```js

```

## 二叉搜索树的第K个结点.js

```js

```

## 二叉树中和为某一值的路径.js

```js

```

## 二叉树的下一个结点.js

```js

```

## 二叉树的深度.js

```js

```

## 从上往下打印二叉树.js

```js

```

## 对称的二叉树.js

```js

```

## 平衡二叉树.js

```js

```

## 序列化二叉树.js

```js

```

## 把二叉树打印成多行.js

```js

```

## 按之字形顺序打印二叉树.js

```js

```

## 数据流中的中位数.js

```js

```

## 树的子结构.js

```js

```

## 重建二叉树.js

```js

```

# 深度优先

## 机器人的运动范围.js

```js

```

# 贪心

## 连续子数组的最大和.js

```js

```

# 递归

## 最大长度单词分词.js

```js
/**
 * https://www.codewars.com/kata/word-segmentation-maxmatch/train/javascript
 * 
 * MaxMatch 句子分词
 * - 找到最大长度单词进行分词
 * 
 * @param {string} sentence 
 */
function maxMatch(sentence){
  for (let i = sentence.length; i > 0; i--) {
    const word = sentence.slice(0, i);
    if (
      i === 1 ||
      VALID_WORDS.has(word)
    ) {
      return [word].concat(maxMatch(sentence.slice(i)));
    }
  }  
  
  return [];
}
```

# 链表

## 两个链表的第一个公共结点.js

```js

```

## 二叉搜索树与双向链表.js

```js

```

## 从头到尾打印链表.js

```js

```

## 删除链表中重复的结点.js

```js

```

## 反转链表.js

```js

```

## 合并两个排序的链表.js

```js

```

## 把字符串转换成整数.js

```js

```

## 链表中倒数第K个结点.js

```js

```

## 链表中环的入口结点.js

```js

```

# 队列

## 用两个栈实现队列.js

```js

```

