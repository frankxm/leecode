反转一个单链表。

示例:

输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL

进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？



/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

迭代：
struct ListNode* reverseList(struct ListNode* head){
    struct ListNode *current=head;
    struct ListNode *pre=NULL;
    while(current!=NULL){
        struct ListNode *temp=current->next;
        current->next=pre;
        pre=current;
        current=temp;
    }
    return pre;
}

参考了题目的提示，我的思路就是:
1、首先设定一个current指针，把current.next,也就是指向下一个的节点的指针改变，把current.next指向前面一个数，这样在当前指针之后就应该指向前面的值。之后当前指针往后移，通过把后面指针的给当前实现current=temp
2、不过需要额外注意的是原来的链表尾部有NULL，所以反向链表尾部也要有NULL，也就是头部要指向NULL。所以我又额外加了个head指针来补齐base case.当current在最开始时前，即指向1之前应该是指向NULL。这样以来每次current和pre都后移，在这个过程中就把开头指针current放到了最初的NULL，pre放在其前面。
所以最终新链表的头部就是原链表的尾部，返回pre

递归
首递归：（就是把迭代放在函数里）
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *reverse(struct ListNode*pre,struct ListNode*current){
    if(current!=NULL){
        struct ListNode *temp=current->next;
        current->next=pre;
        pre=current;
        current=temp;
    return reverse(pre,current);}
    else 
    return pre;}
struct ListNode* reverseList(struct ListNode* head){
    struct ListNode *current=head;struct ListNode *pre=NULL;
    return reverse(pre,current);
}

尾递归：
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode*reverse(struct ListNode*current){
//*输入可能为空的情况，或者是已经到尾节点，需要终止*//
    if((current->next==NULL)||(current==NULL))
    return current;
    //从开始一直往后找节点直至终止条件*//
    struct ListNode *returnnums=reverse(current->next);
    //*当前的指针为current，当前指针的下一个指针为它右边，要使它右边的指针的下一个指向左边*//
    current->next->next=current;
    //*既保证最前面是NULL ，又保证链表不会一直循环*//
    current->next=NULL;
    return returnnums;
}
struct ListNode* reverseList(struct ListNode* head){
//*当输入为空时，返回空*//
    if(head==NULL)
    return head;
    struct ListNode*current=head;
    return reverse(current);
}

尾递归感悟：
1、先从头往后走，每一次进入函数就调用下一次函数，直到遇到终止条件。遇到终止条件后得出尾部节点的值，则返回上一次函数过程。前面每次遇到 struct ListNode *returnnums=reverse(current->next);程序就会进入下一个函数过程，所以当最后的值得到后就返回i上一次函数过程，进行上一次函数内剩余的过程
2、回到前一次函数，假设之后的已经把顺序调换，那现在就需要把当前current右边的指针的下一次指向它左边，也就是自己。  current->next->next=current;
3、不过我们修改的只是当前current下下个值的下一个顺序，当前current的下一个值依旧指向右边，如果这样的话在返回了此次函数的值后下一次依旧是重复之前的操作，所以就需要改变下一次指向的值。因为最终到头时current左边，也就是下一个指向的值是NULL。
所以修改为null.在第二次操作后再修改下一次为NULL不会影响整个过程，因为下一次返回时current就往前推了，它需要的只是它右边指向的值。
