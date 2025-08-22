class Pair{
    TreeNode node;
    int idx;
    Pair(TreeNode node,int idx){
        this.node = node;
        this.idx = idx;
    }
 }
class Solution {
    public int widthOfBinaryTree(TreeNode root) {
        ArrayDeque<Pair> dq = new ArrayDeque<>();
        dq.add(new Pair(root,0));
        int max = 0;
        while(!dq.isEmpty()){
            int size = dq.size();
            int start = dq.peekFirst().idx;
            int end = dq.peekLast().idx;
            max = Math.max(max,end-start+1);
            for(int i=1;i<=size;i++){
                Pair curr = dq.poll();
                int idx = curr.idx;
                if(curr.node.left!=null){
                    dq.addLast(new Pair(curr.node.left,2*idx+1));
                }
                if(curr.node.right!=null){
                    dq.addLast(new Pair(curr.node.right,2*idx+2));
                }
            }
        }
        return max;
    }
}
