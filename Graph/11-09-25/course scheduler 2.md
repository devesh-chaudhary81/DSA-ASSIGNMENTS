class Solution {
    public int[] findOrder(int numCourses, int[][] edges) {
        List<List<Integer>> adj = new ArrayList<>();
        for(int i=0;i<numCourses;i++){
            adj.add(new ArrayList<>());
        }
        for(int[] e:edges){
            adj.get(e[1]).add(e[0]);
        }
        int[] inDegree = new int[adj.size()];
        for(int i=0;i<adj.size();i++){
            for(int nei : adj.get(i)){
                inDegree[nei]++;
            }
        }
        Queue<Integer> q = new LinkedList<>();
        for(int i=0;i<inDegree.length;i++){
            if(inDegree[i]==0){
                q.add(i);
            }
        }
        int[] ans = new int[adj.size()];
        int idx = 0;
        while(q.size()>0){
            int node = q.poll();
            ans[idx++] = node;
            for(int nei : adj.get(node)){
                inDegree[nei]--;
                if(inDegree[nei]==0){
                    q.add(nei);
                }
            }
            
        }
        int count = 0;
        for(int e:ans){
            if(e==0) count++;
            if(count>1){
            return new int[]{};
        }
        }
        
        return ans;
    }
}