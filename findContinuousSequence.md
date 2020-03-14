/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** findContinuousSequence(int target, int* returnSize, int** returnColumnSizes){
    int n=target/2;
    int **answer=(int **)malloc(sizeof(int*)*n);
    *returnColumnSizes=(int *)malloc(sizeof(int)*n);
    *returnSize=0;
    int temp=0;int i=0;int j=0;int k=0;
        for(i=1;i<=n;i++){
            temp=0;
        j=i;
        while(temp<target){
            temp+=j;
            j++;
        }
        if(temp==target){
            answer[*returnSize]=(int*)malloc(sizeof(int)*(j-i));
            for(k=0;k<(j-i);k++){
            answer[*returnSize][k]=i+k;
            (*returnColumnSizes)[*returnSize]=k+1;
            }
        (*returnSize)++;
    }
}
return answer;}


1、不理解（j-i)是什么回事，按理说是j-i+1——————————while循环！while循环是先判断条件再执行语句，如果要终止循环必须条件不满足。但是前提是在判断前面的一个循环内的语句要执行完
这里虽然当temp等于了target但是要执行完j++才能再次判断，所以最后j多加了一次
