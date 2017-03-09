---
layout: post
title:  "PERMUTATIONS"
date:   2017-03-09 05:30:23 +0000
---


Permutation is a way of arranging/rearranging all members of  a set into some sequence or order. Order matters in a permutation, as opposed to a combination, where order does not matter (a combination lock is actually more like a permutation lock).
Permutations determine all possible arrangement or order of characters in a set.
To calculate how many possible permutations a set of characters of size ' n' we calculate the factorial of 'n'. 

Here is a method to get the factorial of n:

```
def factorial(n)     
if n==0
1
else 
n * factorial(n-1) 
end
end
```

In order to get the number of all possible permutations for a string of size 3, such as "abc":

* factorial(3) 
* => 6

There are different algorithms to get all possible permutations of a set of characters, for this blog post, I used Heap's Algorithm.
Heap's algorithm gets each permutation from the previous by swapping two elements at a time. Basically it fixes the element in the last position, conducts all permutations for the rest of the elements and then, swaps the last fixed element with one of the other elements, recursively doing this n!-1 swaps (factorial of n -1):

 0 | 123
 1 | 213
 2 | 312
 3 | 132
 4 | 231
 5 | 321


Here is a ruby interpretation of this algorithm 

```
def perms (array, n = array.size-1)
    if  n == 0
   
        return array
    else
        for i in 0..n do 
            perms(array, n-1)
            if (n-1) % 2 == 1 
                array[1], array[n] = array[n], array[1]
            else
                array[i], array[n] = array[n], array[i]
            end
        end
    end
end
```

I will get more into the details on how the algorithm works on the next blog post. The details are a little bit complicated and the fact that it uses recursion to do this contributes to the complexity of the algorithm. Looking at the example with the set of numbers and how each permutation changes helped me understand a little bit better how it works. 







