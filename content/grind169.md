+++
title = 'Things I learnt while grinding: The Grind75 Edition'
date = 2024-06-16T10:21:32+05:30
draft = false
description = "There isn't much right now, cuz I've just started."
image = "/images/grind.png"
imageBig = "/images/grind.png"
categories = ["coding","placement"]
authors = ["Raghul"]
avatar = "/images/avatar.webp"

+++

> [**Grind75**](https://www.techinterviewhandbook.org/grind75?weeks=26&hours=40) - Click to view the original site.

------

#### Two Sum:

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

#### Valid Parantheses:

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

