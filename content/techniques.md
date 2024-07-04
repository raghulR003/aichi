+++
title = 'Tricks'
date = 2024-07-04T07:55:28+05:30
draft = false
description = "A compilation of tricks I learnt while coding"
image = ""
imageBig = ""
categories = ["general"]
authors = ["Raghul"]
avatar = "/images/avatar.webp"

+++

### Find the number of digits in a number - Optimal Solution:

The logarithmic base 10 of a positive integers gives the number of  digits in n. We add 1 to the result to ensure that the count is correct  even for numbers that are powers of 10.

```java
public class pattern9 {
    public static void main(String args[]){
        int n = 89765;
        int val = (int)(Math.log10(n))+1;
        System.out.print("For "+n+" the number of digits is: "+val);
    }
}
```

