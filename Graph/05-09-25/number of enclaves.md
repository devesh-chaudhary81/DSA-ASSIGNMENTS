class Solution {

    int numberOfEnclaves(int[][] grid) {

        // Your code here
        int n = grid.length;
        int m = grid[0].length;
        boolean[][] vis = new boolean[n][m];
        Queue<int[]> q = new LinkedList<>();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if((i==0 || i==n-1 || j==0 || j==m-1) && grid[i][j]==1){
                    
                        q.add(new int[]{i,j});
                        vis[i][j]=true;
                    
                }
            }
        }
        while(q.size()>0){
            int[] curr = q.poll();
            int r = curr[0];
            int c = curr[1];
            int[] dr = {-1,0,1,0};
            int[] dc = {0,1,0,-1};
            for(int i=0;i<4;i++){
                int nr = r + dr[i];
                int nc = c + dc[i];
                if(nr>=0 && nr<n && nc>=0 && nc<m && !vis[nr][nc] && grid[nr][nc]==1){
                    q.add(new int[]{nr,nc});
                    vis[nr][nc] = true;
                }
            }
        }
        int count = 0;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==1 && !vis[i][j]){
                    
                       count++;
                    
                }
            }
        }
        return count;
    }
}