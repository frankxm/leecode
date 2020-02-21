给定一个字符串和一个整数 k，你需要对从字符串开头算起的每个 2k 个字符的前k个字符进行反转。如果剩余少于 k 个字符，则将剩余的所有全部反转。如果有小于 2k 但大于或等于 k 个字符，则反转前 k 个字符，并将剩余的字符保持原样。

示例:

输入: s = "abcdefg", k = 2
输出: "bacdfeg"

要求:

    该字符串只包含小写的英文字母。
    给定字符串的长度和 k 在[1, 10000]范围内。



void reverse(int i,int j,char *arr){

    while(i<j){
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
        i++;j--;
    }
}
char * reverseStr(char * s, int k){
    int start=0;
    int length=strlen(s);
    while(start<length){
        if(start+2*k<length)
            reverse(start,start+k-1,s);
        else if(start+k<length)
            reverse(start,start+k-1,s);
        else if(start+k>=length)
            reverse(start,length-1,s);
            start+=2*k;
}
return s;}


做题感悟：
1、题目就是要求对每K个数进行翻转，之后跳过K个数然后重复之前操作。但是需要判断翻转后的数是否满K。
正常情况下翻转后进行后面2K个数的循环，当剩余数满K不满2K时就另一种情况，特殊情况为剩余不满K
2、直接引用函数可以提高运行速度，引用函数时对于数组输入变量时是输入数组名
