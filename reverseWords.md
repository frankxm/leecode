给定一个字符串，你需要反转字符串中每个单词的字符顺序，同时仍保留空格和单词的初始顺序。

示例 1:

输入: "Let's take LeetCode contest"
输出: "s'teL ekat edoCteeL tsetnoc" 

注意：在字符串中，每个单词由单个空格分隔，并且字符串中不会有任何额外的空格。


void reverse(int i,int j,char *arr){
    while(i<j){
        char temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
        i++;j--;
    }
}
char * reverseWords(char *s){
    int length=strlen(s);
    int i=0;int start=0;int end=0;
    for(int i=0;i<length+1;i++){
        if((s[i]==' ')||(s[i]=='\0')){
            reverse(start,end,s);
            start=i+1;
        }
        end=i;
    }
return s;
}

做题感悟：
进行一次遍历当遇到空格时就翻转前面的，每一次翻转后记录新的起始坐标，每一次遍历则更新末尾坐标。特殊情况为strlen计算的字符串长度不包含'\0'，所以要考虑'\0'
