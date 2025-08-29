class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++){
            map.put(nums[i],map.getOrDefault(nums[i],0)+1);
        }
        PriorityQueue<int[]> pq = new PriorityQueue<>((a,b) ->{
            return a[1]-b[1];
        });
        for(Map.Entry<Integer,Integer> pair : map.entrySet()){
            int[] temp = new int[2];
            temp[0] = pair.getKey();
            temp[1] = pair.getValue();
            pq.add(temp);
            if(pq.size()>k){
                pq.poll();
            }
        }
        int[] ans = new int[k];
        for(int i=0;i<k;i++){
            ans[i] = pq.poll()[0];
        }
        return ans;
    }
}