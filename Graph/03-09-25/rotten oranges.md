class Solution {
   
    public int orangesRotting(int[][] grid) {
        int row = grid.length;
        int col = grid[0].length;
        int count = 0;
        int fresh = 0;
        Queue<int[]> q = new LinkedList<>();
        for(int i=0;i<row;i++){
            for(int j=0;j<col;j++){
                if(grid[i][j]==2){
                    q.add(new int[]{i,j});
                }else if(grid[i][j]==1){
                    fresh++;
                }
            }
        }
        if(fresh==0){
            return 0;
        }
        int[] dr = {0,1,0,-1};
        int[] dc = {1,0,-1,0};
        int min = 0;
        while(q.size()>0){
            int size = q.size();
            for(int i=0;i<size;i++){
            int[] curr = q.poll();
            int r = curr[0];
            int c = curr[1];
            for(int j=0;j<4;j++){
               int nr = r + dr[j];
               int nc = c + dc[j];
               if(nr>=0 && nr<row && nc>=0 && nc<col && grid[nr][nc]==1){
                q.add(new int[]{nr,nc});
                grid[nr][nc] = 2;
                fresh--;
               }
            }
            }
            min++;
            
        }
        if(fresh==0){
            return min-1;
        }else{
            return -1;
        }
        
    }
}