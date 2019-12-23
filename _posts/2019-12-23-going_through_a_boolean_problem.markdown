---
layout: post
title:      "Going Through a Boolean Problem"
date:       2019-12-23 20:38:59 +0000
permalink:  going_through_a_boolean_problem
---


An interesting problem that I solved whilst learning booleans was learning how multiple true or false statements interact with different boolean operators such as !(NOT), &&(AND), and ||(OR). When I was in college, I had learned about similar problems in Boolean Algebra, so these problems weren't so difficult, but it was fun to revisit the same kind of material I learned about in school. As an example, let's take a look at problem 3 from the Truthiness Code Challenge in the Booleans module in the Procedural Ruby topic on Learn.co. The problem states:
> Take a look at the method using_truthiness below. 
 
>What value(s) for ? will make using_truthiness return false?

> def using_truthiness

> 7 > 8 || ?

> end
>> false

>>8 > 9

>>!true

>>!false

So we want the statement inside #using_truthiness to evaluate to false so that #using_truthiness returns false. The statement is a boolean OR and boolean ORs only evaluate to false when both A and B evaluate to false (if the statement is of the form A V B). Fortunately, 7 > 8 is already false, so we need only to select answers that evaluate to false which are false, 8>9, and !true since !false evaluates to true and would cause #using_truthiness to evaluate true as a result.
