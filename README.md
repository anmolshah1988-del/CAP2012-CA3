# CAP2012-CA3

Q1 TWO SUM :
#include <vector>
class Solution
{
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) 
    {
  
        for (int i = 0; i < nums.size(); i++) {
           
            for (int j = i + 1; j < nums.size(); j++) {
               
                if (nums[i] + nums[j] == target) {
                    
                    return {i, j};
                }
            }
        }
      
        return {};
    }
};


Q2 PLUS ONE :
#include <vector>

class Solution {
public:
    std::vector<int> plusOne(std::vector<int>& digits)
    {
        int n = digits.size();
        for (int i = n - 1; i >= 0; i--) 
        {
            if (digits[i] < 9) {
                digits[i] += 1;
                return digits;
            }
    
            digits[i] = 0;
        }
        
        digits.insert(digits.begin(), 1);
        
        return digits;
    }
};

Q3 MOVE ZEROES :
#include <vector>

class Solution
{
public:
    void moveZeroes(std::vector<int>& nums)
    {
        int insertPos = 0;
        
        
        for (int i = 0; i < nums.size(); i++)
        {
            if (nums[i] != 0) {
                nums[insertPos] = nums[i];
                insertPos++; 
            }
        }
        
     
        for (int i = insertPos; i < nums.size(); i++) {
            nums[i] = 0;
        }
    }
};


Q4 Best Time to Buy and Sell Stock :

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX; 
        int maxProfit = 0;      

        for (int i = 0; i < prices.size(); i++) {
           
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            } 
            
            else if (prices[i] - minPrice > maxProfit) {
                maxProfit = prices[i] - minPrice;
            }
        }

        return maxProfit;
    }
};


Q5  Valid Parentheses

class Solution {
public:
    bool isValid(string s) {
        stack<char> st;
        
     
        for (int i = 0; i < s.length(); i++) {
            char c = s[i];
            
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } 
            else {
                
                if (st.empty()) {
                    return false;
                }
                
                char topChar = st.top();
                
              
                if (c == ')' && topChar != '(') {
                    return false;
                }
                if (c == '}' && topChar != '{') {
                    return false;
                }
                if (c == ']' && topChar != '[') {
                    return false;
                }
                
               
                st.pop();
            }
        }
        
       
        if (st.empty()) {
            return true;
        } else {
            return false;
        }
    }
};

Q10 Add Two Numbers
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* head = NULL;
        ListNode* tail = NULL;
        int carry = 0;

        while (l1 != NULL || l2 != NULL || carry != 0) {
            int sum = carry;

            if (l1 != NULL) {
                sum = sum + l1->val;
                l1 = l1->next;
            }

            if (l2 != NULL) {
                sum = sum + l2->val;
                l2 = l2->next;
            }

         
            int digit = sum % 10;
            carry = sum / 10;

          
            ListNode* temp = new ListNode(digit);

           
            if (head == NULL) {
                head = temp;
                tail = temp;
            } 
          
            else {
                tail->next = temp;
                tail = temp;
            }
        }

        return head;
    }
};

Q11 Rotate list 


class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
       
        if (head == nullptr || head->next == nullptr || k == 0) {
            return head;
        }

   
        int length = 1;
        ListNode* tail = head;
        while (tail->next != nullptr) {
            tail = tail->next;
            length++;
        }

              k = k % length;
        if (k == 0) {
            return head; 
        }

        
        tail->next = head;

        
        int stepsToNewTail = length - k;
        ListNode* newTail = head;
        for (int i = 1; i < stepsToNewTail; i++) {
            newTail = newTail->next;
        }

    
        ListNode* newHead = newTail->next;
        newTail->next = nullptr;

        return newHead;
    }
};

Q6 Reverse Linked list 

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr; 
        ListNode* curr = head;    
        while (curr != nullptr) {
           
            ListNode* nextNode = curr->next;
            
          
            curr->next = prev;
            
            
            prev = curr;
            curr = nextNode;
        }
        
        
        return prev;
    }
};
