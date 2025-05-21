# Custom Doubly Linked List – Custom Palindrome Checker

## Problem Summary

The goal is to create a custom **DoublyLinkedList** class in Python (without using any built-in list, deque, set, or similar data structures). This list will store a sequence of characters and determine if it forms a **custom palindrome** based on specific rules.

### Custom Palindrome Rules

A sequence is a **custom palindrome** if:
- It reads the same **forward and backward**.
- It ignores **case** (**'A'** and **'a'** are treated the same).
- It skips **vowels** (**a, e, i, o, u**).
- It ignores **duplicate characters**, considering only the **first occurrence** per direction (left-to-right and right-to-left).

---

## Approach Used

- Implement a **Node class** with *char*, *prev*, and *next* attributes.
- Implement a **DoublyLinkedList class**:
  - **insert(char)**: Adds alphabetic characters to the list.
  - **_get_filtered_string(reverse)**: 
    - Traverses the list in forward or backward direction.
    - Filters out vowels and previously seen characters.
    - Tracks duplicates using a manual string (not set).
    - Returns the filtered sequence as a string.
  - **is_custom_palindrome()**: Compares filtered strings from both directions to determine if the sequence is a custom palindrome.
- The code avoids all disallowed Python features: no *list*, *set*, *deque*, *.reverse()*, or *slicing*.

---

## Time & Space Complexity

### Time Complexity

Let **n** be the length of the input string.

- **insert(char)**:  
  Inserts each character once → **O(n)** time.

- **_get_filtered_string(reverse=False/True)**:
  - Traverses the entire list once → O(n)
  - For each character:
    - Converts to lowercase → O(1)
    - Checks if it's a vowel → O(1) (compared against 5 vowels)
    - Checks if it has already been seen → max 21 comparisons (only consonants, case-insensitive)
  - So, per character = O(1) → total = **O(n)**

- **is_custom_palindrome()**:
  - Calls *_get_filtered_string()* twice → O(n) + O(n)
  - Compares the two filtered strings character-by-character → O(n)

**Final Total Time Complexity:**  
**O(n)** + **O(n)** + **O(n)** = **O(n)**

### Space Complexity

- The doubly linked list holds each character → O(n)
- Two filtered strings are created → O(n)
- Temporary **seen** string for each traversal → O(21) = O(1)

**Final Total Space Complexity:**  
**O(n)**

---

## Sample Test Cases

Input->Output

 1. "Deified" -> True
 2. "ddoodd"  -> True
 3. "banana"  -> False
 4. "Radar"   -> True
 5. "Reefer"  -> True
 6. "pop"     -> True
 7. "sagas"   -> True
 8. "yellow"  -> False
 9. "noonnoon" -> True
 10. "Xbbzbx" -> True
 11. "cbfcbf" -> False
 12. "Aabaaa" -> True
 13. "abcxyzzyxcba" -> True
 14. "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPpQqRrSsTtUuVvWwXxYyZz" -> False



---

## Constraints

-  Did not use: *list*, *set*, *dict*, *deque*
-  Did not use: *.reverse()*, *slicing ([::-1])*
-  Only used **str** for basic character tracking and comparison
-  All logic is implemented using custom traversal and comparison

