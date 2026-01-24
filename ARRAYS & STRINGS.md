========================================
DSA PRACTICE – LEETCODE (JAVA)
========================================

This repository contains Java solutions for LeetCode DSA problems.
Used for learning, revision, and interview preparation.

========================================
MERGE & SORT
========================================

class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while (i >= 0 && j >= 0) {
            nums1[k--] = (nums1[i] > nums2[j]) ? nums1[i--] : nums2[j--];
        }

        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
}

========================================
REMOVE ELEMENTS AND PRINT REMAINING
========================================

class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[k++] = nums[i];
            }
        }
        return k;
    }
}

========================================
PRINT 2ND HIGHEST NUMBER IN ARRAY
========================================

import java.util.Arrays;

class Solution {
    public int getSecondLargest(int[] arr) {
        Arrays.sort(arr);
        int n = arr.length;
        int max = arr[n - 1];

        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] < max) {
                return arr[i];
            }
        }
        return -1;
    }
}

========================================
MAX CONSECUTIVE ONES
========================================

class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int max = 0;
        int current = 0;

        for (int num : nums) {
            if (num == 1) {
                current++;
                max = Math.max(max, current);
            } else {
                current = 0;
            }
        }
        return max;
    }
}

========================================
MOVE ZEROES TO LAST
========================================

class Solution {
    public void moveZeroes(int[] nums) {
        int insertPos = 0;

        for (int num : nums) {
            if (num != 0) {
                nums[insertPos++] = num;
            }
        }

        while (insertPos < nums.length) {
            nums[insertPos++] = 0;
        }
    }
}

========================================
 Best Time to Buy and Sell Stock
========================================

class Solution {
    public int maxProfit(int[] prices) {
        int maxprofit = 0;
        int minprice = Integer.MAX_VALUE;
        for(int price : prices){
            minprice = Math.min(minprice,price);
            maxprofit = Math.max(maxprofit,price - minprice);
        }
        return maxprofit;
    }
    
}
========================================
 Min Max Pair in an Array
========================================

class Solution {
    public int minPairSum(int[] nums) {
        Arrays.sort(nums);

        int maxPairSum = 0;
        int i = 0, j = nums.length - 1;

        while (i < j) {
            maxPairSum = Math.max(maxPairSum, nums[i] + nums[j]);
            i++;
            j--;
        }

        return maxPairSum;
    }
}


========================================
NOTES
========================================
Language: Java
Platform: LeetCode
Purpose: Interview Preparation
Focus: Clean & readable code
========================================
