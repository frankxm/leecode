给定字符串列表，你需要从它们中找出最长的特殊序列。最长特殊序列定义如下：该序列为某字符串独有的最长子序列（即不能是其他字符串的子序列）。

子序列可以通过删去字符串中的某些字符实现，但不能改变剩余字符的相对顺序。空序列为所有字符串的子序列，任何字符串为其自身的子序列。

输入将是一个字符串列表，输出是最长特殊序列的长度。如果最长特殊序列不存在，返回 -1 。

 

示例：

输入: "aba", "cdc", "eae"
输出: 3

 

提示：

    所有给定的字符串长度不会超过 10 。
    给定字符串列表的长度将在 [2, 50 ] 之间。

int findLUSlength(char ** strs, int strsSize){
    int answer=-1;char flag;
    int index_first=0;int index_second=0;int k=0;int tick_first=0;int tick_second=0;
    for(int i=0;i<strsSize-1;i++){
        for(int j=i+1;j<strsSize;j++){
            if(strlen(strs[i])<strlen(strs[j])){
                char *temp=' ';
                temp=strs[i];
                strs[i]=strs[j];
                strs[j]=temp;
            }
        }
    }
    for(int i=0;i<(strsSize-1);i++){
        if(strlen(strs[i])==strlen(strs[i+1])){
            index_second=0;index_first=0;
            while(index_second<strlen(strs[i+1])){
                if(strs[i][index_first]!=strs[i+1][index_second]){
                    answer=strlen(strs[i]);
                    break;
                }
                index_first++;index_second++;
            }
             if(index_second!=strlen(strs[i+1]))
            break;}
        else if(strlen(strs[i])>strlen(strs[i+1])){
            if(i==0){
            answer=strlen(strs[0]);
            break;}
            for( k=0;k<strlen(strs[i]);k++){
                if(strs[i][k]==strs[i+1][0]){
                    tick_first=k; tick_second=0;
                    tick_first++;tick_second++;break;
                    }}
                if(k==strlen(strs[i])){
                answer=strlen(strs[i+1]);
                break;}
        while(tick_second<strlen(strs[i+1])){
            while(tick_first<strlen(strs[i])){
                if(strs[i][tick_first]==strs[i+1][tick_second])
                break;
                tick_first++;
            }
            if(tick_first==strlen(strs[i]))
            break;
            tick_first++;
            tick_second++;}
                if(tick_first==strlen(strs[i])&&tick_second!=strlen(strs[i+1])){
            answer=strlen(strs[i+1]);break;}
                }}
        if(strlen(strs[0])==1){
           for(int i=0;i<strsSize-1;i++){
               flag=strs[i][0];
               for(int j=i+1;j<strsSize;j++){
                   if(strs[i][0]==strs[j][0]){
                       strs[j][0]=0;
                       flag=0;
                   }}
                   strs[i][0]=flag;
               }
           for(int i=0;i<strsSize;i++){
               if(strs[i][0]!=0){
               answer=1;break;}
               answer=-1;
           }}
                return answer;}
