给定一个仅包含大小写字母和空格 ' ' 的字符串 s，返回其最后一个单词的长度。

如果字符串从左向右滚动显示，那么最后一个单词就是最后出现的单词。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指仅由字母组成、不包含任何空格的 最大子字符串。

 

示例:

输入: "Hello World"
输出: 5



int lengthOfLastWord(char * s){
    int length=strlen(s);
    if(!length)
    return 0;
    int answer=0;int tick=0;
    for(int i=length-1;i>=0;i--){
        if(s[i]!=' '){
            tick=i;
            break;
            }}
            for(int i=tick;i>=0;i--){
                if(s[i]==' ')
                break;
                answer++;
            }
            return answer;}
            
   做题感悟：
   直接从尾部遍历，当不是空格时说明此时遍历到了最后一个单词再计数
