[Coin Change (LeetCode)](https://leetcode.com/problems/coin-change/description/)

## Here, we will discuss and explain solutions of Coin Change problem:  


### Problem Statement:
> You are given an integer array representing coins of different denominations and an integer representing a total amount of money.  
You are required to return the fewest number of coins that you need to make up that total amount. And if there is no combination of coins that make up that total amount, return -1  


During the session, there were 3 suggested solution by 3 different people, and we didn't show which of the solutions would work and what wouldn't, so let's do it now.


### Solution 1 (Wrong Answer):

```C++ 
class Solution {
public:

    vector<int> memo;

    int dp(int val, vector<int>& coins){
        if(not val){
            return 0;
        }
        int& ret = memo[val];
        if(~ret){
            return ret;
        }
        ret = int(1e7);

        for(auto& coin : coins){
            ret = min(ret, val / coin + dp(val % coin, coins));
        }
        return ret;
    }

    int coinChange(vector<int>& coins, int amount) {
        memo.assign(amount + 5, -1);
        int ans = dp(amount, coins);
        if(ans > amount)
            ans = -1;
        return ans;
    }
};
```

This solution is wrong becuase the idea of taking modulo means that each time we decide to pick a coin with some value, we're taking as many coins as we can, and then calling the function with the remainder after these operations.  

For example: if we currently have the total amount equals to 5, and we decide to choose a coin with value 2, we have to take 2 coins and make a call with the remainder which equals to 1 (while this may not be the optimal answer and we need to take only one coin with value 2)


### Solution 2 (Time Limit Exceeded):

```C++ 

class Solution {
public:

    vector<int> memo;

    int dp(int val, vector<int>& coins){
        if(not val){
            return not val ? 0 : int(1e7);
        }
        int& ret = memo[val];
        if(~ret){
            return ret;
        }
        ret = int(1e7);

        for(int idx = 0; idx < coins.size(); idx++){
            for(int i = 1; ; i++){
                if(i * coins[idx] > val)
                    break;
                ret = min(ret, i + dp(val - coins[idx] * i, coins));
            }
        }
        return ret;
    }

    int coinChange(vector<int>& coins, int amount) {
        memo.assign(amount + 5, -1);
        int ans = dp(amount, coins);
        if(ans > amount)
            ans = -1;
        return ans;
    }
};

```

This solution gives us a correct answer, but exceeds the time limit for the problem because of the internal loop which checks for the number of coins we need to pick with this value. After many such calls with big values of Total Amound and small values of Coins, this will exceed the limit and our solution will not pass.


### Solution 3 (Accepted):

```C++

class Solution {
public:

    vector<vector<int>> memo;

    int dp(int idx, int value, vector<int>& coins){
        if(value <= 0 or idx >= coins.size()){
            return not value ? 0 : int(1e7);
        }

        int& ret = memo[idx][value];
        if(~ret){
            return ret;
        }
        ret = int(1e7);

        ret = dp(idx + 1, value, coins);
        ret = min(ret, 1 + dp(idx + 1, value - coins[idx], coins));
        ret = min(ret, 1 + dp(idx, value - coins[idx], coins));

        return ret;
    }

    int coinChange(vector<int>& coins, int amount) {
        memo.assign(coins.size(), vector<int>(amount + 5, -1));
        int ans = dp(0, amount, coins);
        if(ans > amount)
            ans = -1;
        return ans;
    }
};

```

This solution is correct and doesn't exceed the time limit. Here, we are trying 3 different possibilities for each coin:

1. We can leave the coins having the current values and move to the next coin without changing our value (excluding coin[idx] from the solution)

2. We can pick one of the coins having the current value only this time, change total value to **value - coins[idx]**, and then proceed to the next value of coins

3. We can pick one of the coins having the current value, change the total value to **value - coins[idx]**, and then try to pick another coin with same value (we don't change the index)

This will implement the idea of the previous solution without making unnecessary loops that may cause TLE.


### Additional Solution (Accepted + Better Memory): 

```C++ 
    class Solution {
public:

    vector<int> memo;

    int dp(int val, vector<int>& coins){
        if(val <= 0){
            return not val ? 0 : int(1e7);
        }
        int& ret = memo[val];
        if(~ret){
            return ret;
        }
        ret = int(1e7);

        for(int idx = 0; idx < coins.size(); idx++){
            ret = min(ret, 1 + dp(val - coins[idx], coins));
        }
        return ret;
    }

    int coinChange(vector<int>& coins, int amount) {
        memo.assign(amount + 5, -1);
        int ans = dp(amount, coins);
        if(ans > amount)
            ans = -1;
        return ans;
    }
};
```

This solution is changing the prespective we look at the solution from. Instead of finding the best answer for the current value starting from a particular coin, we are trying to find the best answer for the current value and discarding index's dimension.  
For each call, we are iterating over the set of coins we have and trying to pick a suitable coin for current Total Amount, and then proceeding to the next resulting value after picking this coin. 