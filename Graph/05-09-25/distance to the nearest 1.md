class Solution {
    // Function to find distance of nearest 1 in the grid for each cell.
    public int[][] nearest(int[][] grid) {
        // Code here
        int n = grid.length;
        int m = grid[0].length;
        int[][] ans = new int[n][m];
        Queue<int[]> q = new LinkedList<>();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==1){
                    q.add(new int[]{i,j});
                    ans[i][j] = 0;
                }else{
                    ans[i][j] = -1;
                }
            }
        }
        
        while(q.size()>0){
            int[] curr = q.poll();
            int r = curr[0];
            int c = curr[1];
            int[] dr = {-1,0,1,0};
            int[] dc = {0,1,0,-1};
                for(int j=0;j<4;j++){
                    int nr = r + dr[j];
                    int nc = c + dc[j];
                    if(nr>=0 && nr<grid.length && nc>=0 && nc<grid[0].length && grid[nr][nc]==0 && ans[nr][nc]==-1){
                        q.add(new int[]{nr,nc});
                        ans[nr][nc] = ans[r][c] + 1;
                    }
                }
        }
        return ans;
    }
}