给定一个数组，它的第 i 个元素是一支给定的股票在第 i 天的价格。

设计一个算法来计算你所能获取的最大利润。你最多可以完成 k 笔交易。

注意: 你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

示例 1:

输入: [2,4,1], k = 2
输出: 2
解释: 在第 1 天 (股票价格 = 2) 的时候买入，在第 2 天 (股票价格 = 4) 的时候卖出，这笔交易所能获得利润 = 4-2 = 2 。

示例 2:

输入: [3,2,6,5,0,3], k = 2
输出: 7
解释: 在第 2 天 (股票价格 = 2) 的时候买入，在第 3 天 (股票价格 = 6) 的时候卖出, 这笔交易所能获得利润 = 6-2 = 4 。
     随后，在第 5 天 (股票价格 = 0) 的时候买入，在第 6 天 (股票价格 = 3) 的时候卖出, 这笔交易所能获得利润 = 3-0 = 3 


int max(int a,int b){
    return (a>=b)? a:b ;
}
int maxProfit(int k, int* prices, int pricesSize){
        if((pricesSize<2)||(k==0))
    return 0;
    int maxProfit=0;
    if(k>(pricesSize/2)){
    for(int i=1;i<pricesSize;i++){
        if(prices[i]>prices[i-1])
        maxProfit+=prices[i]-prices[i-1];
    }
    return maxProfit;}
    int dp[pricesSize][k+1][2];
    memset(dp,0,sizeof(int)*(pricesSize)*2*(k+1));
    for(int i=0;i<pricesSize;i++){
        for(int j=1;j<=k;j++){
            if(i-1==-1){
                dp[0][k][0]=0;
                dp[0][k][1]=-prices[0];
                continue;
            }
            dp[i][j][0]=max(dp[i-1][j][0],dp[i-1][j][1]+prices[i]);
            dp[i][j][1]=max(dp[i-1][j][1],dp[i-1][j-1][0]-prices[i]);}}
    return dp[pricesSize-1][k][0];}
    
    用状态方程 dp[i][j][0]=max(dp[i-1][j][0],dp[i-1][j][1]+prices[i]);
            dp[i][j][1]=max(dp[i-1][j][1],dp[i-1][j-1][0]-prices[i])
     注意点：
     1、k正序倒序都可，正序我理解的是，完成交易的次数。当此时手里有股票时，那么就是之前没有股票时买入的或者之前买了没操作的。但是手里有股票前是没股票状态，那时候即已经完成了一次交易，因此要k-1
     2、初始化时为了避免下标出现-1，特殊考虑数组。dp[0][k][0]代表此时没有开始买股票因此赋值为0，dp[0][k][1]代表没开始时就已经拥有了股票，但这是不成立的，所以让负数代替它
     3、因为一买一卖为一次交易，那一个数组中顶多交易不超过pricesize/2，如果给的K超过了这个最大交易值，那就相当于无限次，就可以用题一的贪心算法。否则当K给很大时会超时
     
