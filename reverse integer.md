给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

示例 1:

输入: 123
输出: 321

 示例 2:

输入: -123
输出: -321

示例 3:

输入: 120
输出: 21

注意:

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。


int reverse(int x){
        int reverse_a=0;int reverse_b=0;int reverse_c=0;
        long max=2147483647;long min=-2147483648;
        /*分类处理正负数，若为负数则转为正数处理*/
        if(x<0&&x>=-max){
        /*因为翻转过程将负数转为了正数，而如果输入了min,转为正数后就溢出了，所以保证输入*/
            x=0-x;
            /*翻转操作*/
        while(x>=1){
            reverse_b=x%10;
            reverse_c=reverse_a*10;
            /*翻转过程reverse_a*10会溢出*/
            if(reverse_a>max/10||reverse_a<min/10){
                reverse_a=0;
                break;
            }
            reverse_a=reverse_a*10+reverse_b;
            x=x/10;}
            reverse_a=0-reverse_a;
            /*判断翻转后的数是否溢出*/
        if(reverse_a<min||reverse_a>max){
            reverse_a=0;}
                }
        else if(x>=0){
        while(x>=1){
            reverse_b=x%10;
            if(reverse_a>max/10||reverse_a<min/10){
                 reverse_a=0;
                break;
            }
            reverse_a=reverse_a*10+reverse_b;
            x=x/10;}
        if(reverse_a<min||reverse_a>max){
            reverse_a=0;}}
                return reverse_a;}
                
    做题感悟：
    1、此题得出一种翻转整数的方法，将整数每个位数分开记录最后再分别相加回去。其中核心的翻转代码为 while(x>=1){ reverse_b=x%10;reverse_a=reverse_a*10+reverse_b;x/10;}
    每个位数合在一起的方法就算各位乘10再相加。
    2、此题有一个重要条件即为“溢出”。一种溢出为输入时未溢出但全部翻转后溢出，一种为翻转时因为翻转过程会溢出，即无法继续。
    3、处理正负数的方式可以放在一起，最后再转为正数
