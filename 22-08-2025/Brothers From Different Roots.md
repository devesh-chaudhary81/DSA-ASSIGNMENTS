class Solution {
    public static int preorder(Node root1,Node root2,int x){
        if(root1==null){
            return 0;
        }
       
        int count = searchNode(root2,x-root1.data);
        int left = preorder(root1.left,root2,x);
        int right = preorder(root1.right,root2,x);
        return count+left+right;
    }
    
    public static int searchNode(Node root2,int target){
        Node curr = root2;
        while(curr!=null){
            if(curr.data==target){
                return 1;
            }
            else if(curr.data<target){
                curr = curr.right;
            }else{
                curr = curr.left;
            }
        }
        return 0;
    }
    public static int countPairs(Node root1, Node root2, int x) {
        // Code here
        return preorder(root1,root2,x);
        
    }
}