class Solution {
    static void preorder(Node root,HashSet<Integer> set,ArrayList<Integer> list){
        if(root==null){
            return;
        }
        
        if(root.left==null && root.right==null){
            list.add(root.data);
            return;
        }
        
        set.add(root.data);
        preorder(root.left,set,list);
        preorder(root.right,set,list);
    }
    public boolean isDeadEnd(Node root) {
        // Code here.
        HashSet<Integer> set = new HashSet<>();
        set.add(0);
        ArrayList<Integer> list = new ArrayList<>();
        preorder(root,set,list);
        for(int i=0;i<list.size();i++){
            if(set.contains(list.get(i)-1) && set.contains(list.get(i)+1)){
                return true;
            }
        }
        return false;
        
    }