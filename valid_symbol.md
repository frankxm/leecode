给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

示例 1:

输入: "()"
输出: true

示例 2:

输入: "()[]{}"
输出: true

示例 3:

输入: "(]"
输出: false

示例 4:

输入: "([)]"
输出: false

示例 5:

输入: "{[]}"
输出: true


bool isValid(char * s){
    int tick;bool m;
    int length=strlen(s);
    if(s[0]==' ')
    m=true;
    if(length%2!=0)
    m=false;
    else{
    for(int i=0;i<length;i++){
        if(s[i]==')'){
             tick=i;
            for(int j=tick-1;j>=0;j--){
                if((s[j]=='{')||(s[j]=='[')){
                m=false;break;}
                else if(s[j]=='('){
                s[j]=' ';
                s[tick]=' ';
                break;
            }
        }}
        else if(s[i]==']'){
             tick=i;
            for(int j=tick-1;j>=0;j--){
                if((s[j]=='{')||(s[j]=='(')){
                m=false;break;}
              else  if(s[j]=='['){
                s[j]=' ';
                s[tick]=' ';
                break;
            }
        }}
        else if(s[i]=='}'){
             tick=i;
            for(int j=tick-1;j>=0;j--){
                if((s[j]=='[')||(s[j]=='(')){
                m=false;break;}
            else if(s[j]=='{'){
                s[j]=' ';
                s[tick]=' ';
                break;
            }
        }}
    }}
    for(int j=0;j<length;j++){
        if((s[j]=='(')||(s[j]==')')||(s[j]=='[')||(s[j]==']')||(s[j]=='{')||(s[j]=='}')){
        m=false;
        break;}
        else 
        m=true;}
        return m;}
        
        
        
 做题感悟：
 1、这道题与之前做的不同，例四是不同的。并且这道题相比上次我多加了一个判断奇偶性的条件，这样一开始就可以直接判断
 2、思路就是从右边符号找起，首先从头遍历之后找到一个右括号后再向前遍历如果是它对应的左括号就都赋值为空格
 3、最后的判断就是还有没有符号，有符号就不合格。
