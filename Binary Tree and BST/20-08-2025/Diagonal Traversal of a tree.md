class Tree {
    static void trev(Node root,TreeMap<Integer,ArrayList<Integer>> map,int left_dist){
        if(root==null){
            return;
        }
        if(map.containsKey(left_dist)){
            map.get(left_dist).add(root.data);
        }else{
            ArrayList<Integer> temp = new ArrayList<>();
            temp.add(root.data);
            map.put(left_dist,temp);
        }
        trev(root.left,map,left_dist+1);
        trev(root.right,map,left_dist);
    }
    public ArrayList<Integer> diagonal(Node root) {
        // add your code here.
        ArrayList<Integer> list = new ArrayList<>();
        TreeMap<Integer,ArrayList<Integer>> map = new TreeMap<>();
        trev(root,map,0);
        for(Map.Entry<Integer,ArrayList<Integer>> ele:map.entrySet()){
            int i = 0;
            while(i<ele.getValue().size()){
                list.add(ele.getValue().get(i));
                i++;
            }
        }
        return list;
    }
}