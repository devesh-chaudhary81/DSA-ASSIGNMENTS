class Solution {
    public int minStep(int n) {
        // code here
        int count = 0;
        while(n>1){
            if(n%3!=0){
                n--;
            }else{
                n = n/3;
            }
            count++;
        }
        return count;
    }
}