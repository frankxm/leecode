对于非负整数 X 而言，X 的数组形式是每位数字按从左到右的顺序形成的数组。例如，如果 X = 1231，那么其数组形式为 [1,2,3,1]。

给定非负整数 X 的数组形式 A，返回整数 X+K 的数组形式。

 

示例 1：

输入：A = [1,2,0,0], K = 34
输出：[1,2,3,4]
解释：1200 + 34 = 1234

示例 2：

输入：A = [2,7,4], K = 181
输出：[4,5,5]
解释：274 + 181 = 455

示例 3：

输入：A = [2,1,5], K = 806
输出：[1,0,2,1]
解释：215 + 806 = 1021

示例 4：

输入：A = [9,9,9,9,9,9,9,9,9,9], K = 1
输出：[1,0,0,0,0,0,0,0,0,0,0]
解释：9999999999 + 1 = 10000000000

 

提示：

    1 <= A.length <= 10000
    0 <= A[i] <= 9
    0 <= K <= 10000
    如果 A.length > 1，那么 A[0] != 0




/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
#define max(a,b)  a>=b?a:b
int* addToArrayForm(int* A, int ASize, int K, int* returnSize){
    int a=K;int count=0;
    /*求出K的位数，注意不能直接使用，否则K的值会改变*/
    while(a!=0){
        count++;
        a=a/10;
    }
   /*用动态分配来定义一个新的数组，来进行运算和存储，注意新数组的长度为K和A中的长值加一*/
    int m=max(ASize,count);
    *returnSize=m;
    int M=m;
    /*定义一个数组同时要初始化为0,这样之后进位可以通过赋值实现*/
    int *answer=(int*)malloc(sizeof(int)*(m+1));
    for(int j=0;j<m;j++){
        answer[j]=0;
    }
    int b=ASize;
    /*接下来分两种情况计算*/
    if(ASize>=count){
    while(b>0){
        answer[m-1]=A[b-1]+K%10+answer[m-1];
        /*如果第一个数也大于等于10，那么需要增加answer长度*/
        if(answer[0]>=10){
            answer[0]=answer[0]-10;
           int *ans=(int*)malloc(sizeof(int)*(M+2));
            ans[0]=1;
            for(int j=0;j<(M+1);j++){
                ans[j+1]=answer[j];
            }
            *returnSize=M+1;
            return ans;
        }
        /*计算的方法位先把各个元素相加，如果大于10，再处理*/
        if(answer[m-1]>=10){
            answer[m-1]=answer[m-1]-10;
            answer[m-2]=1;
        }
        m--;
        b--;
        K=K/10;
    }}
    /*当A只有一个数并且只为0时，特殊考虑，直接把K的各位赋值给answer*/
    else if(A[0]==0){
        for(int i=M-1;i>=0;i--){
        answer[i]=K%10;
        K=K/10;
    }
    return answer;}
    else if(ASize<count){
    /*当b小于等于0是需要退出循环，因为数组会溢出*/
        while(K!=0&&b>0){
         answer[m-1]=A[b-1]+K%10+answer[m-1];
        if(answer[0]>=10){
            answer[0]=answer[0]-10;
           int *ans=(int*)malloc(sizeof(int)*(M+2));
            ans[0]=1;
            for(int j=0;j<(M+1);j++){
                ans[j+1]=answer[j];
            }
            *returnSize=M+1;
            return ans;
        }
        if(answer[m-1]>=10){
            answer[m-1]=answer[m-1]-10;
            answer[m-2]=1;
        }
        m--;
        b--;
        K=K/10;
    }
    /*退出while循环后*/
    for(int i=m-1;i>=0;i--){
        answer[i]=K%10+answer[i];
        if(answer[0]>=10){
            answer[0]=answer[0]-10;
           int *ans=(int*)malloc(sizeof(int)*(M+2));
            ans[0]=1;
            for(int j=0;j<(M+1);j++){
                ans[j+1]=answer[j];
            }
            *returnSize=M+1;
            return ans;
        }
        if(answer[i]>=10){
            answer[i]=answer[i]-10;
            answer[i-1]=1;
        }
        K=K/10;
    }}
    return answer;
}



做题感悟：
1、这道题需要定义一个新数组answer来计算同时进行存储，这样可以解决进位的问题。注意本题的 answer的长度要选ASIZE和COUNT中更长的，并且还要 加一 。（应该是防止A到时候过大导致溢出）
2、注意answer要都初始化为0，这样就能让answer里面的元素参与计算，如果A或K有一方长，这种情况下同样可以计算。
3、注意要分哪个数组长度更长的情况。因为如果A更长answer[i]=answer[i]+A[i]+K%10 就成立，在这种情况下当K的位数加完时，就为0因此可以继续参与运算。但如果K更长，那么当A加完时如果继续加数组就会溢出（即出现A【-1】A【-2】的情况) 这时候就需要停止，重新将剩余的K处理。
