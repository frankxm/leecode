给定两个字符串 A 和 B, 寻找重复叠加字符串A的最小次数，使得字符串B成为叠加后的字符串A的子串，如果不存在则返回 -1。

举个例子，A = "abcd"，B = "cdabcdab"。

答案为 3， 因为 A 重复叠加三遍后为 “abcdabcdabcd”，此时 B 是其子串；A 重复叠加两遍后为"abcdabcd"，B 并不是其子串。

注意:

 A 与 B 字符串的长度在1和10000区间范围内。



int repeatedStringMatch(char * A, char * B){
    int length_a=strlen(A);
    int length_b=strlen(B);
    int count=0;int j=0;int k=0;
    for(int i=0;i<length_a;i++){
        if(B[0]==A[i]){
            count=1;j=i;k=0;
            while(k<length_b){
                if(A[j]!=B[k]){
                    count=-1;k=0;j=0;
                    break;
                }
                j++;
                if(j==length_a){
                    j=0;
                    count++;}
                k++;}
            }
        }
        if(length_a==1)
        count--;
        if(length_a>length_b)
        count--;
        if(count==0)
        return -1;
        else
        return count;
    }
