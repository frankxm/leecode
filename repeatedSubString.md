给定一个非空的字符串，判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母，并且长度不超过10000。

示例 1:

输入: "abab"

输出: True

解释: 可由子字符串 "ab" 重复两次构成。

示例 2:

输入: "aba"

输出: False

示例 3:

输入: "abcabcabcabc"

输出: True

解释: 可由子字符串 "abc" 重复四次构成。 (或者子字符串 "abcabc" 重复两次构成。)


法一：
bool repeatedSubstringPattern(char * s){
    int length=strlen(s);
    bool answer=false;
    for(int i=1;i<length;i++){
        if(s[i]==s[0]){
            int l=i;int j=0;
            if(length%l!=0)
            continue;
            for( j=i;j<length;j++){
                if(s[j]!=s[j%l])
                break;
            }
            if(j==length){
            answer=true;
            break;
        }}
    }
    return answer;
}




法二：（显示超时）
bool repeatedSubstringPattern(char * s){
    bool answer;
    int length_main=0;
    length_main=strlen(s);
    int l=0;int i=0;int j=0;int count=0;
    if(length_main>0&&length_main<=10000){
    while(l<=length_main){
        count++;
        l++;
        char tick[l];
        for(int k=0;k<l;k++)
        tick[k]=s[k];
        i=0;j=0;
        while(i<length_main){
            if(tick[j]!=s[i])
            break;
            j++;
            if(j==l)
            j=0;
            i++;
            }
            if(i==length_main&&j==0)
            break;
        }}
        if(i==length_main&&count!=length_main)
        answer=true;
        else
        answer=false;
        return answer;}
        
        
做题感悟：
1、两种方法思路其实相同：都是找到一个规定字符串来与原字符串比较，如果能遍历到结尾则这个字符串构成原字符串，如果不能则再往后规定字符串
2、法一比较与法二：
一、法一在规定字符串时，首先遍历直至遇到和第一个元素相同的字符，再判断此时字符串长度是否能整除总长  length%l!=0
    法二在规定字符串时，是一个个设置新的数组存储子字符串，如果某一长度的字符串能够遍历到尾即成功
二、法一在用子字符串比较时，是用此时位置与当前子字符串长度求余所得                if(s[j]!=s[j%l])
    法二是用假设的字符串同时比较，当达到长度就归0   
    while(i<length_main){
            if(tick[j]!=s[i])
            break;
            j++;
            if(j==l)
            j=0;
            i++;
            }
            if(i==length_main&&j==0)
            break;
    
