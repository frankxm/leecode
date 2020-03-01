给定一个数组，它的第 i 个元素是一支给定的股票在第 i 天的价格。

设计一个算法来计算你所能获取的最大利润。你最多可以完成 两笔 交易。

注意: 你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。

示例 1:

输入: [3,3,5,0,0,3,1,4]
输出: 6
解释: 在第 4 天（股票价格 = 0）的时候买入，在第 6 天（股票价格 = 3）的时候卖出，这笔交易所能获得利润 = 3-0 = 3 。
     随后，在第 7 天（股票价格 = 1）的时候买入，在第 8 天 （股票价格 = 4）的时候卖出，这笔交易所能获得利润 = 4-1 = 3 。

示例 2:

输入: [1,2,3,4,5]
输出: 4
解释: 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得利润 = 5-1 = 4 。   
     注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。   
     因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。

示例 3:

输入: [7,6,4,3,1] 
输出: 0 
解释: 在这个情况下, 没有交易完成, 所以最大利润为 0。



int maxProfit(int* prices, int pricesSize){
    if(pricesSize<=1)
    return 0;
    int min=prices[0];int max=prices[pricesSize-1];int maxProfit=0;
    int max_first=0;int max_second=0;int profit_first[pricesSize];int profit_second[pricesSize];
    for(int i=0;i<pricesSize;i++){
        if(prices[i]-min>max_first)
        max_first=prices[i]-min;
        if(prices[i]<min)
        min=prices[i];
        profit_first[i]=max_first;
}
    for(int j=pricesSize-1;j>=0;j--){
        if(max-prices[j]>max_second)
        max_second=max-prices[j];
        if(prices[j]>max)
        max=prices[j];
        profit_second[j]=max_second;
    }
    for(int i=0;i<pricesSize;i++){
        if(profit_first[i]+profit_second[i]>maxProfit)
        maxProfit=profit_first[i]+profit_second[i];
    }
    return maxProfit;}
    
    
    两次遍历，一次从头一次从尾，分别记录两次的最大值最后相加。
    从头遍历好理解，第一次买卖时我假设第一天买，那每到第i天时此时最大利润要不就是前面累计的最大利润，要不就是当天减去之前最小值所得的最大利润。这是一次遍历的结果，将其保存在数组中，方便求和时使用。
    中途遇到更小的可以更新买入点
    从尾遍历可以理解为：我第二次买卖时我假设最后一天卖出，那就往前找买入点，第二次遍历记录的每天获得的最大利润意思就是在尽可能很后卖出的情况下我来买入保证利润最大
    注意两次买卖最大利润并不是一次最大加上另一次最大，两次遍历意义不同，第一次是往后，在往后的情况下尽量保证最大。第二次是往前，在往前的情况下尽量保证最大。因为两次记录下来的值都是当天往前和当天往后所获得的最大
    
    
   参考借鉴的动态规划
   int max(int a,int b){
    return a>b? a: b ;
}
int maxProfit(int* prices, int pricesSize){
    if(pricesSize<2)
    return 0;
    int dp[pricesSize][3][2];
    memset(dp,0,sizeof(int)*(pricesSize)*3*2);
    dp[0][1][0]=0;dp[0][1][1]=-prices[0];dp[0][2][0]=0;dp[0][2][1]=-prices[0];
    for(int i=1;i<pricesSize;i++){
        for(int k=1;k<=2;k++){
            dp[i][k][0]=max(dp[i-1][k][0],dp[i-1][k][1]+prices[i]);
            dp[i][k][1]=max(dp[i-1][k][1],dp[i-1][k-1][0]-prices[i]);
        }
    }
    return dp[pricesSize-1][2][0];}
    
    
    
    
