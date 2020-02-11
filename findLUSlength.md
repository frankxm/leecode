给定两个字符串，你需要从这两个字符串中找出最长的特殊序列。最长特殊序列定义如下：该序列为某字符串独有的最长子序列（即不能是其他字符串的子序列）。

子序列可以通过删去字符串中的某些字符实现，但不能改变剩余字符的相对顺序。空序列为所有字符串的子序列，任何字符串为其自身的子序列。

输入为两个字符串，输出最长特殊序列的长度。如果不存在，则返回 -1。

示例 :

输入: "aba", "cdc"
输出: 3
解析: 最长特殊序列可为 "aba" (或 "cdc")

说明:

    两个字符串长度均小于100。
    字符串中的字符仅含有 'a'~'z'。

int findLUSlength(char * a, char * b){
    int length_a=strlen(a);
    int length_b=strlen(b);
    int j=0;
    if(length_a==length_b){
        for(int i=0;i<length_a;i++){
            if(a[i]!=b[j]){
            j=0;break;}
            j++;
        }
        if(j==length_a)
            return -1;
            else
            return length_a;
        }
    int answer=0;
    if(length_a>length_b)
    answer=length_a;
    else if(length_a<length_b)
    answer=length_b;
return answer;
}

做题感悟：
这道题关键时要理解题意：
当两个字符串长度相同时，如果字符串不同，那么返回的最长的子字符串就是本身，而且不会相同。
当两个字符串长度相同时，如果字符串相同，那么子字符串相同返回-1
当两个字符串长度不相同，那么返回最长的长度。因为长的字符串本身并不会成为短的子序列
