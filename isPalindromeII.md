给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

示例 1:

输入: "A man, a plan, a canal: Panama"
输出: true

示例 2:

输入: "race a car"
输出: false




bool isPalindrome(char * s){
    int length=strlen(s);
    if(!length)
    return NULL;
    if(s=="")
    return true;
    if(length==1){
        if(s=="")
        return true;
        else
        return false;
    }
    bool answer=false;
    int index_first=0;int index_second=length-1;
    for(int i=0;i<length;i++){
        if(s[i]<65||s[i]>122||(s[i]>90&&s[i]<97))
        s[i]=0;
    }
    while(1){
        if(s[index_first]==s[index_second]){
            index_first++;index_second--;
        }
        else {
            if((s[index_first]+32==s[index_second])||(s[index_second]+32==s[index_first])){
                index_first++;index_second--;
            }
            else {
                if(s[index_first]==0)
                index_first++;
                else if(s[index_second]==0)
                index_second--;
                else
                break;
        }}
        if((index_first==index_second)||(index_second+1==index_first)){
        answer=true;
        break;}
    }
    return answer;
}
