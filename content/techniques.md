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

### Find the number of digits in a number - Optimal Solution :

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

### Finding the signed right shift (by 1,2,3...) :

So, for a decimal number (ex: 120), the values will be the integer division by 2 at each consecutive step. If the number is less than 4, then the value is **1**. Also note that **1>>1 = 1**.

```markdown
120 >> 1 = 60
60 >> 1 == 120 >> 2 == 30
30 >> 1 == 60 >> 2 === 120 >>3 ==15
and so on....
```

### Fastest way to check if a number is odd or even (while having access to code env) :

To do that, run the number in a Boolean declaration as ( x & 1 ), if the result is **True**, the number is **Odd** and if it's **False**, then it's **Even**.

```java
public static void main (String args[]){
        int num = 99;
        System.out.print((num&1)==1?"odd":"even");       
    }
```

