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
int* addToArrayForm(int* A, int ASize, int K, int* returnSize){
    int count=0;int i=0;int size=0;int add=0;
    int mark=0;*returnSize=ASize;int r=K;
    int *tick=(int*)malloc(sizeof(int)*ASize);
        while(r!=0){
            r=r/10;
            count++;
        }
        if(K==0){
            *returnSize=ASize;
            return A;
        }
        int *nums=(int*)malloc(sizeof(int)*count);
        for(i=(count-1);i>=0;i--){
            nums[i]=(K%10);
            K=(K/10);
        }
        if(ASize>=count){
               for(int i=0;i<ASize;i++)
    tick[i]=A[i];
        mark=(ASize-count);
        tick[count-1+mark]=((nums[count-1]+A[count-1+mark])%10);
        for(int j=(count-1);j>=1;j--){
                if((nums[j]+A[j+mark]+add)>=10){
                add=1;
                tick[j-1+mark]=((nums[j-1]+A[j+mark-1]+add)%10);
                }
                else if((nums[j]+A[j+mark]+add)<10){
                    add=0;
                    tick[j-1+mark]=((nums[j-1]+A[j+mark-1]+add)%10);
                }}
                if(((nums[0]+A[mark]+1)>=10)||((nums[0]+A[mark])>=10)||tick[0]==0){
                    for(int k=(mark-1);k>=0;k--){
                        if(tick[k]!=9){
                        tick[k]++;
                        return tick;
                        break;}
                        tick[k]=0;
                    }
                        int *answer=(int*)malloc(sizeof(int)*(ASize+1));
                        answer[0]=1;
                        for(int k=1;k<(ASize+1);k++)
                        answer[k]=tick[k-1];
                        *returnSize=(ASize+1);
                    return answer;
                }
                else return tick;}
                else if(ASize<count){
                       for(int i=0;i<count;i++)
    tick[i]=nums[i];
                 mark=(count-ASize);
        tick[ASize-1+mark]=((nums[ASize-1]+A[ASize-1+mark])%10);
        for(int j=(ASize-1);j>=1;j--){
                if((nums[j+mark]+A[j]+add)>=10){
                add=1;
                tick[j-1+mark]=((nums[j-1+mark]+A[j-1]+add)%10);
                }
                else if((nums[j+mark]+A[j]+add)<10){
                    add=0;
                    tick[j-1+mark]=((nums[j-1+mark]+A[j-1]+add)%10);
                }}
                if(((nums[mark]+A[0]+1)>=10)||((nums[mark]+A[0])>=10)||tick[0]==0){
                    for(int k=(mark-1);k>=0;k--){
                        if(tick[k]!=9){
                        tick[k]++;
                        return tick;
                        break;}
                        tick[k]=0;
                    }
                        int *answer=(int*)malloc(sizeof(int)*(count+1));
                        answer[0]=1;
                        for(int k=1;k<(count+1);k++)
                        answer[k]=tick[k-1];
                        *returnSize=(count+1);
                    return answer;
                }
                else 
                return tick;}
                return tick;}
