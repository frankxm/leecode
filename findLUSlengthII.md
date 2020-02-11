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
    int length[strsSize];int answer=-1;
    int index_first=0;int index_second=0;int k=0;int tick_first=0;int tick_second=0;
    for(int i=0;i<strsSize;i++){
        length[i]=strlen(strs[i]);
    }
    for(int i=0;i<strsSize-1;i++){
        for(int j=i+1;j<strsSize;j++){
            if(length[i]<length[j]){
                char temp=strs[i];
                strs[i]=strs[j];
                strs[j]=temp;
            }
        }
    }
    for(int i=0;i<strsSize-1;i++){
        if(length[i]==length[i+1]){
            index_second=0;index_first=0;
            while(index_second<length[i+1]){
                int j=i;
                if(strs[j][index_first]!=strs[j+1][index_second]){
                    answer=length[j];
                    break;
                }
                index_first++;index_second++;
            }
             if(index_second!=length[i+1])
            break;}
        else if(length[i]>length[i+1]){
            if(i==0){
            answer=length[0];
            break;}
            for( k=0;k<length[i];k++){
                if(strs[i][k]==strs[i+1][0]){
                    tick_first=k; tick_second=0;
                    tick_first++;tick_second++;break;
                    }}
                if(k==length[i])
                answer=length[i+1];
        while(tick_second<length[i+1]){
            while(tick_first<length[i]){
                if(strs[i][tick_first]==strs[i+1][tick_second])
                break;
                tick_first++;
            }
            if(tick_first==length[i])
            break;
            tick_first++;
            tick_second++;}
                if(tick_first==length[i]&&tick_second!=length[i+1])
            answer=length[i+1];
                else if(tick_second==length[i+1])
                continue;}}
                return answer;}
