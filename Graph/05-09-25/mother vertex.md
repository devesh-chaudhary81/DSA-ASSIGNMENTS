class Solution {
    // Function to find a Mother Vertex in the Graph.
    static void dfs(int node,ArrayList<ArrayList<Integer>> adj,boolean[] vis){
        vis[node] = true;
        for(int nei : adj.get(node)){
            if(!vis[nei]){
                dfs(nei,adj,vis);
                
            }
        }
    }
    public int findMotherVertex(int V, ArrayList<ArrayList<Integer>> adj) {
        // Code here
        boolean[] vis = new boolean[adj.size()];
        int last = -1;
        for(int i=0;i<adj.size();i++){
            if(!vis[i]){
            dfs(i,adj,vis);
            last = i;
            }
        }
        boolean[] check = new boolean[V];
        dfs(last,adj,check);
        for(boolean val : check){
            if(val==false){
                return -1;
            }
        }
        return last;
    }
}