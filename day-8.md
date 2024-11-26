******💡 Day 8 Problem: Majority Element II**

**🧠 Approach:**
**1️⃣ Understand the Problem:**

A majority element appears more than n/3 times in an array of size n.
There can be at most two majority elements.
**2️⃣ Apply Boyer-Moore Voting Algorithm:**

Maintain two potential candidates (candidate1, candidate2) and their respective counts (count1, count2).
Iterate through the array:
If the current element matches candidate1 or candidate2, increment the respective count.
If a count is zero, replace the corresponding candidate with the current element and set the count to 1.
Otherwise, decrement both counts.
**3️⃣ Verify Candidates:**

Reiterate through the array to count occurrences of candidate1 and candidate2 to confirm they exceed n/3.
**📌 Key Takeaways:**
🔹 The Boyer-Moore Voting Algorithm optimizes this problem to O(n) time complexity and O(1) space complexity.
🔹 Verification is essential to ensure that the candidates meet the majority condition.
🔹 Always consider edge cases like arrays with fewer than three elements or no majority elements.

**code**

      import java.util.*;
    public List<Integer> findMajorityElements(int[] arr) {
    int n = arr.length;
    int candidate1 = 0, candidate2 = 0, count1 = 0, count2 = 0;

    // Step 1: Find potential candidates
    for (int num : arr) {
        if (num == candidate1) {
            count1++;
        } else if (num == candidate2) {
            count2++;
        } else if (count1 == 0) {
            candidate1 = num;
            count1 = 1;
        } else if (count2 == 0) {
            candidate2 = num;
            count2 = 1;
        } else {
            count1--;
            count2--;
        }
    }

    // Step 2: Verify the candidates
    count1 = 0;
    count2 = 0;
    for (int num : arr) {
        if (num == candidate1) count1++;
        else if (num == candidate2) count2++;
    }

    List<Integer> res = new ArrayList<>();
    if (count1 > n / 3) res.add(candidate1);
    if (count2 > n / 3) res.add(candidate2);

    // Ensure ascending order
    if (res.size() == 2 && res.get(0) > res.get(1)) {
        Collections.swap(res, 0, 1);
    }

    return res;
}
