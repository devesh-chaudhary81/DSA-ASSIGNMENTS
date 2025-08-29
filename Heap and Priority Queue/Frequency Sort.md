class Pair{
    char ch ;
    int freq;
    Pair(char ch, int freq){
        this.ch = ch;
        this.freq = freq;
    }
}
class Solution {
    public String frequencySort(String s) {
        HashMap<Character,Integer> map = new HashMap<>();
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b)->{
            return b.freq-a.freq;
        });
        for(int i=0;i<s.length();i++){
            char c = s.charAt(i);
            map.put(c,map.getOrDefault(c,0)+1);
        }
        for(Map.Entry<Character,Integer> pair : map.entrySet()){
            pq.add(new Pair(pair.getKey(),pair.getValue()));
        }
        StringBuilder ans = new StringBuilder();
        while(pq.size()>0){
            Pair p = pq.poll();
            char c = p.ch;
            int fre = p.freq;
            for(int i=0;i<fre;i++){
                ans.append(c);
            }
            
        }
        return ans.toString();

    }
}