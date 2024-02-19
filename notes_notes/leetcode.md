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
### Given a string path, which is an absolute path (starting with a slash '/') to a file or directory in a Unix-style file system, convert it to the simplified canonical path. In a Unix-style file system, a period '.' refers to the current directory, a double period '..' refers to the directory up a level, and any multiple consecutive slashes (i.e. '//') are treated as a single slash '/'. For this problem, any other format of periods such as '...' are treated as file/directory names. The canonical path should have the following format:

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
