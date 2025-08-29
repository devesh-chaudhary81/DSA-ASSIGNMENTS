class Pair{
    String word;
    int freq;
    Pair(String word,int freq){
        this.word = word;
        this.freq = freq;
    }
}
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        HashMap<String,Integer> map = new HashMap<>();
        for(int i=0;i<words.length;i++){
            map.put(words[i],map.getOrDefault(words[i],0)+1);
        }
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b) -> {
            if(a.freq == b.freq){
                return b.word.compareTo(a.word);
            }
            return a.freq - b.freq;
        });
            for(Map.Entry<String,Integer> ele:map.entrySet()){
                pq.add(new Pair(ele.getKey(),ele.getValue()));
                if(pq.size()>k){
                    pq.poll();
                }
            }
            List<String> list = new ArrayList<>();
            while(pq.size()>0){
                list.add(pq.poll().word);
            }
    Collections.reverse(list);
        return list;

    }
}