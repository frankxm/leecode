给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:

输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。

进阶:

如果你已经实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。


int maxSubArray(int* nums, int numsSize){
    int tick=0;int sum=0;int start=0;
    /*将数列的首位元素作为中间值
    tick=nums[0];
    */
    /*每次遍历以该元素为开头进行第二次遍历*/
    for(int i=0;i<numsSize;i++){
        start=0;
        start=start+nums[i];
        sum=start;
        /*当遍历到中间元素时判定本身
        if(i!=0&&i!=numsSize-1&&nums[i]>tick){
            tick=nums[i];
        }
        */
        /*对遍历的最后一个元素本身判定
        else if(i==numsSize-1&&nums[i]>tick){
            tick=nums[i];
        }
        */
        /*第二次遍历求和*/
        for(int j=i+1;j<numsSize;j++){
            sum=sum+nums[j];
            if(sum>tick){
                tick=sum;
            }
        }
    }
return tick;
}




做题感悟：
1、该题我的思路为首先从头遍历，将各元素作为开头start然后以此为标准向后遍历，并循环相加，若和大于中间值则将值转换
2、其中注意细节为：每一次以新的元素为标准进行二次遍历时，需要判断是否该元素大于tick     
if(i!=0&&i!=numsSize-1&&nums[i]>tick){
            tick=nums[i];
        }
3、当遍历到最后时也需要单独判断
