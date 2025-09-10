class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        // Code here
        int old = image[sr][sc];
        if(old==color){
            return image;
        }
        dfs(image,sr,sc,image.length,image[0].length,color,old);
        return image;
    }
    static void dfs(int[][] image,int sr,int sc,int row,int col,int color,int old){
        if(sr<0 || sr >=row || sc<0 || sc>=col || image[sr][sc]!=old){
            return ;
        }
        
        image[sr][sc] = color;
        
        dfs(image,sr-1,sc,row,col,color,old);
        dfs(image,sr+1,sc,row,col,color,old);
        dfs(image,sr,sc-1,row,col,color,old);
        dfs(image,sr,sc+1,row,col,color,old);
    }
}