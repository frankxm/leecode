给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:

    初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
    你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

示例:

输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

输出: [1,2,2,3,5,6]


void merge(int* nums1, int nums1Size, int m, int* nums2, int nums2Size, int n){
    int tick;
            tick=m;
            for(int j=0;j<nums2Size;j++){
             nums1[tick++]=nums2[j];   
            }
            for(int i=0;i<nums1Size-1;i++){
                for(int j=i+1;j<nums1Size;j++){
                    if(nums1[i]>nums1[j]){
                        int temp=nums1[i];
                        nums1[i]=nums1[j];
                        nums1[j]=temp;
                    }
                }
            }
        }
        
        
 做题感悟：
 1、本道题的想法就是将数组2放到数组1中，再冒泡排序
 2、因为题中说数组2要全部存储在数组1，所以数组2的n 不用考虑，只用考虑数组1的m 大小从m开始赋值
 
 从头部双指针，直接覆盖A数组
void merge(int* A, int ASize, int m, int* B, int BSize, int n){
    int index_first=0;int index_second=0;int temp=m;
    while(index_first<m&&index_second<n){
        if(A[index_first]>B[index_second]){
        //*A中从tick_first开始的元素集体后移*//
            while(temp!=index_first){
        A[temp]=A[temp-1];
        temp--;
        }
        //*元素后移插入B后临界条件增大*//
        m++;
        temp=m;
        //*B元素 tick_second插到原来tick_first的位置*//
        A[index_first]=B[index_second];
        index_first++;index_second++;}
        else if(A[index_first]<=B[index_second])
            index_first++;
    }
    //*对B中剩余的元素进行插入*//
    if(index_first==m){
        while(index_second!=n){
            A[index_first++]=B[index_second++];
        }
    }}
    
   因为题目说两个数组是排好序的，所以在插入B可以根据顺序插入，这样就避免了再排序导致效率变低。两个数组从头开始对两个指针所在的位置进行比较，如果A数组的值比B的大，那么A中的元素就要集体后移，B再插入至A。在插入后注意总的m 就变化了，index_first的临界条件就变了。
   
   尾部指针原地修改，两指针实时比较，大的放在当前空位中
   void merge(int* A, int ASize, int m, int* B, int BSize, int n){
int i=m-1;int j=n-1;int k=m+n-1;
while(i>=0&&j>=0){
    if(A[i]<B[j])
    A[k--]=B[j--];
    else if(A[i]>=B[j])
    A[k--]=A[i--];}
    while(j>=0)
    A[k--]=B[j--];
}

1、因为已知一共要组成m+n大小的数组，所以一开始设定一个最后数组的末端指针K，A的末端指针I，B的末端指针J。从AB最后的元素开始比较，如果B中的元素比A大，那么B自然就放在最后面。因为两者都是排序数组，两者依次从最大来比较就可以构成一个由大到小的数组。如果B中的元素小于或等于A，说明B中元素应该在其左方，A中元素应该后移，因为两者都是从大到小开始来比较的，所以A中的元素直接就给新的数组。
2、第一个while循环设定的目的就是要把A中大于B的数往后移，跳出while后如果还能进去第二个循环，说明第一个while 循环里，所有大于当前B[j]的A都已经向后处理了，而此时还剩未处理B（不代表未处理的B就一定是A中最小的值）。相反，如果跳出第一个while之后不能进入第二个，说明在前面处理完了B。
