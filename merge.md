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
