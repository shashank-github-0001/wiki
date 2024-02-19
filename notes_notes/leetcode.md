## Tree:
### 94. Binary Tree Inorder Traversal
* Solved
* Easy

### Given the root of a binary tree, return the inorder traversal of its nodes' values
``` cpp
#include <algorithm>
#include <vector>
using namespace std;

struct TreeNode {
	int val;
	TreeNode *left;
	TreeNode *right;
	TreeNode() : val(0), left(nullptr), right(nullptr) {}
	TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
	TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

class Solution {
	public:
    	vector<int> inorderTraversal(TreeNode* root) {
        	vector<int> result;
        	helperFunction(root, result);
        	reverse(result.begin(), result.end());
        	return result;
    	}
	private:
    	void helperFunction(TreeNode* root, vector<int>& result){
        	if(root!=nullptr){
            	helperFunction(root->right, result);
            	result.push_back(root->val);
            	helperFunction(root->left, result);
        	}
    	}
};
```

## stack:
### 71. Simplify Path
* Solved
* Medium
 
Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path. In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names. The canonical path should have the following format:

* The path starts with a single slash '/'.
* Any two directories are separated by a single slash '/'.
* The path does not end with a trailing '/'.
* The path only contains the directories on the path from the root directory to the target file or directory (i.e., no period '.' or double period '..')
### Return the simplified canonical path.

```cpp
class Solution {
    public:
        string simplifyPath(string path) {
            vector<string> dirs;
            stringstream ss(path);
            stringstream ans;
            stack<string> fullpath;
            string dir;
            while (getline(ss, dir, '/')) {
                dirs.push_back(dir);
            }
            for (const auto word : dirs) {
                if(word == "") continue;
                if(word == ".") continue;
                if(word == "..") {
                    if(fullpath.empty()) continue;
                    else fullpath.pop();
                }
                else fullpath.push(word);
            }
            dirs.clear();
            if(fullpath.empty()) return "/";
            while (!fullpath.empty()) {
                dirs.push_back(fullpath.top());
                fullpath.pop();
            }
            reverse(dirs.begin(), dirs.end());
            for (const auto word : dirs) {
                ans << "/" << word;
            }
            return ans.str();
        }
};
```
### 20. Valid Parentheses
* Solved
* Easy
  
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
An input string is valid if:

* Open brackets must be closed by the same type of brackets.
* Open brackets must be closed in the correct order.
* Every close bracket has a corresponding open bracket of the same type
```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;



class Solution {
    public:
        bool isValid(string s) {
            stack<char> params;
            for(const auto chars : s ){
                switch(chars){
                    case '(': params.push(chars);
                              break;
                    case ')': if(!params.empty() && params.top()=='(') params.pop();
                              else return false;
                              break;
                    case '[': params.push(chars);
                              break;
                    case ']': if(!params.empty() && params.top()=='[') params.pop();
                              else return false;
                              break;
                    case '{': params.push(chars);
                              break;
                    case '}': if(!params.empty() && params.top()=='{') params.pop();
                              else return false;
                              break;
                }
            }
            if(params.empty()) return true;
            else return false;
        }
};
```

## Linked List:
### 19. Remove Nth Node From End of List
* Solved
* Medium

Given the head of a linked list, remove the nth node from the end of the list and return its head.

```cpp
#include <bits/stdc++.h>


struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};

class Solution {
    public:
        ListNode* removeNthFromEnd(ListNode* head, int n) {
            ListNode* cur = head;
            ListNode* temp = nullptr;
            int length_of_node = length(head);
            if(length_of_node==1) return nullptr;
            if(length_of_node==n) return head->next;
            int count = 0;
            while (count!=length_of_node-n-1) {
                count++;
                cur = cur->next;
            }
            temp = cur->next;
            cur->next = cur->next->next;
            return head;
        }
    private:
        int length(ListNode* head) {
            int count = 0;
            while(head!=nullptr){
                count++;
                head = head->next;
            }
            return count;
        }
};
```

## Queue:
### 225. Implement Stack using Queues
* Solved
* Easy

Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).
Implement the MyStack class:

* void push(int x) Pushes element x to the top of the stack.
* int pop() Removes the element on the top of the stack and returns it.
* int top() Returns the element on the top of the stack.
* boolean empty() Returns true if the stack is empty, false otherwise

```cpp
#include <bits/stdc++.h>
#include <queue>
using namespace std;

class MyStack {
    public:
        queue<int> main_q, temp_q;
        MyStack() = default;
        void push(int x) {
            if(main_q.empty()){
                main_q.push(x);
            } else {
                temp_q.push(x);
                while(!main_q.empty()){
                    temp_q.push(main_q.front());
                    main_q.pop();
                }
            }
            while(!temp_q.empty()) {
                main_q.push(temp_q.front());
                temp_q.pop();
            }
        }
        int pop() {
            int val = main_q.front();
            main_q.pop();
            return val;
        }
        int top() {
            return main_q.front();
        }
        bool empty() {
            return main_q.empty();
        }
};
```
