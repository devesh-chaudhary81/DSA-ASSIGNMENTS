class Solution {
    static void trev(Node root,Stack<Integer> stk){
        if(root==null){
            return;
        }
        trev(root.left,stk);
        stk.push(root.data);
        trev(root.right,stk);
    }
    // return the Kth largest element in the given BST rooted at 'root'
    public int kthLargest(Node root, int k) {
        // Your code here
        Stack<Integer> stk = new Stack<>();
        trev(root,stk);
        int cnt = 1;
        while(cnt<k){
            stk.pop();
            cnt++;
        }
        return stk.pop();
    }
}