给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
 
int *twoSum(int *nums,int numSize,int target,int *returnSize){
    int*answer=(int*)malloc(sizeof(int)*2);
    *returnSize=2;
for(int i=0;i<numSize-1;i++){
    for(int j=i+1;j<numSize;j++){
if(nums[i]+nums[j]==target){
            answer[0]=i;
            answer[1]=j;
        }
    }
}
return answer;
}


做题心得：
1、做了此题以后才知道需要根据题目信息来做。一开始做的时候我忽略了题目本来给定的函数条件，题目本身就给了一个函数让自己来完善，同时给了几个变量，这些都是需要用到的。
2、题目的returnSize 在做题中一开始没用上，实际上是关键。题目中说要假设每次输入只会对应一种答案，所以说明returnSize的大小只能赋值为2。
3、题目中还要求需要自己给返回值answer动态分配一个内存，学到了动态分配内存的方法。  int*answer=(int*)malloc(sizeof(int)*2)  定义一个指针变量,然后函数malloc的返回值为void,所以需要将其强制转换为int 型，之后(sizeof(int)*2)表示分配两个int大小的内存空间。
4、此题我用的是比较笨的遍历算法，通过分别将每个数遍历，将其相加值与标准值比较

