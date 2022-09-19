    /**
     * Definition for singly-linked list.
     * struct ListNode {
     *     int val;
     *     ListNode *next;
     *     ListNode() : val(0), next(nullptr) {}
     *     ListNode(int x) : val(x), next(nullptr) {}
     *     ListNode(int x, ListNode *next) : val(x), next(next) {}
     * };
     */
    class Solution {
    public:
        ListNode* reverse(ListNode* a,ListNode* b){
            ListNode* cur = a;
            ListNode* nxt = nullptr;
            ListNode* pre = nullptr;
            while(cur != b){
                nxt = cur->next;
                cur->next = pre;
                pre = cur;
                cur = nxt;
            }
            return pre;
        }
        ListNode* reverseKGroup(ListNode* head, int k) {
            int cnt = k;
            ListNode* a;
            ListNode* b;
            a = head;
            b = head;

            while(cnt--){
                if(b == nullptr) return a; 
                b = b->next;
            }
            ListNode* new_head = reverse(a,b);
            a->next = reverseKGroup(b,k);

            return new_head;
        }
    };
