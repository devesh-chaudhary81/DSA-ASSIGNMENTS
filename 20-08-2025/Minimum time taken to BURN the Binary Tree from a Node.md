class Solution {
    static void mark_parent(TreeNode root,HashMap<TreeNode,TreeNode> parent){
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            TreeNode node = q.poll();
            if(node.left!=null){
                parent.put(node.left,node);
                q.add(node.left);
            }
            if(node.right!=null){
                parent.put(node.right,node);
                q.add(node.right);
            }
        }
    }

    static TreeNode findNode(TreeNode root,int start){
        if(root==null){
            return null;
        }
        if(root.val==start){
            return root;
        }
       TreeNode left = findNode(root.left,start);
       if(left!=null){
        return left;
       } 
       return findNode(root.right,start);
        
    }
    public int amountOfTime(TreeNode root, int start) {
        HashMap<TreeNode,TreeNode> parent = new HashMap<>();
        mark_parent(root,parent);
        TreeNode target = findNode(root,start);
        HashSet<TreeNode> visited = new HashSet<>();
        Queue<TreeNode> q = new LinkedList<>();
        q.add(target);
        visited.add(target);
        int count = 0;
        while(!q.isEmpty()){
             count++;
             int size = q.size();
             for(int i=1;i<=size;i++){
                TreeNode curr = q.poll();
                if(parent.containsKey(curr) && !visited.contains(parent.get(curr))){
                    q.add(parent.get(curr));
                    visited.add(parent.get(curr));
                }
                if(curr.left!=null && !visited.contains(curr.left)){
                    q.add(curr.left);
                    visited.add(curr.left);
                }
                if(curr.right!=null && !visited.contains(curr.right)){
                    q.add(curr.right);
                    visited.add(curr.right);
                }
             }
        }
        return count-1;
    }
}