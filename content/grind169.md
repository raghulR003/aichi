+++
title = 'The Grind75 Edition - Full Solutions'
date = 2024-06-16T10:21:32+05:30
draft = false
description = "Started pretty well...."
image = "/images/grind.png"
imageBig = "/images/grind.png"
categories = ["coding","placement"]
authors = ["Raghul"]
avatar = "/images/avatar.webp"

+++

> [**Grind75**](https://www.techinterviewhandbook.org/grind75?weeks=26&hours=40) - Click to view the original site.

------

# Contents
 - [Two Sum](#two-sum) 
 - [Valid Parentheses](#valid-parantheses)

------



## Two Sum:

####two-sum

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.You can return the answer in any order.

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       for (int i = 1; i < nums.length; i++) {
            for (int j = i; j < nums.length; j++) {
                if (nums[j] + nums[j - i] == target) {
                    return new int[]{j, j - i};
                }
            }
        }
        return null;
    }
}
```

------



## Valid Parentheses:

####valid-parantheses

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

**Example 1:**

```
Input: s = "()"
Output: true
```

**Example 2:**

```
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```
Input: s = "(]"
Output: false
```

```Java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stk=new Stack<Character>();
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)=='(' ||s.charAt(i)=='{' ||s.charAt(i)=='['){
                stk.push(s.charAt(i));
            }
            else if(s.charAt(i)==')' ||s.charAt(i)=='}' ||s.charAt(i)==']'){
                if(stk.isEmpty()) {
                    return false;
                }
                else if(s.charAt(i)==')' && stk.peek()=='('){
                    stk.pop();
                }
                else if(s.charAt(i)=='}' && stk.peek()=='{'){
                    stk.pop();
                }
                else if(s.charAt(i)==']' && stk.peek()=='['){
                    stk.pop();
                }
                else{
                    return false;
                }
            }
            else{
                return false;
            }
        }
        return stk.isEmpty();  // The stack should be empty at the end for all brackets to be valid
    }
}
```

------



## ## Merge Two Sorted Lists:

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return *the head of the merged linked list*.

**Example 1:**

```
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**Example 2:**

```
Input: list1 = [], list2 = []
Output: []
```

**Example 3:**

```
Input: list1 = [], list2 = [0]
Output: [0]
```

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0); // Dummy node to start the merged list
        ListNode current = dummy;  // Pointer to traverse the merged list

        // Handle empty list cases (you had this right!)
        if (list1 == null) {
            return list2;
        } else if (list2 == null) {
            return list1;
        }

        // Iterate until both lists are exhausted
        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                current.next = new ListNode(list1.val); // Create new node
                list1 = list1.next;
            } else {
                current.next = new ListNode(list2.val); 
                list2 = list2.next;
            }
            current = current.next; // Move to the next node in the merged list
        }

        // Add any remaining nodes from list1 or list2
        current.next = (list1 != null) ? list1 : list2;

        return dummy.next; // Return the head of the merged list
    }
}
```

------

