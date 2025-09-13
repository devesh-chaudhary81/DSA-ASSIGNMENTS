class Solution {
    // Function to find whether a path exists from the source to destination.
    public boolean is_Possible(int[][] grid) {
        // Code here
        int n = grid.length;
        int m = grid[0].length;
        int sr = 0;
        int sc = 0;
        int tr = 0;
        int tc = 0;
        boolean flag1 = false;
        boolean flag2 = false;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(grid[i][j]==1){
                    sr = i;
                    sc = j;
                    flag1 = true;
                }else if(grid[i][j]==2){
                    tr = i;
                    tc = j;
                    flag2 = true;
                }
            }
            if(flag1&&flag2){
                break;
            }
        }
        boolean[][] vis = new boolean[n][m];
        vis[sr][sc] = true;
        Queue<int[]> q = new LinkedList<>();
        q.add(new int[]{sr,sc});
        while(q.size()>0){
            int[] curr = q.poll();
            int r = curr[0];
            int c = curr[1];
            int[] dr = {-1,0,1,0};
            int[] dc = {0,1,0,-1};
            for(int i=0;i<4;i++){
                int nr = dr[i] +r;
                int nc = dc[i] +c;
                if(nr>=0 && nr<n && nc>=0 && nc<m && !vis[nr][nc]){
                    if(grid[nr][nc]==2){
                        return true;
                    }else if(grid[nr][nc]==3){
                        q.add(new int[]{nr,nc});
                    }
                }
            }
        }
        return false;
    }
}