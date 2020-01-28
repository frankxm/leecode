给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。

 

示例：

给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]



/**
 * Return an array of arrays of size *returnSize.
 * The sizes of the arrays are returned as *returnColumnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
    int** threeSum(int* nums, int numsSize, int* returnSize,int **returnColumnSizes){
    for(int i=0;i<numsSize-1;i++){
        for(int j=i+1;j<numsSize;j++){
            if(nums[i]>nums[j]){
                int temp=nums[i];
                nums[i]=nums[j];
                nums[j]=temp;
            }
        }
    }
    int i=0;int j=0;int k=0;int tick=0;int pointer=0;
   *returnColumnSizes=(int*)malloc(sizeof(int)*200000);
    int **answer = (int **)malloc(sizeof(int *) * 200000);
    for(i=0;i<numsSize-2;i++){
        if(nums[i]!=nums[i-1]&&(i>0)||i==0){
        tick=-nums[i];
        j=i+1;
        k=numsSize-1;
        while(j<k){
            if(nums[k]+nums[j]==tick){
                answer[++pointer]=(int*)malloc(sizeof(int)*3);
                answer[pointer][0]=nums[i];
                answer[pointer][1]=nums[j];
                answer[pointer][2]=nums[k];
                 (*returnColumnSizes)[pointer]=3;
            while(j<k&&nums[j]==nums[j+1]){
                j++;
            }
            while(j<k&&nums[k]==nums[k-1]){
                k--;
                }
                j++;k--;
            }
            else if(nums[k]+nums[j]<tick){
                while(j<k&&nums[j]==nums[j+1]){
                    j++;
                }
                j++;}
            else if(nums[k]+nums[j]>tick){
                while(j<k&&nums[k]==nums[k-1]){
                    k--;
                }
                k--;}            
            }}}
            *returnSize=pointer+1;
return answer;
}
