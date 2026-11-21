class Solution {
public:
//Identifiers
vector<vector<int>> ans;
vector<int> temp;
void backtrack(vector<int> &nums, int sum, int target, int start){
    //base case
    if(sum == target){
        ans.push_back(temp);
        return;
    }
    //choice: Iterate all possible elements but in order, if no order needed we could do i = 0, like [2,2,3] and [3,2,2] is considered different
    for(int i = start; i < nums.size(); i++){
        //constraint : if greater than the target, no need to consider the element
        if(sum + nums[i] > target)continue;
        temp.push_back(nums[i]);
        sum += nums[i];
        //explore : Notice how we did i instead i + 1, cause we can use the element any number of times
        backtrack(nums,sum,target,i);
        //backtrack
        sum-= nums[i];
        temp.pop_back();
    }
}
    vector<vector<int>> combinationSum(vector<int>& nums, int target) {
        backtrack(nums, 0, target, 0);
        return ans;
    }
};