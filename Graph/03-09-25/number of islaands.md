class Solution {
    static void bfs(int i ,int j,int n,int m,char[][] grid,boolean[][] visited){
        Queue<int[]> q = new LinkedList<>();
        q.add(new int[]{i,j});
        visited[i][j] = true;
        int[] dr = {0,1,0,-1,-1,-1,1,1};
        int[] dc = {1,0,-1,0,1,-1,-1,1};
        while(q.size()>0){
            int[] curr = q.poll();
            int x = curr[0];
            int y = curr[1];
            for(int c=0;c<8;c++){
                int curr_row = x + dr[c];
                int curr_col = y + dc[c];
                if(curr_row>=0 && curr_row<n && curr_col>=0 && curr_col<m && !visited[curr_row][curr_col] && grid[curr_row][curr_col]=='L'){
                    q.add(new int[]{curr_row,curr_col});
                    visited[curr_row][curr_col] = true;
                }
            }
        }
    }
    public int countIslands(char[][] grid) {
        // Code here
        int n = grid.length;
        int m = grid[0].length;
        boolean[][] visited = new boolean[n][m];
        int count = 0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(!visited[i][j] && grid[i][j]!='W'){
                    count++;
                    bfs(i,j,n,m,grid,visited);
                }
            }
        }
        return count;
    }
}