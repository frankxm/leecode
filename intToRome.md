罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。

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

给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。

示例 1:

输入: 3
输出: "III"

示例 2:

输入: 4
输出: "IV"

示例 3:

输入: 9
输出: "IX"

示例 4:

输入: 58
输出: "LVIII"
解释: L = 50, V = 5, III = 3.

示例 5:

输入: 1994
输出: "MCMXCIV"
解释: M = 1000, CM = 900, XC = 90, IV = 4.



char * intToRoman(int num){
    char *answer=(char*)malloc(sizeof(char)*16);
    for(int j=0;j<16;j++)
    answer[j]=0;
    int tick=num;int times=0;int s=0;int i=0;
    if(tick>=1000){
        times=tick/1000; i=0;
        while(i<times){
            answer[i++]='M';
        }
        s=i;
        tick=tick-1000*times;
    }
    if(tick>=100&&tick<1000){
        times=tick/100;
        if(times>4&&times<9){
            answer[s]='D';
            for( i=s+1;i<(s+1+(times-5));i++){
                answer[i]='C';
            }s=i+1;
        }
        else if(times<4){
            for( i=s;i<(s+times);i++){
                answer[i]='C';
            }s=i+1;
        }
        else if(times==4){
            answer[s]='C';answer[s+1]='D';
            s=s+2;
        }
        else if(times==9){
            answer[s]='C';answer[s+1]='M';
            s=s+2;
        }
        tick=tick-100*times;
    }
    if(tick>=10&&tick<100){
        times=tick/10;
        if(times>4&&times<9){
            answer[s]='L';
            for( i=s+1;i<(s+1+(times-5));i++){
                answer[i]='X';
            }s=i+1;
        }
        else if(times<4){
            for( i=s;i<(s+times);i++){
                answer[i]='X';
            }s=i+1;
        }
        else if(times==4){
            answer[s]='X';answer[s+1]='L';
            s=s+2;
        }
        else if(times==9){
            answer[s]='X';answer[s+1]='C';
            s=s+2;
        }
        tick=tick-10*times;
    }
    if(tick<10&&tick>0){
        times=tick;
        if(times>4&&times<9){
            answer[s]='V';
            for( i=s+1;i<(s+1+(times-5));i++){
                answer[i]='I';
            }
        }
        else if(times<4){
            for( i=s;i<(s+times);i++){
                answer[i]='I';
            }
        }
        else if(times==4){
            answer[s]='I';answer[s+1]='V';
        }
        else if(times==9){
            answer[s]='I';answer[s+1]='X';
        }
    }
    return answer;}
