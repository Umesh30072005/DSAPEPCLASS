### **Merge \& Sort:**

class Solution {

    public void merge(int\[] nums1, int m, int\[] nums2, int n) {

        int i = m-1;

        int j = n-1;

        int k = m + n - 1;

        while(i >= 0 \&\& j >= 0){

            nums1\[k--] = (nums1\[i] > nums2\[j]) ? nums1\[i--] : nums2\[j--];



        }

        while (j >= 0) {

        nums1\[k--] = nums2\[j--];

    }

    }

}

### **Remove Elements And print remaining:**

class Solution {

    public int removeElement(int\[] nums, int val) {

        int k = 0; // index for non-val elements



        for (int i = 0; i < nums.length; i++) {

            if (nums\[i] != val) {

                nums\[k] = nums\[i];

                k++;

            }

        }

        return k; // number of elements left

    }

}



### **Print the 2nd highest number in array:**

**class Solution {**

    **public int getSecondLargest(int\[] arr) {**

        **// code here**

        **Arrays.sort(arr);**

       **int n = arr.length;**

        **int k = arr\[n-1];**

        

       **for (int i = n - 2; i >= 0; i--) {**

            **if (arr\[i] < k) {**

                **return arr\[i];**

            **}**

        **}** 

        **return -1;**

    **}**

**}**

