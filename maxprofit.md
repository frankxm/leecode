给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。

注意你不能在买入股票前卖出股票。

示例 1:

输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。

示例 2:

输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。


常规解法
 while循环

int maxProfit(int* prices, int pricesSize){
    if(pricesSize<=1)
    return 0;
    int buy=0;int sell=0;int profit=0;int maxProfit=0;int tick=0;
    while(buy<(pricesSize-1)){
        tick=buy;
    while((buy<pricesSize-1)&&sell<pricesSize){
        if(prices[buy]>=prices[sell])
            sell++;
        else{
            if((sell+1<pricesSize)&&(prices[sell]<prices[sell+1]))
                sell++;
            else {
                profit=prices[sell]-prices[buy];
                if(profit>maxProfit)
                maxProfit=profit;
                sell++;
                }}
    }
    buy=tick+1;sell=buy+1;}
    return maxProfit;
}

for 循环

int maxProfit(int* prices, int pricesSize){
            int maxprofit = 0;
        for (int i = 0; i < pricesSize-1; i++) {
            for (int j = i + 1; j < pricesSize; j++) {
                int profit = prices[j] - prices[i];
                if (profit > maxprofit)
                    maxprofit = profit;
            }
        }
        return maxprofit;
    }

动态规划一

int maxProfit(int* prices, int pricesSize){
    if(pricesSize<=1)
    return 0;
    int min=prices[0];int maxProfit=0;int max=0;
    for(int i=1;i<pricesSize;i++){
        if(prices[i]-min>maxProfit)
        maxProfit=prices[i]-min;
        if(prices[i]<min)
        min=prices[i];
    }
return maxProfit;
}

用动态规划核心思想就是：如果到了第n天，那此时最大利润就是max(prices[n]-min,max)，要不就是前n-1天的最大值，要不就是当天的值减去前n-1天的最小值
同时假设一开始值最小，在遍历过程逐步替换。如果前n-1天出现了最大利润，那么就算之后最小值再怎么表小，当前值再怎么大，差值也大不过最大利润

动态规划二

int maxProfit(int* prices, int pricesSize){
    int maxProfit=0;int temp=0;
    for(int i=1;i<pricesSize;i++){
        temp+=prices[i]-prices[i-1];
        if(temp<0)
        temp=0;
        if(temp>maxProfit)
        maxProfit=temp;
    }
return maxProfit;
}

法二不同于法一在于，法一每次遍历需要更新最小值，而一开始就定义最小值为第一个数。如果输入的数组是个空数组，那么初始化时就会溢出，所以为了避免多加空数组的判断，不定义最小值，直接考虑每次的差值。如果是空数组的话自然无法进行循环就直接返回0了。每次遍历让上一次差值加这一次差值，如果总和temp小于0说明到此时没钱赚并且亏了，那么就不符合获得利润,temp归0。如果此时temp大于0，说明从开始至现在都在赚钱，利润逐渐增加。每一次获得利润时再更新最大利润。
说白了就是记录每次最大可能的利润最终再比较
