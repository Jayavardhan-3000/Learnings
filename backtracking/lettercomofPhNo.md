
class Solution {
public:
    vector<string> ans;
    string temp;

    string mapping[10] = {
        "", "", "abc", "def", "ghi",
        "jkl", "mno", "pqrs", "tuv", "wxyz"
    };

    void backtrack(string &digits, int index) {

        // Base case
        if(index == digits.size()) {
            ans.push_back(temp);
            return;
        }

        // Choices
        string letters = mapping[digits[index] - '0'];

        for(int i = 0; i < letters.size(); i++) {

            // Choose
            temp.push_back(letters[i]);

            // Explore next digit
            backtrack(digits, index + 1);

            // Backtrack
            temp.pop_back();
        }
    }

    vector<string> letterCombinations(string digits) {

        if(digits.empty()) return ans;

        backtrack(digits, 0);

        return ans;
    }
};
//Didn't had the time to do it, it's pass 12 am but did revised though
