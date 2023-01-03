# Combination Sum III

### [Problem Link](https://leetcode.com/problems/combination-sum-iii/)

### Solution
```cpp
class Solution {
public:
    void helper(int idx, int sum, int n, vector<int>& combination, vector<vector<int>>& ans, int k){
        if(sum == n && k == 0){
            ans.push_back(combination);
            return;
        }
        if(sum > n){
            return;
        }
        for(int i = idx; i <= 9; i++){
            if(i > n){
                break;
            }
            combination.push_back(i);
            helper(i+1,sum+i,n,combination,ans,k-1);
            combination.pop_back();                       //backtrack          
        }
    }
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> combination;
        vector<vector<int>> ans;
        helper(1,0,n,combination,ans,k);

        return ans;
    }
};
```
