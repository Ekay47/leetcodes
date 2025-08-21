给定一个 m x n 的矩阵，如果一个元素为 0 ，则将其所在行和列的所有元素都设为 0 。请使用 原地 算法。

用第一行和第一列存储信息，同时找俩flag记录第一列和第一行是否需要置为0

class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length, n = matrix[0].length;
        boolean mflag = false, nflag = false;
        for(int i=0;i<m;i++){
            if(matrix[i][0]==0){
                mflag = true;
                break;
            }
        }
        for(int j=0;j<n;j++){
            if(matrix[0][j]==0){
                nflag = true;
                break;
            }
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                if(matrix[i][j]==0)matrix[i][0] = matrix[0][j] = 0;
            }
        }
        for(int j=1;j<n;j++){
            if(matrix[0][j]==0){
                for(int i=1;i<m;i++){
                    matrix[i][j] = 0;
                }
            }
        }
        for(int i=1;i<m;i++){
            if(matrix[i][0]==0){
                for(int j=1;j<n;j++){
                    matrix[i][j] = 0;
                }
            }
        }
        if(mflag){for(int i=0;i<m;i++)matrix[i][0]=0;}
        if(nflag)Arrays.fill(matrix[0],0);
    }
}
