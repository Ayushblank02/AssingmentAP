# Sorting a Linked List using Merge Sort in Java

## Overview
This Java program sorts a singly linked list using the **Merge Sort** algorithm. Merge Sort is an efficient, stable, and divide-and-conquer sorting algorithm with a time complexity of **O(n log n)**, making it optimal for sorting linked lists.

## Features
- Uses **Merge Sort** for sorting.
- Implements **slow and fast pointer technique** to find the middle of the list.
- Recursively sorts and merges sublists.
- Efficient with **O(n log n)** time complexity and **O(1) space complexity** (excluding recursion stack).

## How It Works
1. **Find the middle node** using slow and fast pointers.
2. **Split the list** into two halves.
3. **Recursively sort** both halves.
4. **Merge the sorted halves** back together.

## Implementation
### **Class Definition**
```java
// Definition for singly-linked list.
public class ListNode {
    int val;
    ListNode next;
    ListNode() {}
    ListNode(int val) { this.val = val; }
    ListNode(int val, ListNode next) { this.val = val; this.next = next; }
}
```

### **Sorting a Linked List**
```java
class Solution {
    public ListNode sortList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        
        ListNode mid = getMiddle(head);
        ListNode rightHead = mid.next;
        mid.next = null; // Break the list into two halves

        ListNode leftSorted = sortList(head);
        ListNode rightSorted = sortList(rightHead);

        return merge(leftSorted, rightSorted);
    }

    private ListNode getMiddle(ListNode head) {
        ListNode slow = head, fast = head.next;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }

    private ListNode merge(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                current.next = l1;
                l1 = l1.next;
            } else {
                current.next = l2;
                l2 = l2.next;
            }
            current = current.next;
        }

        if (l1 != null) current.next = l1;
        if (l2 != null) current.next = l2;

        return dummy.next;
    }
}
```

## Example Usage
### **Input:**
```
head = [4, 2, 1, 3]
```

### **Output:**
```
[1, 2, 3, 4]
```

## Complexity Analysis
- **Time Complexity:** O(n log n)
- **Space Complexity:** O(1) (excluding recursion stack)

## Why Merge Sort for Linked Lists?
- **Does not require random access** (unlike Quick Sort).
- **Efficient for large lists**.
- **Stable sorting algorithm**.

## How to Run the Program
1. Compile the Java file using:
   ```sh
   javac Solution.java
   ```
2. Run the program with:
   ```sh
   java Solution
   ```

## Conclusion
This program efficiently sorts a linked list using **Merge Sort**, making it optimal for linked list sorting. 🚀

