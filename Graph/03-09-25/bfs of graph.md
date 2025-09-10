class Solution {
    // Function to return Breadth First Search Traversal of given graph.
    public ArrayList<Integer> bfs(ArrayList<ArrayList<Integer>> adj) {
        // code here
        ArrayList<Integer> ans = new ArrayList<>();
        Queue<Integer> q = new LinkedList<>();
        boolean[] vis = new boolean[adj.size()];
        q.add(0);
        vis[0] = true;
        while(!q.isEmpty()){
            int curr = q.poll();
            ans.add(curr);
            for(int i=0;i<adj.get(curr).size();i++){
                int val = adj.get(curr).get(i);
                if(!ans.contains(val) && vis[val]==false){
                    q.add(val);
                    vis[val] = true;
                }
            }
        }
        return ans;
    }
}