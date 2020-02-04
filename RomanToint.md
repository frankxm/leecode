罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。

字符          数值
I             1
V             5
X             10
L             50
C             100
D             500
M             1000

例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

    I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
    X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
    C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。

给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。

示例 1:

输入: "III"
输出: 3

示例 2:

输入: "IV"
输出: 4

示例 3:

输入: "IX"
输出: 9

示例 4:

输入: "LVIII"
输出: 58
解释: L = 50, V= 5, III = 3.

示例 5:

输入: "MCMXCIV"
输出: 1994
解释: M = 1000, CM = 900, XC = 90, IV = 4.

int romanToInt(char * s){
    int length=strlen(s);int number=0;
    int answer=0;int pre_number=0;
    /*进行循环计算，每遇到一次字符就赋值，赋完值后就参与计算*/
    while(*s){
         switch(*s){
        case 'I':number=1;break;
        case 'V':number=5;break;
        case 'X':number=10;break;
        case 'L':number=50;break;
        case 'C':number=100;break;
        case 'D':number=500;break;
        case 'M':number=1000;break;
    }
        if(number>pre_number){
            answer=(number+answer-2*pre_number);
        }
        else if(number<pre_number){
            answer=answer+number;
        }
        else if(number=pre_number){
            answer=answer+number;
        }
        pre_number=number;
        /*每次增加的是地址，每次扫描判定的是值*/
        s++;
        }
    return answer;
}



做题感悟：
1、这题因为情况较多，所以我用了switch case  使用switch时需要注意switch()中要是常量，里面不能写s，因为s是个地址，这样的话如果遇到情况无法赋值。*s就是具体的数值，如果是罗马数字中的某一个，就把值赋给number
2、因为用的是switch 所以我用常量参与每次计算。每一次的number参与answer的计算，如果本次number小于之前的pre，那么为正常情况，answer直接与number相加。如果本次number大于pre，那么为特殊情况
我用 answer=(number+answer-2*pre_number)来表示
3、while（*s）指的是当在该字符串范围内来计算，s++指的是每完成一次循环就往下推进，*s就直接指下一个
