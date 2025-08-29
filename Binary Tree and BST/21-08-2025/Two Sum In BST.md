class Solution {
    static void trev(TreeNode root,HashSet<Integer> list){
           if(root==null){
            return;
           }
           list.add(root.val);
           trev(root.left,list);
           trev(root.right,list);
    }
    public boolean findTarget(TreeNode root, int k) {
        HashSet<Integer> list = new HashSet<>();
        trev(root,list);
        for(Integer ele:list){
            if(list.contains(k-ele) && k-ele != ele){
                return true;
            }
        }
        return false;
    }
}