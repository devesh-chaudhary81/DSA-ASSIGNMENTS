class Solution {

    int shortestPath(int[][] grid, int[] source, int[] destination) {

        // Your code here
        int n = grid.length;
        int m = grid[0].length;
        
        // if source or destination is blocked
        if (grid[source[0]][source[1]] == 0 || grid[destination[0]][destination[1]] == 0) {
            return -1;
        }

        boolean[][] vis = new boolean[n][m];
        Queue<int[]> q = new LinkedList<>();
        
        // {row, col, distance}
        q.add(new int[]{source[0], source[1], 0});
        vis[source[0]][source[1]] = true;

        int[] dr = {-1, 0, 1, 0};
        int[] dc = {0, 1, 0, -1};

        while (!q.isEmpty()) {
            int[] cur = q.poll();
            int r = cur[0], c = cur[1], dist = cur[2];


            if (r == destination[0] && c == destination[1]) {
                return dist;
            }

            for (int k = 0; k < 4; k++) {
                int nr = r + dr[k];
                int nc = c + dc[k];
                if (nr >= 0 && nc >= 0 && nr < n && nc < m 
                    && grid[nr][nc] == 1 && !vis[nr][nc]) {
                    vis[nr][nc] = true;
                    q.add(new int[]{nr, nc, dist + 1});
                }
            }
        }

        return -1;
    }
}