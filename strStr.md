实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

示例 1:

输入: haystack = "hello", needle = "ll"
输出: 2

示例 2:

输入: haystack = "aaaaa", needle = "bba"
输出: -1

说明:

当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。


int strStr(char * haystack, char * needle){
    int length_first=strlen(haystack);
    int length_second=strlen(needle);
    int answer=0;
    int tick_second=0;int tick_first=0;
    /*如果haystack长度小于needle*/
    if(length_first<length_second）
    return -1;
    /*如果needle为空字符串*/
    if(!length_second)
    return 0;
    /*如果needle只为1个位，就遍历判断有没有出现它的情况*/
    if(length_second==1){
        for(int k=0;k<length_first;k++){
            if(haystack[k]==needle[0]){
            answer=k;break;
        }}
    }
    /*遍历直到找到与needle第一个位相同的数，之后同时往后遍历判断*/
    for(int k=0;k<length_first;k++){
        if(haystack[k]!=needle[0])
        answer++; }
        if(answer==length_first)
        return -1;
    int flag=0;answer=0;
    for(int i=0;i<length_first;i++){
        if(haystack[i]==needle[tick_second]){
            tick_first=i;flag=i;tick_first++;tick_second++;
            while(tick_second<length_second){
                if(haystack[tick_first]!=needle[tick_second]){
                    tick_second=0;flag=-1;break;}
                 flag++;tick_first++;tick_second++;}}}
    answer=flag-tick_second+1;
    /*如果判断都没找到匹配needle的情况，就把answer的值改变，通过中间值flag实现*/
    if(flag==-1)
    answer=-1;
    return answer;}
    
    
   做题感悟：
   1、需要注意几个特殊情况 一2、字符串为空 二、子字符串为1直接判断有没有和子相同 三、子字符串不为1
   2、在正常情况时，我的思路是：先将haystack遍历，遍历到某一字符与needle第一个字符相同时开始while循环。while循环中如果每次比较不相同就break退出，如果相同就各下标增加。每一次增加都要用flag来记录最后位置，最后再用answer来结算
   3、在正常情况中，如果分析出没有匹配needle的情况，那么answer就要变为-1 因此每次匹配失败时flag我把它赋值为-1。原来我赋值为0，这样的话容易造成位置在第一项的误解
