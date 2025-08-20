class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        
        if(root==null){
            TreeNode temp = new TreeNode(val);
                root = temp;
                return root;
        }
        TreeNode curr = root;
        while(true){
            if(curr.right==null && curr.val<val){
                TreeNode temp = new TreeNode(val);
                curr.right = temp;
                break;
            }
            else if(curr.left==null && curr.val>val){
                TreeNode temp = new TreeNode(val);
                curr.left = temp;
                break;
            }
            else if(curr.val<val){
                curr = curr.right;
            }else{
                curr = curr.left;
            }
        }
        return root;
    }
}