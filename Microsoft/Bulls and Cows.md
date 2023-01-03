# Bulls and Cows 

### [Problem Link](https://leetcode.com/problems/bulls-and-cows/)

### Solution
```cpp
class Solution {
public:
    string getHint(string secret, string guess) {
        int n = secret.size();
        unordered_map<char,int> mp;
        int bulls = 0, cows = 0;
        for(int i = 0; i < n; i++){
            // digits in the guess that are in the correct position
            if(secret[i] == guess[i]){
                bulls++;
            }
            else{
                mp[secret[i]]++;
            }
        }
        for(int i = 0; i < n; i++){
            // digits in the guess that are in your secret number but are located in the wrong position 
            if(secret[i] != guess[i] && mp[guess[i]] > 0){
                cows++;
                mp[guess[i]]--;
            }
        }
        string ans = to_string(bulls) + "A" + to_string(cows) + "B";

        return ans;
    }
};
```
