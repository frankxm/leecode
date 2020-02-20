给定一个非空字符串 s，最多删除一个字符。判断是否能成为回文字符串。

示例 1:

输入: "aba"
输出: True

示例 2:

输入: "abca"
输出: True
解释: 你可以删除c字符。

注意:

    字符串只包含从 a-z 的小写字母。字符串的最大长度是50000。


bool validPalindrome(char * s){
    int length=strlen(s);
    if(length>50000)
    return NULL;
    bool answer=false;int i=0;int j=0;int k=0;
    for( i=0;i<(length/2);i++){
        if(s[i]!=s[length-1-i])
        break;
    }
    int tick_first=i;int tick_second=length-1-i;
    j=tick_first;int count=0;
    if(i==(length/2))
    return true;
    else{
        char *strs=(char*)malloc(sizeof(char)*(length-1));
        while(count!=2){
        for( i=0;i<length;i++){
            if(i==j)
            continue;
            strs[k++]=s[i];
        }
        for( i=0;i<((length-1)/2);i++){
            if(strs[i]!=strs[length-2-i]){
                j=tick_second;
                count++;
                k=0;
                break;
            }
        }
        if(i==((length-1)/2))
        return true;
    }
}
return answer;}


做题感悟：
1、原来思路是先判断原字符串是否回文，若回文就返回。若不回文则依次删除元素判断是否回文，中途删除元素用设定新数组的方式。但此方法超时，因为它从头逐个删减时间复杂度为N方
2、当首次判断不是回文串时遍历终止，此时说明当前位置的两个元素需要删除判断，如果两个元素各删除都无法回文则返回错。若满足题目的回文则当前两个元素一定有一个多余，所以各删除一个后可得
