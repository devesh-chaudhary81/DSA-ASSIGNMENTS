class Solution {
    static void preorder(Node root,Node root2){
        if(root==null){
            return;
        }
        insertNode(root,root2);
        preorder(root.left,root2);
        preorder(root.right,root2);
    }
    static void insertNode(Node node,Node root2){
        Node curr = root2;
        while(curr.data!=node.data){
            if(node.data<curr.data){
                if(curr.left==null){
                    Node newNode = new Node(node.data);
                    curr.left = newNode;
                    return;
                }
                curr = curr.left;
            }
            else{
                if(curr.right==null){
                    Node newNode = new Node(node.data);
                    curr.right = newNode;
                    return;
                }
                curr = curr.right;
            }
        }
        return ;
    }
    Node binaryTreeToBST(Node root) {
        
        Node root2 = new Node(root.data);
        preorder(root,root2);
        return root2;
        
    }
}