给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).


int abs(int x){
    if(x>=0)
    return x;
    else 
    return -x;
}
int threeSumClosest(int* nums, int numsSize, int target){
    int answer=0;int target_new=0;int i=0;int j=0;int sum=0;
    for(int i=0;i<numsSize-1;i++){
        for(int j=i+1;j<numsSize;j++){
            if(nums[i]>nums[j]){
                int temp=nums[i];
                nums[i]=nums[j];
                nums[j]=temp;
            }
        }
    }
    answer=nums[0]+nums[1]+nums[numsSize-1];
    for(int k=0;k<numsSize-2;k++){
        i=k+1;
        j=numsSize-1;
        while(i<j){
            sum=nums[k]+nums[i]+nums[j];
            if(abs(sum-target)<abs(answer-target))
            answer=sum;
            if(sum>target)
            j--;
            else if(sum<target)
            i++;
            else if(sum==target){
            answer=sum;
            break;}
    }
    if(answer==target)
    break;}
    return answer;
}



做题感悟：
1、这题总思路就是先升序方式排序，在双指针遍历。因为在升序之后如果三数之和大于target则后指针往前，否则则前指针往后。在while里每一次判断三数之和前，都将当前的差值与之前的差值判断。这样在全部遍历完以后也就得出了最接近的和
2、一开始我的思路为当找到和为与之前不同时则结束，意思是：如果一开始是大于target，那么当小于target时则结束。之后发现这样遍历的话会出现少情况，比如当和不同于之前时 ，可能前面指针或者后面指针可以继续移动再减小差值
3、引用了abs求绝对值函数。
同时也了解到了比较字符串的strcmp函数。头文件为#include<stdio.h>，具体功能为将两个字符串同样位置做差，因为每个字符都有值，这样一来如果返回值为大于0的数说明该字符更大，若返回值小于0则说明该字符串更小，若为0则说明相同。
具体用法：
int strcmp(int const char*s1,int const char*s2);
