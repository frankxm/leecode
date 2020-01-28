给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

示例 1:

输入: [1,3,5,6], 5
输出: 2

示例 2:

输入: [1,3,5,6], 2
输出: 1

示例 3:

输入: [1,3,5,6], 7
输出: 4

示例 4:

输入: [1,3,5,6], 0
输出: 0

int searchInsert(int* nums, int numsSize, int target){
    int tick=0;
    for(int i=0;i<numsSize;i++){
        if(nums[i]==target){
            tick=i;
            break;
        }
        else if(nums[i]!=target&&nums[i]>target){
            tick=i;
        break;
    }
        else if(nums[i]!=target&&nums[i]<target){
            tick++;
        }}
return tick;
}



做题感悟：
1、此题需要明确三种情况，一种为数组中存在目标，一种为数组不存在但是全比目标小，还有一种为数组不存在但是存在大于目标的数
2、做这种插入题时需要在得到坐标时及时退出循环，前两种可能都需要使用break
