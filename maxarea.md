给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器，且 n 的值至少为 2。

图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

示例:

输入: [1,8,6,2,5,4,8,3,7]
输出: 49

int maxArea(int* height, int heightSize){
    int high=0;int diff=0;int maxarea=0;int compare=0;
    for(int i=0;i<heightSize-1;i++){
        for(int j=i+1;j<heightSize;j++){
            high=(height[i]<height[j])?height[i]:height[j];
            diff=j-i;
            compare=diff*high;
            maxarea=(compare>maxarea)?compare:maxarea;
           }
        }
return maxarea;}


做题感悟：
1、此题的主要思想是通过遍历各元素，分别求各元素的值来比较
2、难点在于如何比较得出最大值，我一开始想要用一个数组来储存求得的值，后发现不方便。于是想到用中间值的方法，将每次遍历获得的值与中间值比较，如果比中间值大
就将该值赋给中间值，这样只有更大的值才能出来
3、本题我用来三元运算符，即条件运算符（？：）
