给你一个整数数组 nums，返回 数组 answer ，其中 answer[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积 。

题目数据 保证 数组 nums之中任意元素的全部前缀元素和后缀的乘积都在  32 位 整数范围内。

请 不要使用除法，且在 O(n) 时间复杂度内完成此题。

class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] ldp = new int[n];
        int[] rdp = new int[n];

        ldp[0] = 1;
        rdp[n-1] = 1;

        int[] res = new int[n];

        for(int i=1;i<n;i++){
            ldp[i] = ldp[i-1] * nums[i-1];
        }
        for(int j=n-2;j>=0;j--){
            rdp[j] = rdp[j+1] * nums[j+1];
        }
        for(int i=0;i<n;i++){
            res[i] = ldp[i] * rdp[i]; 
        }
        return res;
    }
}
