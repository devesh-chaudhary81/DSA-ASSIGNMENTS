class Solution {
    static void inorder(Node root,LinkedHashSet<Integer> set){
        if(root==null){
            return;
        }
        inorder(root.left,set);
        set.add(root.data);
        inorder(root.right,set);
    }
    // Function to find the nodes that are common in both BST.
    public static ArrayList<Integer> findCommon(Node r1, Node r2) {
        // code here
        LinkedHashSet<Integer> set1 = new LinkedHashSet<>();
        LinkedHashSet<Integer> set2 = new LinkedHashSet<>();
        inorder(r1,set1);
        inorder(r2,set2);
        ArrayList<Integer> ans = new ArrayList<>();
        for(Integer ele:set1){
            if(set2.contains(ele)){
                ans.add(ele);
            }
        }
        return ans;
        
    }
}