给你一个整数数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口内的 k 个数字。滑动窗口每次只向右移动一位。

返回 滑动窗口中的最大值 。
    
    public int[] maxSlidingWindow(int[] nums, int k) {
        if(nums.length==0 || k==0)return new int[0];
        Deque<Integer> dq = new LinkedList<>();
        int []res = new int[nums.length - k + 1];
        for(int i=0;i<k;i++){
            while(!dq.isEmpty()&&dq.peekLast()<nums[i]){
                dq.removeLast();
            }
            dq.addLast(nums[i]);
        }
        res[0] = dq.peekFirst();
        for(int i=k;i<nums.length;i++){
            if(dq.peekFirst()==nums[i-k])dq.removeFirst();
            while(!dq.isEmpty()&&dq.peekLast()<nums[i]){
                dq.removeLast();
            }
            dq.addLast(nums[i]);
            res[i-k+1]=dq.peekFirst();
        }
        return res;
    }
