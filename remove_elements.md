给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。

示例 1:

给定 nums = [3,2,2,3], val = 3,

函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。

你不需要考虑数组中超出新长度后面的元素。

示例 2:

给定 nums = [0,1,2,2,3,0,4,2], val = 2,

函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。

注意这五个元素可为任意顺序。

你不需要考虑数组中超出新长度后面的元素。

说明:

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以“引用”方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

// nums 是以“引用”方式传递的。也就是说，不对实参作任何拷贝
int len = removeElement(nums, val);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中该长度范围内的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}


int removeElement(int* nums, int numsSize, int val){
/*定义一个count记录所需要返回的大小，定义start作为起点
    int count=0;int start;
    */
    /*一开始就直接找出需要返回的大小
    for(int k=0;k<numsSize;k++){
        if(nums[k]!=val)
        count++;
    }
    */
    /*就地修改元素，从起点遍历直至遇到第一个不需要删除的元素，与起点互换
    if(count>0){
    for(int i=0;i<numsSize;i++){
         if(nums[i]==val){
            start=i;
            for(int j=start;j<numsSize;j++){
                if(nums[j]!=val){
                    nums[start]=nums[j];
                    nums[j]=val;
                    break;
                }}}}}
                */
                return count;}
                

做题感悟：
1、本题与“删除数组重复元素”类似，都是需要在返回新数组的大小同时还需要就地修改数组
2、就地修改数组的思路是——调换位置 即先找到需要“删除”的元素，然后从这个元素为起点向后找，当找到与它不同的元素时就将该元素与起点元素互换数值，就起到
了删除的作用。同时每次换元素时就结束遍历，保证互换的元素一定是第一个元素。
 for(int i=0;i<numsSize;i++){
         if(nums[i]==val){
            start=i;
            for(int j=start;j<numsSize;j++){
                if(nums[j]!=val){
                    nums[start]=nums[j];
                    nums[j]=val;
                    break;
3、有个隐含情况是：当数组中所有元素都需要删除时，需要特殊考虑。








