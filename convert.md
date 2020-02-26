将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "LEETCODEISHIRING" 行数为 3 时，排列如下：

L   C   I   R
E T O E S I I G
E   D   H   N

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。

请你实现这个将字符串进行指定行数变换的函数：

string convert(string s, int numRows);

示例 1:

输入: s = "LEETCODEISHIRING", numRows = 3
输出: "LCIRETOESIIGEDHN"

示例 2:

输入: s = "LEETCODEISHIRING", numRows = 4
输出: "LDREOEIIECIHNTSG"
解释:

L     D     R
E   O E   I I
E C   I H   N
T     S     G


char * convert(char * s, int numRows){
    int length=strlen(s);
    char *answer=(char*)malloc(sizeof(char)*(length+1));
    for(int j=0;j<length+1;j++)
    answer[j]=0;
    if(numRows<=1)
    return s;
    int step_first=0;int step_second=0;
    int flag=numRows*2-2;int count=1;
    int current=0;int i=0;int start=0;
    while(start<numRows){
        step_first=(numRows-start)*2-2;
        if(start==(numRows-1))
        step_first=flag;
        step_second=flag-step_first;
        answer[i++]=s[start];
        current=start;
        while(current<length){
        if(count%2!=0){
            current+=step_first;
            answer[i++]=s[current];
            count++;
        }
        else if(count%2==0){
            if(step_second==0){
                count++;
                continue;
            }
            current+=step_second;
            answer[i++]=s[current];
            count++;
        }}
        count=1;start++;}
        answer[i]='\0';
        return answer;
}
