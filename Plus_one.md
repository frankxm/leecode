给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

示例 1:

输入: [1,2,3]
输出: [1,2,4]
解释: 输入数组表示数字 123。

示例 2:

输入: [4,3,2,1]
输出: [4,3,2,2]
解释: 输入数组表示数字 4321。



/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize){
    int i=0;int j=0;*returnSize=digitsSize;
    /*从最低位开始遍历数字，将原数组修改
        for( i=(digitsSize-1);i>=0;i--){
        if(digits[i]<9){
            digits[i]++;
            break;
        }
        digits[i]=0;}
        */
        /*当数组全为9时，第一个数在前面的修改过程中会变为0
        if(digits[0]==0){
                int *answer=(int*)malloc(sizeof(int)*(digitsSize+1));
                answer[0]=1;
                for(int i=1;i<(digitsSize+1);i++){
                    answer[i]=0;
                }
                *returnSize=(digitsSize+1);
                return answer;
                */
            }
            else 
        return digits;}
        
        
        
  做题感悟：
  1、这道题出现的情况较多，我总结分为三种：
  一 、当遍历到的数字小于9时，那么直接加1即可  二、当遍历的数字等于9时，则进1此数字变为0  三、当遍历的数字都为9时，需要用新的数组来存储
  2、难点在于如何把条件分类，一开始我一直执着于如何描述全部为9，发现这么描述的话很多情况会重叠，于是想到：正常情况下数字就仅加1，当为9时就为0，首先数字就只有这两种情况，只有当遍历到开头时才会出现分类的情况
  当遍历到开头时，如果是9，那么将会赋值为0，如果小于9，那么就加一。这样一次遍历就将数组更改了
  3、之后按照题目要求设置一个新数组answer来存储答案，当全为9的情况时，那么第一个数字就变为0了，这时候就可以进行分类来赋值了
  4、这道题我第一次尝试用多个return的方法，以前都是改变某个值最后统一 return
