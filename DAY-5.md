**Problem description**

**Stock Buy and Sell – Multiple Transaction Allowed**

The cost of stock on each day is given in an array price[]. Each day you may decide to either buy or sell the stock at price[i], you can even buy and sell the stock on the same day. Find the maximum profit that you can get.

Note: A stock can only be sold if it has been bought previously and multiple stocks cannot be held on any given day.

Examples:

Input: prices[] = [100, 180, 260, 310, 40, 535, 695]
Output: 865
Explanation: Buy the stock on day 0 and sell it on day 3 => 310 – 100 = 210. Buy the stock on day 4 and sell it on day 6 => 695 – 40 = 655. Maximum Profit = 210 + 655 = 865.

**Approach**



🧠 Approach:
1️⃣ Traverse the array and look for consecutive upward price trends.
2️⃣ Buy stock on the first day of an upward trend and sell on the last day of that trend.
3️⃣ Add the difference between the buy and sell prices to the total profit.
4️⃣ Repeat for all upward trends in the array.

**code**

      class Solution {
    public int maximumProfit(int prices[]) {
        int profit = 0;

        // Traverse the prices array to calculate profit for all possible transactions
        for (int i = 1; i < prices.length; i++) {
            // If the price today is higher than the previous day, sell for profit
            if (prices[i] > prices[i - 1]) {
                profit += prices[i] - prices[i - 1];
            }
        }

        return profit;
    }
    }
