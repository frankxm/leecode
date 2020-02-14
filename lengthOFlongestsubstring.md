给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。

示例 1:

输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。


int lengthOfLongestSubstring(char * s){
    int length=strlen(s);
    int i=0;int index_first=0;int count=0;int tick=0;
    int max_length=0;
    if(!length)
    return NULL;
    if(length==1)
    return 1;
    for(int i=1;i<length;i++){
        if(s[i]==s[0])
        count++;
    }
    if(count==length-1)
    return 1;
    int windows_length=1;
    while(1){
    for(i=tick;i<tick+windows_length;i++){
        if(s[i]==s[tick+windows_length]){
        index_first++;
        tick=index_first;
        windows_length=1;
        break;}
    }
    if(i==(windows_length+tick)){
        windows_length++;
        if(windows_length>max_length)
        max_length=windows_length;
    }
    if(tick+windows_length==length)
    break;
    else if(tick==(length-1))
    break; 
    }
    return max_length;}

做题感悟：
1、我用的是直接暴力法，就是假设一个窗口框住其中的元素，窗口长度要已知。每一次就遍历窗口中的元素，如果窗口后一个元素与其中某元素相同，则窗口的开头后移，长度变为1；若窗口元素没有与其相同，则窗口长度增加。
2、就算最大长度的方法就是，当窗口后面一位与窗口其中元素不同时说明算上后面窗口长度符合要求，所以此时就要比较。
3、当窗口刚好框到该数组尾部时结束while。当窗口开头到数组尾部时，因为默认窗口长度为一，所以此时需要结束while。
