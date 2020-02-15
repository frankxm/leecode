void sortColors(int* nums, int numsSize){
 给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

示例:

输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]

进阶：

    一个直观的解决方案是使用计数排序的两趟扫描算法。
    首先，迭代计算出0、1 和 2 元素的个数，然后按照0、1、2的排序，重写当前数组。
    你能想出一个仅使用常数空间的一趟扫描算法吗？


void sortColors(int* nums, int numsSize){
    int index_first=0;int index_second=numsSize-1;
    int current=0;
    while(current<=index_second){
        if(nums[current]==1){
            current++;
        }
        else if(nums[current]==0){
            int temp=nums[current];
            nums[current]=nums[index_first];
            nums[index_first]=temp;
            index_first++;
            current++;
        }
        else if(nums[current]==2){
            int temp=nums[current];
            nums[current]=nums[index_second];
            nums[index_second]=temp;
            index_second--;
        }

    }
}


void sortColors(int* nums, int numsSize){
    int count[3]={0};
    for(int i=0;i<numsSize;i++){
        if(nums[i]==0)
        count[0]++;
        else if(nums[i]==1)
        count[1]++;
        else if(nums[i]==2)
        count[2]++;
    }
    for(int i=0;i<count[0];i++)
    nums[i]=0;
    for(int i=count[0];i<count[0]+count[1];i++)
    nums[i]=1;
    for(int i=count[0]+count[1];i<count[0]+count[1]+count[2];i++)
    nums[i]=2;
}



做题感悟：
1、法二为一般的方法，进行了两次遍历，一次来计算各数字出现的个数，第二次来修改数组，不需要交换。
2、法一为题中要求的仅用常数空间的一次遍历法。荷兰国旗问题：
用三个指针一次完成遍历，index_first记录左边，index_second记录右边，current记录当前。只分析0和2，当current为0时，要放到左边去。当current为2时，要放到右边去。当current为1时不变
应该注意的是每一次交换后可能出现换了0或2回来，这就需要在换了之后还要再当前位置判断。而只有当值为0时才可以current++，因为左边一定时排好序了或为1，不然current是无法移动的，所以换回来的一定不会是2
