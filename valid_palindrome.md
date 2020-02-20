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
    if(i==(length/2))
    return true;
    else{
        char *strs=(char*)malloc(sizeof(char)*(length-1));
        while(j!=length){
        for( i=0;i<length;i++){
            if(i==j)
            continue;
            strs[k++]=s[i];
        }
        for( i=0;i<((length-1)/2);i++){
            if(strs[i]!=strs[length-2-i]){
                j++;
                k=0;
                break;
            }
        }
        if(i==((length-1)/2))
        return true;
    }
}
return answer;}
