class Solution {
    static int preorder(Node root,int l,int h){
        if(root==null){
            return 0;
        }
        int count = 0;
        if(root.data>=l && root.data<=h){
            count = 1;
        }
        int left = preorder(root.left,l,h);
        int right = preorder(root.right,l,h);
        return left+right+count;
    }
    int getCount(Node root, int l, int h) {
        // Your code here
       return preorder(root,l,h);
    }
}