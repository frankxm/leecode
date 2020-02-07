编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

示例 1:

输入: ["flower","flow","flight"]
输出: "fl"

示例 2:

输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。

说明:
所有输入只包含小写字母 a-z 。




char * longestCommonPrefix(char ** strs, int strsSize){
/*当没有字符串大小时，即输入【】时*/
    if(!strsSize)
    return "";
/*当只有一个字符串或者字符串为“ ”时返回本身*/
    if(strsSize<=1)
    return (*strs);
/*正常情况先判断各字符串长度大小，以长度最小为标准*/
    int tick=1;int i=0;int j=0;int flag=0;int k=0;
    int length[strsSize];
    for(int k=0;k<strsSize;k++)
    length[k]=strlen(strs[k]);
    for(int i=0;i<strsSize-1;i++){
        for(int j=i+1;j<strsSize;j++){
            if(length[i]>length[j]){
                int temp=length[i];
                length[i]=length[j];
                length[j]=temp;
            }
        }
    }
/*j不能超过字符串最小长度否则会越界*/
    int min_num=length[0];
/*纵向分析各字符串同样位置，如果tick满strsSize的话则同样位置的值相同*/
       while(j<min_num){
    while(i<(strsSize-1)){
        if(strs[i][j]!=strs[i+1][j])
        break;
        tick++;
        i++;}
    if(tick!=strsSize)
        break;
    else if(tick==strsSize){
        tick=1;flag++;i=0;j++;
    }}
  /*flag表示出现相同的次数，再以第一个的前flag来赋值*/
    if(flag==0)
    return "";
        char *answer=(char*)malloc(sizeof(char)*(flag+1));
        for( k=0;k<flag;k++)
        answer[k]=0;
        for( k=0;k<flag;k++){
            answer[k]=strs[0][k];}
            answer[k]='\0';
            return answer;}



做题感悟：
1、本题主要注意数组越界：一、每个字符串长度越界  二、字符串为空  三、字符串个数i ，在判断两字符串时越界
2、字符串最后要手动加‘\0’
3、思路就是从每个字符串相同位置进行遍历，如果同样位置值相同那么tick就增加，如果不同就停止判断。某一位置判断完后再重新前面操作，因此要用while，中途只要出现不同的情况就break
4、最后就根据前面记录个数的 flag来赋值
