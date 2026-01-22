###  **Merge \& Sort:**  

class Solution {

&nbsp;   public void merge(int\[] nums1, int m, int\[] nums2, int n) {

&nbsp;       int i = m-1;

&nbsp;       int j = n-1;

&nbsp;       int k = m + n - 1;

&nbsp;       while(i >= 0 \&\& j >= 0){

&nbsp;           nums1\[k--] = (nums1\[i] > nums2\[j]) ? nums1\[i--] : nums2\[j--];



&nbsp;       }

&nbsp;       while (j >= 0) {

&nbsp;       nums1\[k--] = nums2\[j--];

&nbsp;   }

&nbsp;   }

}

### **Remove Elements And print remaining:**

class Solution {

&nbsp;   public int removeElement(int\[] nums, int val) {

&nbsp;       int k = 0; // index for non-val elements



&nbsp;       for (int i = 0; i < nums.length; i++) {

&nbsp;           if (nums\[i] != val) {

&nbsp;               nums\[k] = nums\[i];

&nbsp;               k++;

&nbsp;           }

&nbsp;       }

&nbsp;       return k; // number of elements left

&nbsp;   }

}





