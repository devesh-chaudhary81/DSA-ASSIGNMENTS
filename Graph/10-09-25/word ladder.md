class Solution {
    public int ladderLength(String begin, String end, List<String> list) {
        if(!list.contains(end)){
            return 0;
        }
        HashSet<String> visited = new HashSet<>();
        int count = 0;
        while(!begin.equals(end) && visited.size()<list.size()){
            for(int i=0;i<list.size();i++){
                String temp = list.get(i);
                if(visited.contains(temp)){
                    continue;
                }
                int cnt = 0;
                for(int j=0;j<temp.length();j++){
                     if(temp.charAt(j) != begin.charAt(j)){
                        cnt++;
                        if(cnt>1) break;
                     }
                }
                if(cnt==1){
                    begin = temp;
                    count++;
                    if(begin.equals(end)){
                        return count;
                    }
                    visited.add(temp);
                    break;
                }
                }
            }
        
        return count;
    }
}