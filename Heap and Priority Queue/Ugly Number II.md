class Solution {
    public int nthUglyNumber(int n) {
        HashSet<Long> set = new HashSet<>();
        set.add((long)1);
        PriorityQueue<Long> pq = new PriorityQueue<>();
        pq.add((long)1);
        int[] factors = {2,3,5};
        long ugli = 1;
        for(int i=0;i<n;i++){
            ugli = pq.poll();
            for(int factor : factors){
               if(!set.contains(factor*ugli)){
                   pq.add(factor*ugli);
                   set.add(factor*ugli);
               }
            }
        }
        return (int) ugli;
    }
}