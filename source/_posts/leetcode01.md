
---
title: leetcode01

date: 2017-10-20 09:49:24

categories: hexo             
tags: [nodejs, hexo, NexT]   
---

  __这是我首次尝试使用markdown来记录自己刷LeetCode的过程。__  
  本题简介：  
   
    Given an array of integers, return indices of the two numbers such that they add up to a specific target.
    You may assume that each input would have exactly one solution, and you may not use the same element twice.  
example:    

    Given nums = [2, 7, 11, 15], target = 9,
    Because nums[0] + nums[1] = 2 + 7 = 9,
    return [0, 1].
这题需要我们找出数组中等于target的二数之和，这里可以有几种方式，   
1、直接使用冒泡法对数组进行遍历查询相加，找出对应的数组的位置。  

	【js】
     var twoSum = function(nums, target) {
       for (var i=0;i<nums.length;i++){
          for (var j=i+1;j<nums.length;j++){
             if (nums[i]+nums[j]==target){
                return [i,j];
             }
          }
       }
    }
2、第一种方法的时间复杂度时O（n^2),所以我们继续改进  

	var twoSum = function(nums, target) {
    var ans = [];
    var map = [];
      for (var i = 0; i < nums.length; i++) {
         if (map[target - nums[i]] !== undefined) {
             ans[0] = parseInt(map[target - nums[i]]) ;
             ans[1] = i;
             return ans;
         } 
          map[nums[i]] = i;
       }
    }
这种办法是跟Java中的map方法，组成key和value一一对应，这样只要一次循环就能找出对应的value了