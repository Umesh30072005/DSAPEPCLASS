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
Find Peak Element
========================================

class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0;
        int right = nums.length -1;

        while(left<right){
            int mid = left + (right - left)/2;
            if(nums[mid] < nums[mid + 1]){
                left = mid + 1;
            }
            else{
                right = mid;
            }
        }
        return left;
    }
}

========================================
Aggresive Cows
========================================

class Solution {
    public int aggressiveCows(int[] stalls, int k) {
        Arrays.sort(stalls);
        int n = stalls.length;
        int low = 1;
        int high = stalls[n-1] - stalls[0];
        int result = 0;
        
        while(low<=high){
            int mid = low + (high - low)/2;
            if(canplace(stalls,k,mid)){
                result = mid;
                low = mid+1;
            }else{
                high = mid-1;
            }
        }
        return result;
    }
    private boolean canplace(int [] stalls,int k,int dist){
        int cowplaced = 1;
        int lastpos = stalls[0];
        for(int i = 1;i<stalls.length;i++){
            if(stalls[i] - lastpos >= dist){
                cowplaced++;
                lastpos = stalls[i];
            }
        }
        return cowplaced >= k;
    }
}

========================================
Capacity Of Ship Package within D Days
========================================

class Solution {
    public int shipWithinDays(int[] weights, int days) {
        int n = weights.length;
        int low = 0;
        int high = 0;
        for(int w : weights){
            low = Math.max(low,w);
            high += w;
        } 
        while(low < high){
            int mid = low + (high - low)/2;
            if(canship(weights,days,mid)){
                high = mid;
            }else{
                low = mid + 1;
            }
        }
        return low;
    }
    private boolean canship(int [] weights,int days, int capacity){
        int daysneeded = 1;
        int currentload = 0;
        for(int w: weights){
            if(currentload + w > capacity ){
                daysneeded++;
                currentload = 0;
            }
            currentload += w;
        }
            return daysneeded <= days;
        
    }
}

========================================
Valid Anagram 
========================================

class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()){
            return false;
        }
        int[] arr = new int[26];
        for(int i = 0;i<s.length(); i++){
            arr[s.charAt(i) - 'a']++;
            arr[t.charAt(i) - 'a']--;
        }
        for(int check : arr){
            if(check != 0){
                return false;
            }
        }
        return true;
    }
}

========================================
Valid Palindrome
========================================
class Solution {
    public boolean isPalindrome(String s) {

        if (s == null || s.length() == 0) {
            return true;
        }

        int start = 0;
        int last = s.length() - 1;

        while (start <= last) {
            char currFirst = s.charAt(start);
            char currLast = s.charAt(last);

            if (!Character.isLetterOrDigit(currFirst)) {
                start++;
            }
            else if (!Character.isLetterOrDigit(currLast)) {
                last--;
            }
            else {
                if (Character.toLowerCase(currFirst) != Character.toLowerCase(currLast)) {
                    return false;
                }
                start++;
                last--;
            }
        }
        return true;
    }
}

========================================
Valid Palindrome ||
========================================

class Solution {
    public boolean validPalindrome(String s) {
        
        int start = 0;
        int last = s.length()-1;
        boolean skipped =false;
        while(start<last){
         if(s.charAt(start) == s.chatAt(last)){
            start++;
            last--;
         } else{
            if(skipped){
                return false;
            }
            return isPal(s,start +1,last) || isPal(s,start,last-1);
         }
        }
        return true;

    }
    private boolean isPAl(String s, int start,int last){
        while(start<last){
            if(s.charAt(start) != s.charAt(last)){
                return false;
            }
            start++;
            last--;
        }
        return true;
    }
}

========================================
Sunsequence String
========================================

class Solution {
    public boolean isSubsequence(String s, String t) {
        int sp = 0;
        int tp = 0;
        while(sp<s.length() && tp < t.length()){
            if(s.charAt(sp) == t.charAt(tp)){
                sp++;
            }
            tp++;
        }
        return sp == s.length();
    }
}


========================================
First unique character in String
========================================

class Solution {
    public int firstUniqChar(String s) {
        HashMap<Character, Integer> map = new HashMap<>();

        // Count frequency of each character
        for (char a : s.toCharArray()) {
            map.put(a, map.getOrDefault(a, 0) + 1);
        }

        // Find first character with frequency 1
        for (int i = 0; i < s.length(); i++) {
            if (map.get(s.charAt(i)) == 1) {
                return i;
            }
        }
        return -1;
    }
}

