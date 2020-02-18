给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

示例 1:

输入: "A man, a plan, a canal: Panama"
输出: true

示例 2:

输入: "race a car"
输出: false



bool isPalindrome(char * s){

    int str_len = strlen(s);
    char *new_s = (char *)malloc( sizeof(char) * str_len);
    int j = 0;

    for (int i =0 ; i < str_len; i++){
        if ( s[i] >= 'A' && s[i] <= 'Z'){
        /*这里可以用 tolower或者toupper函数转换大小写*/
            s[i]=s[i]+32;
            new_s[j++] = s[i];
        } else if ( s[i] >= 'a' && s[i] <= 'z'){
            new_s[j++] = s[i];
        } else if (s[i] >= '0' && s[i] <= '9'){
            new_s[j++] = s[i];
        } else{
            continue;
        }
    }
    
    for ( int i = 0; i < (j/2); i ++){
        if (new_s[i] != new_s[j-i-1]){
            return false;
        }
    }
    return true;
}

做题感悟：
1、因为该字符串要考虑数字和字母，其余字符都不考虑，所以可以把其余字符先去掉。于是我想到重新设定一个数组，把字母数字都存储进去，当有大小写时直接转换。
2、然后进入for循环判断，当出现不相同的状况立马返回。借鉴了他人简洁的判断方式，new_s[i] != new_s[j-i-1]
j代表元素个数，i为前面元素标号，如果是对称的位置，标号相加为元素总数减一
