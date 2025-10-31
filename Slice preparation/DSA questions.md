* https://leetcode.com/problems/lru-cache/description/

```cpp
class LRUCache {
private:
    int capacity;
    list<pair<int,int>> dll;
    map<int,list<pair<int,int>>::iterator> keyToIterator;
public:
    LRUCache(int capacity) {
        this->capacity = capacity;
    }
    
    int get(int key) {
        if(keyToIterator.find(key) == keyToIterator.end()){
            return -1;
        }
        else{
            int value = keyToIterator[key]->second;
            put(key,value);
            return value;
        }
    }
    
    void put(int key, int value) {
        auto it = keyToIterator.find(key);
        if(it != keyToIterator.end()){
            dll.erase(keyToIterator[key]);
        }
        else{
            if(dll.size() == capacity){
                // need to evict lru
                int lruKey = dll.begin()->first;
                keyToIterator.erase(lruKey);
                dll.pop_front();
            }
        }
        dll.push_back({key,value});
        keyToIterator[key] = prev(dll.end());
    }
};
```


* https://leetcode.com/problems/merge-k-sorted-lists/description/
``` cpp
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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        priority_queue<ListNode*,vector<ListNode*>,compare> minHeap;
        for(auto list: lists){
            if(list!=NULL){
                minHeap.push(list);
            }
        }

        ListNode* preHead = new ListNode();
        ListNode* curr = preHead;
        
        while(!minHeap.empty()){
            ListNode* node = minHeap.top();
            minHeap.pop();

            curr->next = node;
            curr = curr->next;

            if(node->next){
                minHeap.push(node->next);
            }
        }

        return preHead->next;
    }
private:
    struct compare{
        bool operator()(ListNode* l1, ListNode* l2){
            return l1->val > l2->val;
        }
    };
};
```

* https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        const int n = nums.size();
        int low=0,high=n-1;
        while(low<high){
            int mid = (low+high)/2;
            if(nums[mid]<nums[high]){
                // mid is in second half
                // l-----pivot---mid----------------r
                high = mid;
            }
            else{
                // mid is in first half
                // l------------mid----pivot--------r
                low = mid+1;
            }
        }
        
        return nums[high]; // could be nums[low] also
    }
};
```

* [C. Balanced Team](https://codeforces.com/problemset/problem/1133/C)
```cpp

```

* [Minimum no. of iterations to pass information to all nodes in the tree](https://www.geeksforgeeks.org/dsa/minimum-iterations-pass-information-nodes-tree/)
```cpp

```

* [73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/description/)
```cpp
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        bool firstRowAllZero = false, firstColAllZero = false;
        int n = matrix.size(), m = matrix[0].size();
        
        for(int j=0;j<m;j++){
            if(matrix[0][j] == 0){
                firstRowAllZero = true;
                break;
            }
        }
        
        for(int i=0;i<n;i++){
            if(matrix[i][0] == 0){
                firstColAllZero = true;
                break;
            }
        }
        
        for(int i=1;i<n;i++){
            for(int j=1;j<m;j++){
                if(matrix[i][j] == 0){
                    matrix[i][0] = matrix[0][j] = 0;
                }
            }
        }
        
        for(int i=1;i<n;i++){
            if(matrix[i][0]==0){
                for(int j=1;j<m;j++)
                    matrix[i][j] = 0;
            }
        }
        
        for(int j=1;j<m;j++)
            if(matrix[0][j]==0){
                for(int i=1;i<n;i++){
                    matrix[i][j] = 0;
            }
        }
        
        if(firstRowAllZero)
            for(int j=0;j<m;j++)
                matrix[0][j] = 0;
        
        if(firstColAllZero)
            for(int i=0;i<n;i++)
                matrix[i][0] = 0;
    }
};
```


* [41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/description/)
```cpp
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        // Getting rid of -ve numbers
        for(int &num: nums){
            if(num<0){
                num = 0;
            }
        }

        int n = nums.size();
        for(int i=0;i<n;i++){
            int index = abs(nums[i]);
            if(index>0 && index<=n){
                if(nums[index-1]>0){
                    nums[index-1] *= (-1);
                }
                else if(nums[index-1]==0){
                    // Since multiplying 0 with -ve, doesn't convert it into -ve.
                    // So we need some workaround to make it negative.
                    // So converting it to -1e9 so that it becomes -ve.
                    nums[index-1] = -1e9;
                }
            }
        }

        for(int i=0;i<n;i++){
            if(!(nums[i]<0)){
                return i+1;
            }
        }

        return n+1;
    }
};
```


* [224. Basic Calculator](https://leetcode.com/problems/basic-calculator/description/)
```cpp
class Solution {
public:
    int calculate(string s){
        int n = s.length(),sum=0,sign=1;
        stack<int> stk;
        for(int i=0;i<n;i++){
            if(isdigit(s[i]) ){
                int val = 0;
                while(i<n && isdigit(s[i])){
                    val *= 10;
                    val += s[i++]-'0';
                }
                i--;
                sum += val*sign;
                val = 0;
                sign = 1;
            }
            else if(s[i]=='-') sign = -1;
            else if(s[i]=='+') sign = 1;
            else if(s[i]=='('){
                stk.push(sum);
                stk.push(sign);
                sum = 0;
                sign = 1;
            }
            else if(s[i]==')'){
                sum *= stk.top(); stk.pop();
                sum += stk.top(); stk.pop();
            }
        }
        
        return sum;
    }
};
```


* [227. Basic Calculator II](https://leetcode.com/problems/basic-calculator-ii/description/)
```cpp

```