========================================
Add Two strigs
========================================

class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder res = new StringBuilder();
        int i = num1.length() - 1; 
        int j = num2.length() - 1; 
        int carry = 0;

        
        while (i >= 0 || j >= 0 || carry != 0) {
            
            int d1 = (i >= 0) ? num1.charAt(i) - '0' : 0;
            int d2 = (j >= 0) ? num2.charAt(j) - '0' : 0;

            int sum = d1 + d2 + carry;
            res.append(sum % 10); 
            carry = sum / 10;     

            i--;
            j--;
        }
        return res.reverse().toString();
    }
}

========================================
Sum Of Arrays Using Recurrsion
========================================

// User function Template for Java

class Solution {
    int arraySum(int arr[]) {
        // code here
        return sum(arr,0);
    }
    private int sum(int arr[], int index){
        if(index == arr.length){
            return 0;
        }
        return arr[index] + sum(arr,index + 1);
    }
}

========================================
Fibonacci number
========================================

class Solution {
    public int fib(int n) {
        if(n<=1) 
        {
            return n;
        }
        return fib(n-1) + fib(n-2);
    }
}

========================================
Climbing Stars
========================================

class Solution {
    public int climbStairs(int n) {
        if(n<=0){
            return 0;
        }
        if(n == 1){
            return 1;
        }
        if(n == 2){
            return 2;
        }
        int onestepbefore = 2;
        int twostepbefore = 1;
        int currentstep = 0;
        for(int i =2;i<n;i++){
            currentstep = onestepbefore + twostepbefore;
            twostepbefore = onestepbefore;
            onestepbefore = currentstep;
        }
        return currentstep;
    }
}

========================================
Factorial Prop
========================================

class Solution {
    int factorial(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        return n * factorial(n - 1);
    }
}

========================================
Power Of Number
========================================

class Solution {
    public int reverseExponentiation(int n) {
        long mod = 1000000007L;
        long r = 0;
        int temp = n;
        while (temp > 0) {
            r = (r * 10) + (temp % 10);
            temp /= 10;
        }
        long res = 1;
        long base = n % mod;
        
        while (r > 0) {
            if (r % 2 == 1) {
                res = (res * base) % mod;
            }
            base = (base * base) % mod;
            r /= 2;
        }
        
        return (int) res;
    }
}

========================================
Merge Sort
========================================

class Solution {

    void mergeSort(int arr[], int l, int r) {
        // code here
        if(l<r){
            int m = l + (r-l)/2;
            mergeSort(arr,l,m);
            mergeSort(arr,m+1,r);
            merge(arr,l,m,r);
        }
        
    }
    void merge(int arr[],int l , int m , int r){
        int n1 = m-l+1;
        int n2 = r-m;
        
        int L[] = new int[n1];
        int R[] = new int[n2];
        for(int i = 0;i<n1;++i){
            L[i] = arr[l+i];
            for(int j = 0;j<n2;++j){
                R[j] = arr[m+1+j];
            }
        }
        int i = 0,j=0;
        int k =l;
        while(i<n1 &&j<n2){
            if(L[i] <= R[j]){
                arr[k] = L[i];
                i++;
            }else{
                arr[k] = R[j];
                j++;
            }
            k++;
        }
        while(i<n1){
            arr[k] = L[i];
            i++;
            k++;
        }
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }
}

========================================
Quick Sort 
========================================

class Solution {
    public void quickSort(int[] arr, int low, int high) {

        if (low < high) {
            int pivotIndex = partition(arr, low, high);

            quickSort(arr, low, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, high); // ✅ fixed
        }
    }

    private int partition(int[] arr, int low, int high) {

        int pivot = arr[high];
        int i = low - 1;

        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        return i + 1;
    }
}

========================================
first element as pivot :
========================================

class QuickSortFirstPivot {

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int p = partition(arr, low, high);
            quickSort(arr, low, p - 1);
            quickSort(arr, p + 1, high);
        }
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[low];   // FIRST element as pivot
        int i = low + 1;
        int j = high;

        while (i <= j) {
            while (i <= high && arr[i] <= pivot) i++;
            while (arr[j] > pivot) j--;

            if (i < j) {
                swap(arr, i, j);
            }
        }
        swap(arr, low, j);  // place pivot correctly
        return j;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}
========================================
Middle element as pivot :
========================================

