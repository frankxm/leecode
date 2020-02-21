给定一个字符串 S，返回 “反转后的” 字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。

 

示例 1：

输入："ab-cd"
输出："dc-ba"

示例 2：

输入："a-bC-dEf-ghIj"
输出："j-Ih-gfE-dCba"

示例 3：

输入："Test1ng-Leet=code-Q!"
输出："Qedo1ct-eeLg=ntse-T!"

 

提示：

    S.length <= 100
    33 <= S[i].ASCIIcode <= 122 
    S 中不包含 \ or "



void reverse(int i,int j,char *S){
    while(i<j){
        char temp=S[i];
        S[i]=S[j];
        S[j]=temp;
        i++;j--;
    }
}
char * reverseOnlyLetters(char * S){
    int length=strlen(S);
    if(!length)
    return "";
    char tick[length];int j=0;
    for(int i=0;i<length+1;i++){
        if((S[i]>='A'&&S[i]<='Z')||(S[i]>='a'&&S[i]<='z')){
            tick[j++]=S[i];
        }
    }
    int count=j;
    reverse(0,j-1,tick);
    j=0;
    for(int i=0;i<length+1;i++){
        if((S[i]>='A'&&S[i]<='Z')||(S[i]>='a'&&S[i]<='z')){
          S[i]=tick[j++];
          if(j==count)
          break;  
        }
    }
    return S;
}


做题感悟：
类比之前翻转，设定一个新数组存储字母，再于新数组tick中进行翻转操作，操作完后依次放回原数组
