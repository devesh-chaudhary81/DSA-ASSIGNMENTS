class Pair{
    double dist;
    int x;
    int y;
    Pair(double dist,int x ,int y){
        this.dist = dist;
        this.x = x;
        this.y = y;
    }
}
class Solution {
    public int[][] kClosest(int[][] points, int k) {
        PriorityQueue<Pair> pq = new PriorityQueue<>((a,b) -> {
            return Double.compare(b.dist,a.dist);
        });
        for(int i=0;i<points.length;i++){
            int cord[] = points[i];
            int x = cord[0];
            int y = cord[1];

            double dist = Math.sqrt((x*x) + (y*y));
            pq.add(new Pair(dist,x,y));
            if(pq.size()>k){
                pq.poll();
            }
        }
        int[][] ans = new int[k][2];
        for(int i=0;i<k;i++){
            Pair temp = pq.poll();
            ans[i][0] = temp.x;
            ans[i][1] = temp.y;
        }
        return ans;
    }
}