class QuickSortMiddlePivot {

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int p = partition(arr, low, high);
            quickSort(arr, low, p);
            quickSort(arr, p + 1, high);
        }
    }

    private static int partition(int[] arr, int low, int high) {
        int pivot = arr[(low + high) / 2]; // MIDDLE element
        int i = low;
        int j = high;

        while (i <= j) {
            while (arr[i] < pivot) i++;
            while (arr[j] > pivot) j--;

            if (i <= j) {
                swap(arr, i, j);
                i++;
                j--;
            }
        }
        return j;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
}


========================================
Transformed Array :
========================================

class Solution {
    public int[] constructTransformedArray(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        for(int i = 0; i < n; i ++){
            result[i] = nums[((i + nums[i]) % n + n) % n];
        }
        return result;
    }
}

========================================
Remmove duplicates in array from sorted array ||
========================================

class Solution {
    public int removeDuplicates(int[] nums) {
        int k = 2;

        for (int i = 2; i < nums.length; i++) {
            if (nums[i] != nums[k - 2]) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;        
    }
}

========================================
Minimun removal to balance array:
========================================

class Solution {
    public int minRemoval(int[] nums, int k) {
        Arrays.sort(nums);
        int i = 0;
        int maxLen = 0;

        for (int j = 0; j < nums.length; j++) {
            while ((long) nums[j] > (long) nums[i] * k) {
                i++;
            }
            maxLen = Math.max(maxLen, j - i + 1);
        }

        return nums.length - maxLen;
    }
}


========================================
Search a 2D Array:
========================================

class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        for(int [] num:matrix){
            if((num[0] <= target && num[num.length-1] >= target) && bs(num,target,0,num.length-1)){
                return true;
            }
        }
        return false;
    }
    public boolean bs(int[] num,int target, int s, int e){
        if(s>e){
            return false;
        }
        int mid = s +(e-s)/2;
        if(num[mid] == target){
            return true;
        }
        if(num[mid] < target){
            return bs(num,target,mid+1,e);
        }
        return bs(num,target,s,mid-1);
    }
}

========================================
Search a 2D Array:
========================================

class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = matrix.length;
        int col = matrix[0].length -1;
        int r =0;
        while(r<row && col >=0){
            if(target>matrix[r][col]){
                r++;
            }else{
                if(target<matrix[r][col]){
                    col--;
                }else{
                    return true;
                }
            }
        }
        return false;
    }
}

========================================
Max traversal of matrix bondaries
========================================

class Solution {
    public ArrayList<Integer> boundaryTraversal(int mat[][]) {
        // code here
        ArrayList<Integer>result = new ArrayList<>();
        
        int rows = mat.length;
        int cols = mat[0].length;
        
        if(rows == 1){
            for(int j = 0;j<cols;j++){
                result.add(mat[0][j]);
            }
            return result;
        }
        if(cols == 1){
            for(int i = 0;i<rows;i++){
                result.add(mat[i][0]);
            }
            return result;
        }
        for(int j = 0;j<cols;j++){
            result.add(mat[0][j]);
        }
        for(int i = 1;i<rows -1;i++){
            result.add(mat[i][cols -1]);
        }
        for(int j = cols -1; j>=0;j--){
            result.add(mat[rows-1][j]);
        }
        for(int i = rows -2;i>=1;i--){
            result.add(mat[i][0]);
        }
        return result;
    }
}

========================================
Spiral Matrix
========================================

import java.util.*;

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> result = new ArrayList<>();

        int top = 0;
        int bottom = matrix.length - 1;
        int left = 0;
        int right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {

            
            for (int j = left; j <= right; j++) {
                result.add(matrix[top][j]);
            }
            top++;

            
            for (int i = top; i <= bottom; i++) {
                result.add(matrix[i][right]);
            }
            right--;

            
            if (top <= bottom) {
                for (int j = right; j >= left; j--) {
                    result.add(matrix[bottom][j]);
                }
                bottom--;
            }

            
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    result.add(matrix[i][left]);
                }
                left++;
            }
        }

        return result;
    }
}

========================================
Snake Pattern in matrix
========================================

class Solution {
    static ArrayList<Integer> snakePattern(int matrix[][]) {

        ArrayList<Integer> result = new ArrayList<>();
        int n = matrix.length;

        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                for (int j = 0; j < n; j++) {
                    result.add(matrix[i][j]);
                }
            }
            else {
                for (int j = n - 1; j >= 0; j--) {
                    result.add(matrix[i][j]);
                }
            }
        }
        return result;
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
