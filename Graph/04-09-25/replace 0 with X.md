class Solution {
    static void travel(char[][] mat,boolean[][] vis,int i,int j,int row,int col){
        vis[i][j] = true;
        int[] dr = {-1,0,1,0};
        int[] dc = {0,1,0,-1};
        for(int k=0;k<4;k++){
            int nr = dr[k] + i;
            int nc = dc[k] + j;
            if(nr>=0 && nr<row && nc>=0 && nc<col && !vis[nr][nc] && mat[nr][nc]=='O'){
                mat[nr][nc] = '1';
                vis[nr][nc] = true;
                travel(mat,vis,nr,nc,row,col);
            }
        }
    }
    static char[][] fill(char mat[][]) {
        // code here
        int row = mat.length;
        int col = mat[0].length;
        boolean[][] vis = new boolean[row][col];
        for(int i=0;i<mat.length;i++){
            for(int j=0;j<mat[i].length;j++){
                if((i==0 || i==row-1 || j==0 || j==col-1) && mat[i][j]=='O' && !vis[i][j]){
                    travel(mat,vis,i,j,row,col);
                }
            }
        }
        for(int i=0;i<mat.length;i++){
            for(int j=0;j<mat[i].length;j++){
                if((i==0 || i==row-1 || j==0 || j==col-1) && mat[i][j]!='X'){
                    mat[i][j] = 'O';
                }
                else if(mat[i][j]=='O'){
                    mat[i][j] = 'X';
                }else if(mat[i][j]=='1'){
                    mat[i][j] = 'O';
                }
            }
        }
        return mat;
    }
}