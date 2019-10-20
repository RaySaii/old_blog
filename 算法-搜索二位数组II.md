## 题目

编写一个高效的算法来搜索 *m* x *n* 矩阵 matrix 中的一个目标值 target。该矩阵具有以下特性：

- 每行的元素从左到右升序排列。
- 每列的元素从上到下升序排列。

**示例:**

现有矩阵 matrix 如下：

```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```

给定 target = `5`，返回 `true`。

给定 target = `20`，返回 `false`。

## 解法

依题目开始分析，我们可以发现：

1. 如果`target`大于右上角的数，那他一定在这个数的下面。
2. 如果`target`小于右上角的数，那他一定在这个数的左边。

所以这样分析下来，问题就可以简化为，从右上角开始遍历，让游标如上面的逻辑变动，就可以得到结果了。

```js
/**
 * @param {number[][]} matrix
 * @param {number} target
 * @return {boolean}
 */
var searchMatrix = function(matrix, target) {
    if(matrix.length==0)return false
    let row=0
    let col=matrix[0].length-1
    while(row<matrix.length&&col>=0){
        let cur=matrix[row][col]
        if(target>cur){
            row++
        }else if(target<cur){
            col--
        }else{
            return true
        }
    }
    return false
};
```

