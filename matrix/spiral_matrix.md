给你一个 m 行 n 列的矩阵 matrix ，请按照 顺时针螺旋顺序 ，返回矩阵中的所有元素。

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        if(matrix.length==0)return ans;
        int m = matrix.length-1, n = matrix[0].length-1;
        int l = 0, t = 0;
        while(true){
            for(int i=l;i<=n;i++){
                ans.add(matrix[t][i]);
            }
            if(++t>m)break;
            for(int i=t;i<=m;i++){
                ans.add(matrix[i][n]);
            }
            if(l>--n)break;
            for(int i=n;i>=l;i--){
                ans.add(matrix[m][i]);
            }
            if(--m<t)break;
            for(int i=m;i>=t;i--){
                ans.add(matrix[i][l]);
            }
            if(++l>n)break;
        }
        return ans;
    }
}
