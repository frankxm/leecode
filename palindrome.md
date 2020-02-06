判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

示例 1:

输入: 121
输出: true

示例 2:

输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

示例 3:

输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。


bool isPalindrome(int x){
    int number=x;int count=0;
    bool answer;
    while(number!=0){
        count++;
        number=number/10;
    }
    number=x;
    if(x>0){
    int *nums=(int*)malloc(sizeof(int)*(count+1));
    for(int i=count-1;i>=0;i--){
        nums[i]=number%10;
        number=number/10;
    }
    int i=0;int j=count-1;
    while(i!=j&&i<j){
        if(nums[i]==nums[j]){
            i++;
            j--;
        }
        else if(nums[i]!=nums[j])
        break;
    }
    if(i==j||(j+1==i))
    answer=true;
    else 
    answer=false;
    }
    else if(x<0)
    answer=false;
    else if(x==0)
    answer=true;
    return answer;}

做题感悟：
1、这题我的想法是首先确定是几位数，再将各个位赋值给数组。再对数组中进行前后遍历，设置一个前指针和后指针，用while循环完成。
2、再while循环中，如果是回文数，那么指针会一直靠近直至相等或一前一后。如果不是，中途就退出循环，break;

