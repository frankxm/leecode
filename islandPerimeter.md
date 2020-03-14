给定一个包含 0 和 1 的二维网格地图，其中 1 表示陆地 0 表示水域。

网格中的格子水平和垂直方向相连（对角线方向不相连）。整个网格被水完全包围，但其中恰好有一个岛屿（或者说，一个或多个表示陆地的格子相连组成的岛屿）。

岛屿中没有“湖”（“湖” 指水域在岛屿内部且不和岛屿周围的水相连）。格子是边长为 1 的正方形。网格为长方形，且宽度和高度均不超过 100 。计算这个岛屿的周长。

 

示例 :

输入:
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

输出: 16



int islandPerimeter(int** grid, int gridSize, int* gridColSize){
      int n=gridSize;int m=gridColSize[0];    
      int count=0;int count_row=0;int count_col=0;int index=0;
        for(int i=0;i<n;i++){
                for(int j=0;j<m;j++){
                        if(grid[i][j]==1){
                                count++;
                                index=j;
                while(index!=m-1&&grid[i][index]==grid[i][index+1]){
                                        count_row++;
                                        count++;
                                        index++;}
                j=index+1;}}}
        for(int j=0;j<m;j++){
                for(int i=0;i<n;i++){
                        if(grid[i][j]==1){
                                index=i;
                while(index!=n-1&&grid[index][j]==grid[index+1][j]){
                        count_col++;
                        index++;}
                i=index+1;}}}
        int answer=count*4-(count_row+count_col)*2;
        return answer;
}
