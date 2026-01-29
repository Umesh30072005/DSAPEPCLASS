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
 Twice Counter
========================================

import java.util.*;

class Solution {
    public int countWords(String[] list, int N) {
        HashMap<String, Integer> map = new HashMap<>();
        
        for (String word : list) {
            map.put(word, map.getOrDefault(word, 0) + 1);
        }
        
        int count = 0;
        
        for (int freq : map.values()) {
            if (freq == 2) {
                count++;
            }
        }

        return count;
    }
}

========================================
 Triplet Sum in Array (maps)
========================================

import java.util.*;

class Solution {
    public boolean hasTripletSum(int arr[], int target) {

        for (int i = 0; i < arr.length - 2; i++) {

            HashMap<Integer, Integer> map = new HashMap<>();

            for (int j = i + 1; j < arr.length; j++) {
                int needed = target - (arr[i] + arr[j]);

                if (map.containsKey(needed)) {
                    return true;
                }

                map.put(arr[j], j);
            }
        }
        return false;
    }
}

========================================
 Jump Game Array
========================================

class Solution {
    public boolean canJump(int[] nums) {
        int maxReach = 0;

        for (int i = 0; i < nums.length; i++) {
            if (i > maxReach) return false;

            maxReach = Math.max(maxReach, i + nums[i]);
        }

        return true;
    }
}

========================================
 Jump Game Array ||
========================================

class Solution {
    public int jump(int[] nums) {
        int jumps = 0;
        int end = 0;
        int maxreach = 0;
        for(int i = 0;i<nums.length-1;i++){
            maxreach = Math.max(maxreach, i+nums[i]);
            if(i == end){
                jumps++;
                end = maxreach;
            }
        }
        return jumps;
    }
}

========================================
H - Index 
========================================

import java.util.*;

class Solution {
    public int hIndex(int[] citations) {
        Arrays.sort(citations);

        int n = citations.length;

        for (int i = 0; i < n; i++) {
            int h = n - i;
            if (citations[i] >= h) {
                return h;
            }
        }
        return 0;
    }
}

========================================
Minimum Difference Between Highest and Lowest of K Scores
Solved
========================================

class Solution {
    public int minimumDifference(int[] nums, int k) {
        int n = nums.length;
        Arrays.sort(nums);
        int ans = nums[k - 1] - nums[0];
        for (int i = 0; i + k <= n; i++) {
            ans = Math.min(ans, nums[i + k - 1] - nums[i]);
        }
        return ans;
    }
}

========================================
Pair Sum in a Sorted and Rotated Array
========================================

import java.util.HashMap;

class Solution {
    static boolean pairInSortedRotated(int arr[], int target) {
    
        HashMap<Integer, Integer> map = new HashMap<>();
        
        for (int i = 0; i < arr.length; i++) {
            int complement = target - arr[i];
            if (map.containsKey(complement)) {
                return true;
            }
            map.put(arr[i], i);
        }
        
        return false;
    }
}

----------------(or)-----------------

import java.util.Arrays;

class Solution {
    static boolean pairInSortedRotated(int arr[], int target) {
        int n = arr.length;
        if (n < 2) return false;
        int i;
        for (i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                break; 
            }
        }

        
        int left = (i + 1) % n; 
        int right = i;           
        while (left != right) {
            int currentSum = arr[left] + arr[right];
            
            if (currentSum == target) {
                return true;
            }
            
            if (currentSum < target) {
                left = (left + 1) % n;
            } else {
                right = (n + right - 1) % n;
            }
        }
        
        return false;
    }
}

========================================
Bubble Sort 
========================================

class Solution {
    public void bubbleSort(int[] arr) {
        int n = arr.length;
        
        
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}

========================================
Selection Sort 
========================================

class Solution {
    void selectionSort(int[] arr) {
        // code here
        int n = arr.length;
        for(int i = 0;i<n-1;i++){
            int min = i;
            for(int j = i+1;j<n;j++){
                if(arr[j] < arr[min]){
                    min  = j;
                }
            }
            int temp = arr[min];
            arr[min] = arr[i];
            arr[i] = temp;
        }
    }
}

========================================
Insertion Sort 
========================================

class Solution {
    public void insertionSort(int[] arr) {
        int n = arr.length;
        
        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }
}

========================================
Max Sum SubArray
========================================

class Solution {
    public int maxSubarraySum(int[] arr, int k) {

        int n = arr.length;
        int max_sum = Integer.MIN_VALUE;

        for (int i = 0; i <= n - k; i++) {
            int current = 0;

            for (int j = 0; j < k; j++) {
                current += arr[i + j];
            }

            max_sum = Math.max(current, max_sum);
        }
        return max_sum;
    }
}

========================================
Search In Rotated Sorted Array
========================================

class Solution {
    public int search(int[] nums, int target) {
       
        int left = 0;
        int right = nums.length -1;

        while (left<=right){
            int mid  = left + (right - left)/2;
            if(nums[mid] == target){
                return mid;
            }
            if(nums[left] <= nums[mid]){
                if(nums[left] <= target && target < nums[mid]){
                    right = mid -1;
                }else{
                    left = mid + 1;
                }
            }
            else{
                if(nums[mid] < target && target <= nums[right]){
                    left = mid + 1;
                }else{
                    right = mid - 1;
                }
            }
        }
        return -1;
    }
}

========================================
Search In Rotated Sorted Array With Duplicates Handeled
========================================

class Solution {
    public boolean search(int[] nums, int target) {
        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == target) {
                return true;
            }
            
            if (nums[left] == nums[mid] && nums[mid] == nums[right]) {
                left++;
                right--;
                continue; 
            }
        

            if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            } else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        return false;
    }
}


========================================
NOTES
========================================
Language: Java
Platform: LeetCode
Purpose: Interview Preparation
Focus: Clean & readable code
O(notations) : (n^n, n!,2^n,n^3,n^2,nlogn,n,logn,1)
========================================
