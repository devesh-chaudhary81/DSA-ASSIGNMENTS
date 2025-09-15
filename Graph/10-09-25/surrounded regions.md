class Solution {
    static void dfs(char[][] board,boolean[][] vis,int i,int j,int row,int col){
        vis[i][j] = true;
        int[] dr = {-1,0,1,0};
        int[] dc = {0,1,0,-1};
        for(int k=0;k<4;k++){
            int nr = dr[k] + i;
            int nc = dc[k] + j;
            if(nr>=0 && nr<row && nc>=0 && nc<col && !vis[nr][nc] && board[nr][nc]=='O'){
                board[nr][nc] = '1';
                vis[nr][nc] = true;
                dfs(board,vis,nr,nc,row,col);
            }
        }
    }
    public void solve(char[][] board) {
        int row = board.length;
        int col = board[0].length;
        boolean[][] vis = new boolean[row][col];
        for(int i =0;i<row;i++){
            for(int j=0;j<col;j++){
                if((i==0 || i==row-1 || j==0 || j==col-1) && !vis[i][j] && board[i][j]=='O'){
                    dfs(board,vis,i,j,row,col);
                }
            }
        }
        for(int i =0;i<row;i++){
            for(int j=0;j<col;j++){
                if((i==0 || i==row-1 || j==0 || j==col-1) && board[i][j]!='X'){
                    board[i][j] = 'O';
                }
                else if(board[i][j]=='1'){
                    board[i][j] = 'O';
                }
                else if(board[i][j]=='O'){
                    board[i][j] = 'X';
                }
            }
        }
        
    }
}