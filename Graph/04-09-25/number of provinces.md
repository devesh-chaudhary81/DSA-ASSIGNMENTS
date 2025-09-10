class Solution {
     static void dfs(boolean[] vis,List<ArrayList<Integer>> adj2,int node){
        vis[node] = true;
        for(int nei:adj2.get(node)){
            if(!vis[nei]){
                dfs(vis,adj2,nei);
            }
        }
    }
    static int numProvinces(ArrayList<ArrayList<Integer>> adj, int V) {
        // code here
        List<ArrayList<Integer>> adj2 = new ArrayList<>();
        for(int i =0;i<adj.size();i++){
            adj2.add(new ArrayList<>());
        }
        boolean[] vis = new boolean[adj2.size()];
        for(int i=0;i<adj.size();i++){
            for(int j=0;j<adj.get(i).size();j++){
                if(i!=j && adj.get(i).get(j)==1){
                    adj2.get(i).add(j);
                }
            }
        }
        int count = 0;
        for(int i=0;i<adj2.size();i++){
            if(!vis[i]){
                dfs(vis,adj2,i);
                count++;
            }
        }
        return count;
    }
};