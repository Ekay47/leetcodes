给你一个未排序的整数数组 nums ，请你找出其中没有出现的最小的正整数。

请你实现时间复杂度为 O(n) 并且只使用常数级别额外空间的解决方案。

class Solution {
    public int firstMissingPositive(int[] nums) {
        int len = nums.length;
        for(int i=0;i<len;i++){
            while(nums[i]>0 && nums[i]<=len && nums[nums[i]-1]!=nums[i]){
                swap(nums, nums[i]-1, i);
            }
        }
        for(int i=0;i<len;i++){
            if(nums[i]!=i+1)return i+1; 
        }
        return len+1;
    }

    private void swap(int[] nums, int idx1, int idx2){
        int temp = nums[idx1];
        nums[idx1] = nums[idx2];
        nums[idx2] = temp;
    }
}
