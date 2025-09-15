class Solution {
    static boolean dfs(int node,ArrayList<ArrayList<Integer>> adj,boolean[] vis,int[] path){
        vis[node] = true;
        path[node] = 1;
        for(int nei : adj.get(node)){
            if(!vis[nei]){
                if(dfs(nei,adj,vis,path)) return true;
            }else if(path[nei]==1){
                return true;
            }
        }
        path[node] = 0;
        return false;
    }
    public boolean canFinish(int numCourses, int[][] mat) {
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for(int i=0;i<numCourses;i++){
            adj.add(new ArrayList<>());
        }
        
            for(int[] e : mat){
                adj.get(e[1]).add(e[0]);
            }
        
        boolean[] vis = new boolean[adj.size()];
        int[] path = new int[adj.size()];
        for(int i=0;i<adj.size();i++){
            if(!vis[i]){
                if(dfs(i,adj,vis,path)){
                    return false;
                };
            }
        }
        return true;
    }
}