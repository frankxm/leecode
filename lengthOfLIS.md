给定一个无序的整数数组，找到其中最长上升子序列的长度。

示例:

输入: [10,9,2,5,3,7,101,18]
输出: 4 
解释: 最长的上升子序列是 [2,3,7,101]，它的长度是 4。

说明:

    可能会有多种最长上升子序列的组合，你只需要输出对应的长度即可。
    你算法的时间复杂度应该为 O(n2) 。

进阶: 你能将算法的时间复杂度降低到 O(n log n) 吗?


int lengthOfLIS(int* nums, int numsSize){
    if(numsSize==0)
    return NULL;
    int array[numsSize];
    array[0]=nums[0];int index=0;
    int length=1;
    for(int i=0;i<numsSize;i++){
        if(nums[i]>array[index]){
            index++;
            array[index]=nums[i];
            length++;
        }
        else if(nums[i]<array[index]){
            for(int j=index;j>=0;j--){
                if(j==0||array[j-1]<nums[i]){
                    array[j]=nums[i];
                    break;
                }
            }
        }
    }
    return length;
}
