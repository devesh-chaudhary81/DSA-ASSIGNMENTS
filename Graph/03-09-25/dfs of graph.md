class Solution {
    // Function to return a list containing the DFS traversal of the graph.
    public ArrayList<Integer> dfs(ArrayList<ArrayList<Integer>> adj) {
        // Code here
        int v = adj.size();
        boolean vis[] = new boolean[v];
        ArrayList<Integer> ans = new ArrayList<>();
        for(int i = 0;i<adj.size();i++){
            if(!vis[i]){
                dfs(adj,i,vis,ans);
            }
        }
        
        return ans;
    }
    static void dfs(ArrayList<ArrayList<Integer>> adj,int node,boolean[] vis,ArrayList<Integer> ans){
       
        vis[node] = true;
        ans.add(node);
        
        for (int nei : adj.get(node)){
            if(!vis[nei]){
                 dfs(adj,nei,vis,ans);
            }
           
        }
    }
}