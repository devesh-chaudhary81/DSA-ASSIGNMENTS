class Solution {
    static void trev(TreeNode root, int k,Stack<Integer> stk){
        if(root==null){
            return;
        }
        trev(root.left,k,stk);
        if(stk.size()==k){
            return;
        }
        stk.push(root.val);
        
        trev(root.right,k,stk);
        

    }
    public int kthSmallest(TreeNode root, int k) {
        Stack<Integer> stk = new Stack<>();
        trev(root,k,stk);
        return stk.pop();
    }
}