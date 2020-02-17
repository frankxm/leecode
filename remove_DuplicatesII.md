给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

示例 1:

给定 nums = [1,1,1,2,2,3],

函数应返回新长度 length = 5, 并且原数组的前五个元素被修改为 1, 1, 2, 2, 3 。

你不需要考虑数组中超出新长度后面的元素。

示例 2:

给定 nums = [0,0,1,1,1,1,2,3,3],

函数应返回新长度 length = 7, 并且原数组的前五个元素被修改为 0, 0, 1, 1, 2, 3, 3 。

你不需要考虑数组中超出新长度后面的元素。

说明:

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以“引用”方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

// nums 是以“引用”方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中该长度范围内的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}

在真实的面试中遇到过这道题？




int removeDuplicates(int* nums, int numsSize){
/*没有输入时返回空指针*/
    if(!numsSize)
    return NULL;
    int count=0;int tick[numsSize];int counts[numsSize];
    int j=0;int sum=0;int start=0;
    /*定义数组后及时初始化*/
    for(int i=0;i<numsSize;i++){
        tick[i]=0;
        counts[i]=0;
    }
    /*将每个数字和该数字出现次数分别对应记录*/
    for(int i=0;i<numsSize-1;i++){
        count++;
        if(nums[i]!=nums[i+1]){
            tick[j]=nums[i];
            counts[j]=count;
            count=0;
            j++;
    }
}
/*因为遍历只能遍历到倒数第二位，所以对最后一位需要额外记录*/
    tick[j]=nums[numsSize-1];
    counts[j]=count+1;
    int number=j+1;
 /*修改次数，过2改为2*/
    for(int i=0;i<number;i++){
         if(counts[i]>2)
         counts[i]=2;}
    for(int i=0;i<number;i++){
        sum=sum+counts[i];
    }
 /*重新修改数组，每一次从开头改变，开头每次为末尾*/
    j=0;
    while(j<number){
    for(int i=start;i<(start+counts[j]);i++){
        nums[i]=tick[j];
    }
    start=start+counts[j];
    j++;}
    return sum;}


做题感悟：
1、我的思路是设定两个数组，一个tick来存储具体数字，一个counts来存储出现次数。注意再设定数组后要初始化，否则会溢出。
接下来将出现次数依次判定并修改，最后根据次数重新修改数组。
