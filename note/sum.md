### 求两位数之和

> 给定一个整数数组 nums  和一个目标值 target，请你在该数组中找出和为目标值的那   两个   整数，并返回他们的数组下标。

> 你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

> 示例:

> 给定 nums = [2, 7, 11, 15], target = 9

> 因为 nums[0] + nums[1] = 2 + 7 = 9
> 所以返回 [0, 1]

> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/two-sum
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

### 解法 1

#### 思路 day9.14

才看这道题也是无从下手,虽然写程序很长时间了,当时我走在路上边走边想这道题,隐隐约约好像很熟悉的感觉,应该使用两层循环,就想下自己平时不用程序自己是如何解决这个问题的(就当解数学题),我会拿张纸,写下一组数据,然后用第一个数字依次和第二个第三个数字相加,并画出相加的线条,如果答案等于 target 就停下来,否则用第二个数字依次...如此循环直到每个数字都循环一遍

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  for (var i = 0; i < nums.length; i++) {
    for (var j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j]
      }
    }
  }
}
```

### 解法 2 day9.15

这个解法是参照 LeetCode 官方给出的方法, 用的是空间换时间的做法 使用 Map 的高速特性
,我在做这个的时候先写了一遍 Java 版的,Java 中有个 HashMap 对象,hash 好像是一个链表结构,将数据存储在 HashMap 查找速度比数组要快很多

如果不看官方给出的解法的话我就会直接做下道题了,这样我的思路还是停留在了以前的那个阶段没有丝毫增长

对每道题进行迭代,优化是我以后要多做的事情,不着急去解决其他问题,反正后面肯定有很多难度更高的题,像以前那样做过之后不总结,不复盘的话肯定会碰壁的,要多想一下这道题还有其他解决方法没有(这个道理还可以用在哪? 这个道理还可以怎么用? 有没有其他选项?),有很大概率一道题的其他解法就是下一道题的解题思路

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
         HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        for(int i = 0 ;i<nums.length; i++){
               map.put(nums[i],i);
        }
        for(int i = 0; i<nums.length; i++){
            int x = target - nums[i];
            if ( map.containsKey(x) && map.get(x) != i){
                return new int[]{map.get(x), i};
            }
        }
         throw new IllegalArgumentException("No two sum solution");
    }
}

```

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
  const myMap = new Map()
  for (var i = 0; i < nums.length; i++) {
    myMap.set(nums[i], i)
  }
  for (var i = 0; i < nums.length; i++) {
    const x = target - nums[i]
    if (myMap.has(x) && myMap.get(x) !== i) {
      return [i, myMap.get(x)]
    }
  }
}
```
