class Solution {
    static void dfs(int r,int c,int[][] grid, boolean[][] vis, ArrayList<String> list,int row,int col){
        vis[r][c] = true;
        list.add(Integer.valueOf(r-row) + " " + Integer.valueOf(c-col));
        int[] dr = {-1,0,1,0};
        int[] dc = {0,1,0,-1};
        for(int i=0;i<4;i++){
            int nr = r + dr[i];
            int nc = c + dc[i];
            if(nr>=0 && nr<grid.length && nc>=0 && nc<grid[0].length && !vis[nr][nc] && grid[nr][nc]==1){
                dfs(nr,nc,grid,vis,list,row,col);
            }
        }
    }

    int countDistinctIslands(int[][] grid) {
        // Your Code here
        int n = grid.length;
        int m = grid[0].length;
        boolean[][] vis = new boolean[n][m];
        HashSet<ArrayList<String>> set = new HashSet<>();
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(!vis[i][j] && grid[i][j]==1){
                    ArrayList<String> list = new ArrayList<>();
                    dfs(i,j,grid,vis,list,i,j);
                    set.add(list);
                }
            }
        }
        return set.size();
    }
}