---
title: LeeCode日记
date: 2020-06-11
author: 周鸿宇诶
email: 1821998575@qq.com
tags:
 - LeeCode日记
categories: 
 - 算法
---


```java
package algorithm;
import java.util.HashMap;
/**
 * @Description: 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
 * 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。
 * 示例:
 * 给定 nums = [2, 7, 11, 15], target = 9
 * 因为 nums[0] + nums[1] = 2 + 7 = 9
 * 所以返回 [0, 1]
 * 来源：力扣（LeetCode）
 * 链接：https://leetcode-cn.com/problems/two-sum
 * @Author: 周鸿宇诶
 * @Date: 2020-06-10 16:36
 * @Version: 1.0
 **/
public class TwoSum {
    public static void main(String[] args) {
        int[] arr = solutionTwoSum(new int[]{2, 7, 11, 15},22);
        System.out.println(arr[0]+","+arr[1]);
    }
    private static int[] solutionTwoSum(int[] arr, int target) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for (int i = 0; i < arr.length; i++) {
            //算出余数
            int remainder = target - arr[i];
            if (map.containsKey(remainder)) {
                return new int[]{map.get(remainder),i};
            }else{
                map.put(arr[i], i);
            }
        }
        throw new IllegalArgumentException("该目标未能命中！");
    }
}
```

- 这一题我用的方式是哈希表和余数的思想。数组的值做为map的key，用key来命中余数。
- 每次遍历数组时，我都会算出当前下表元素值和目标值中间的差值，用差值去和map中的key进行匹配。
  如果不匹配代表未能命中，将当前元素值放进哈希表。若直接命中直接返回数组当前下标和命中map的
  value值。