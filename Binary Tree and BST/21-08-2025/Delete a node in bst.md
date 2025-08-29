class Solution {
    public static TreeNode delete(TreeNode root,int key){
        if(root==null){
            return null;
        }
        if(root.val>key){
            root.left = delete(root.left,key);
        }
        else if(root.val<key){
            root.right = delete(root.right,key);
        }else{
            if(root.left==null && root.right==null){
                return null;
            }
            else if(root.left==null){
                return root.right;
            }
            else if(root.right==null){
                return root.left;
            }else{
                TreeNode node = findSuccessor(root.right);
                root.val = node.val;
                root.right = delete(root.right,node.val);
            }
        }
        return root;
    }
    public static TreeNode findSuccessor(TreeNode root){
               while(root.left!=null){
                root = root.left;
               }
               return root;
    }
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root==null){
            return null;
        }
        return delete(root,key);
    }
}