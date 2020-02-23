给定一个由空格分割单词的句子 S。每个单词只包含大写或小写字母。

我们要将句子转换为 “Goat Latin”（一种类似于 猪拉丁文 - Pig Latin 的虚构语言）。

山羊拉丁文的规则如下：

    如果单词以元音开头（a, e, i, o, u），在单词后添加"ma"。
    例如，单词"apple"变为"applema"。

    如果单词以辅音字母开头（即非元音字母），移除第一个字符并将它放到末尾，之后再添加"ma"。
    例如，单词"goat"变为"oatgma"。

    根据单词在句子中的索引，在单词最后添加与索引相同数量的字母'a'，索引从1开始。
    例如，在第一个单词后添加"a"，在第二个单词后添加"aa"，以此类推。

返回将 S 转换为山羊拉丁文后的句子。

示例 1:

输入: "I speak Goat Latin"
输出: "Imaa peaksmaaa oatGmaaaa atinLmaaaaa"

示例 2:

输入: "The quick brown fox jumped over the lazy dog"
输出: "heTmaa uickqmaaa rownbmaaaa oxfmaaaaa umpedjmaaaaaa overmaaaaaaa hetmaaaaaaaa azylmaaaaaaaaa ogdmaaaaaaaaaa"

说明:

    S 中仅包含大小写字母和空格。单词间有且仅有一个空格。
    1 <= S.length <= 150。


char * toGoatLatin(char * S){   
    char *answer=(char*)malloc(sizeof(char)*5000);
    memset(answer,'\0',sizeof(answer));
    int length=strlen(S);
    int count_number=0;int tick=0;int j=0;int current=0;int i=0;int count=0;
    while(tick!=length){
        count_number++;
    if((S[current]=='a')||(S[current]=='e')||(S[current]=='i')||(S[current]=='o')||(S[current]=='u')||(S[current]=='A')||(S[current]=='E')||(S[current]=='I')||(S[current]=='O')||(S[current]=='U')){
        for( i=current;((S[i]!=' ')&&(S[i]!='\0'));i++)
            answer[j++]=S[i];
            current=i+1;
        answer[j]='m';
        answer[j+1]='a';
        for( i=1;i<count_number+1;i++)
            answer[j+1+i]='a';
            tick=current-1;
            answer[j+2+count_number]=' ';
        j=j+3+count_number;
        }
    else{
            answer[j++]=S[current+1];
            for(i=current+2;((S[i]!=' ')&&(S[i]!='\0'));i++)
            answer[j++]=S[i];
        answer[j]=S[current];
        current=i+1;
        answer[j+1]='m';
        answer[j+2]='a';
        for(i=1;i<count_number+1;i++)
        answer[j+2+i]='a';
        tick=current-1;
        answer[j+3+count_number]=' ';
        j=j+4+count_number;
        }
    }
    count=strlen(answer);
    count++;
    char *des=(char*)malloc(sizeof(char)*count);
    memset(des,'\0',sizeof(char)*count);
    for(int k=0;k<count;k++)
    des[k]=answer[k];
    return des;
}
