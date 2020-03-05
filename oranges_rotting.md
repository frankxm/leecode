在给定的网格中，每个单元格可以有以下三个值之一：

    值 0 代表空单元格；
    值 1 代表新鲜橘子；
    值 2 代表腐烂的橘子。

每分钟，任何与腐烂的橘子（在 4 个正方向上）相邻的新鲜橘子都会腐烂。

返回直到单元格中没有新鲜橘子为止所必须经过的最小分钟数。如果不可能，返回 -1。

 

示例 1：

输入：[[2,1,1],[1,1,0],[0,1,1]]
输出：4

示例 2：

输入：[[2,1,1],[0,1,1],[1,0,1]]
输出：-1
解释：左下角的橘子（第 2 行， 第 0 列）永远不会腐烂，因为腐烂只会发生在 4 个正向上。

示例 3：

输入：[[0,2]]
输出：0
解释：因为 0 分钟时已经没有新鲜橘子了，所以答案就是 0 。

 

提示：

    1 <= grid.length <= 10
    1 <= grid[0].length <= 10
    grid[i][j] 仅为 0、1 或 2


int orangesRotting(int** grid, int gridSize, int* gridColSize){
    int count=0;int time=0;
    int row=gridSize;int col=gridColSize[0];
    int k=0;int x[row*col];int y[row*col];int l=0;
    for(int i=0;i<row;i++){
        for(int j=0;j<col;j++){
            if(grid[i][j]==2){
            x[k]=i;
            y[k]=j;
            k++;
        }
           if(grid[i][j]!=1)
           count++;
    }}
    if(count==(row*col))
    return 0;
    int x_grid=0;int y_grid=0;count=0;
    while(1){
        time++;
    for(int i=0;i<k;i++){
        x_grid=x[i];
        y_grid=y[i];
        if((y_grid!=(col-1))&&(grid[x_grid][y_grid+1]==1)){
            grid[x_grid][y_grid+1]=2;
        }
        if((y_grid!=0)&&(grid[x_grid][y_grid-1]==1)){
            grid[x_grid][y_grid-1]=2;
        }
        if((x_grid!=0)&&(grid[x_grid-1][y_grid]==1)){
            grid[x_grid-1][y_grid]=2;
        }
        if((x_grid!=(row-1))&&(grid[x_grid+1][y_grid]==1)){
            grid[x_grid+1][y_grid]=2;
        }
    }
    l=0;
        for(int i=0;i<row;i++){
        for(int j=0;j<col;j++){
            if(grid[i][j]==2){
            x[l]=i;
            y[l]=j;
            l++;
        }
    }
}
if(k==l){
    time=-1;
    break;
}
k=l;
        for(int i=0;i<row;i++){
        for(int j=0;j<col;j++){
            if(grid[i][j]!=1){
                count++;
        }
    }
}
         if(count==row*col)
         break;
         count=0;}
         return time;}


