外观数列 是一个整数序列，从数字 1 开始，序列中的每一项都是对前一项的描述。前五项如下：

1.     1
2.     11
3.     21
4.     1211
5.     111221

1 被读作  "one 1"  ("一个一") , 即 11。
11 被读作 "two 1s" ("两个一"）, 即 21。
21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211。

给定一个正整数 n（1 ≤ n ≤ 30），输出外观数列的第 n 项。

注意：整数序列中的每一项将表示为一个字符串。

 

示例 1:

输入: 1
输出: "1"
解释：这是一个基本样例。

示例 2:

输入: 4
输出: "1211"
解释：当 n = 3 时，序列是 "21"，其中我们有 "2" 和 "1" 两组，"2" 可以读作 "12"，也就是出现频次 = 1 而 值 = 2；类似 "1" 可以读作 "11"。所以答案是 "12" 和 "11" 组合在一起，也就是 "1211"。




char * countAndSay(int n){
/*动态分配内存，定义两个数组，一个用于分析即当前数组，一个用于存储
    char *present=(char*)malloc(sizeof(char)*20000);
    char *nums=(char*)malloc(sizeof(char)*20000);char tick;
    */
    int count=0;int index=0;int len=0;int i=0;
    if(n==1){
        return "1";
    }
    else if(n>1){
        nums=countAndSay(n-1);
         len=strlen(nums);
         i=0;
         count=1;
        while(i<len){
            /*如果标志值与当前值相同，则计数变量count增加
            if(tick==nums[i]){
                count++;
            }
            */
            /*当出现不同时就立刻将前面的count 和 tick 存储
            else if(nums[i]!=tick){
            present[index++]=(char)count+'\0';
            present[index++]=tick;
            */
            /*存储完后立刻将count归为1，将当前值变为tick
            count=1;
            tick=nums[i];}
            */
            i++;
            }
            /*记录最后一项的值，不能漏掉'\0'
            present[index++]=(char)count+'\0';
            present[index++]=tick;
            present[index]='\0';}
            */
            return  present;}



做题感悟：
1、此题首先需要理解题意，就是将某一数字的个数加上本身一同打印出来，需要用递归的思想，因为每次需要求某一数组时就需要知道上一数组对其分析。如果需要求得第n项那么就需要往前分析最终起点项为1
2、若要打印出所需项，就需要用一个数组存储答案，同时需要对上一个数组分析。通过参考部分网友的做法，我学会了动态规划内存的方法来定义数组。
3、核心部分为“统计”，每当出现一样的数字时，用于计数的变量count就需要增加，当出现不同于tick的数字时，就需要直接将tick  和  count 存储
4、其中需要注意的细节是当存储最后一项时需要加'\0'，并且在字符串数组中存储整型数据时需要类型转换加char,而且需要加上数字字符'0'的ASC码值
5、在遍历数据时最后几个相同的数或者最后一个数需要在遍历之外额外添加最后一项的值
