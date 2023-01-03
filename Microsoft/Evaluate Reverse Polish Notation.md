# Evaluate Reverse Polish Notation 

### [Problem Link](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

### Solution
```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> st;
        for(auto s : tokens){
            if(s == "+" || s == "-" || s == "*" || s == "/"){      // operators 
                int op2 = st.top();
                st.pop();
                int op1 = st.top();
                st.pop();

                if(s == "+") st.push(op1 + op2);
                if(s == "-") st.push(op1 - op2);
                if(s == "*") st.push(op1 * op2);
                if(s == "/") st.push(op1 / op2);
            }
            else{
                st.push(stoi(s));          // number -> need to convert from str to int
            }
        }
        return st.top();
    }
};

/* Postfix Expression Evaluation */
```
