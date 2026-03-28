# Rearrange Array Alternating Positive and Negative

## 📌 Problem Statement
Given an array of integers, rearrange the elements such that positive and negative numbers are placed alternately.  

- Maintain the **relative order** of elements (stable order).
- If one category (positive/negative) runs out, append the remaining elements.

---

## 🧠 Approach

1. Traverse the array and split elements into:
   - `positive` list (including 0)
   - `negative` list

2. Merge both lists alternately:
   - Start placing elements from positive, then negative.

3. If one list finishes:
   - Append the remaining elements of the other list.

---

## ⚠️ Important Points

- `0` is treated as **positive**
- Order of elements must remain **unchanged**
- Use `ArrayList.set(index, value)` to modify elements

---

## 💻 Code Implementation (Java)

```java
class Solution {
    void rearrange(ArrayList<Integer> arr) {
        
        ArrayList<Integer> positive = new ArrayList<>();
        ArrayList<Integer> negative = new ArrayList<>();
        
        // Step 1: Separate elements
        for (int ele : arr) {
            if (ele >= 0) positive.add(ele);
            else negative.add(ele);
        }
        
        int i = 0, idx = 0;
        
        // Step 2: Alternate merge
        while (i < positive.size() && i < negative.size()) {
            arr.set(idx++, positive.get(i));
            arr.set(idx++, negative.get(i));
            i++;
        }
        
        // Step 3: Remaining positives
        while (i < positive.size()) {
            arr.set(idx++, positive.get(i));
            i++;
        }
        
        // Step 4: Remaining negatives
        while (i < negative.size()) {
            arr.set(idx++, negative.get(i));
            i++;
        }
    }
}
⏱️ Complexity Analysis
Time Complexity: O(n)
Space Complexity: O(n) (extra lists used)
🧪 Example
Input
[9, 4, -2, -1, 5, 0, -5, -3, 2]
Output
[9, -2, 4, -1, 5, -5, 0, -3, 2]


Author
Sanjeev sharma
