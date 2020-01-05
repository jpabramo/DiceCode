[]{#section0001.xhtml}

[DiceCode Programming Language]{.span0}

[Prebuild ISO version Alpha 1.0]{.span1}

[January 05, 2020]{.span1}

 

 

[]{#section0002.xhtml}

[Introduction]{.span2}

[DiceCode is a programming language made to facilitate analysis of probability distributions, specially when related to dice rolls ]{.span3}[and games, using linguistic elements common to many tabletop games.]{.span3}

[Conventions]{.span4}

[In this document, text in bold between ]{.span3}[lesser-than, greater-than signs]{.span3}[ (\<\>) is read as an expression.]{.span3}

[\<expression\>]{.span5}

[Reference to ]{.span3}[names]{.span3}[ in text is explicit by italics.]{.span3}

[Type, ]{.span6}[expression or variable reference]{.span6}

[]{#section0003.xhtml}

[Supported ]{.span2}[Characters]{.span2}

[Symbols]{.span4}

[+ - \* / % ( ) \[ \] { } \< \> ? ! = . , ; : \# & \| ]{.span3}[(space character)]{.span7}

[Alphanumeric]{.span4}

[\[a, z\], \[A, Z\], \[0, 9\]]{.span8}

[Special ]{.span4}[C]{.span4}[haracters]{.span4}

[\\n ]{.span8}[\\t]{.span8}

[]{#section0004.xhtml}

[Syntax]{.span2}

[Line]{.span4}

[A line contains one or more expression and is ended by a semi-colon (;). The interpreter ignores almost all spaces ( ), all tab (\\t) and all line-break (\\n) characters, so it requires semi-colons to locate code lines.]{.span3}

[\<expressions\>;]{.span5}

[Variable Types]{.span4}

[v]{.span9}[oid]{.span9}

[Represents nothing, or ]{.span8}[null]{.span6}[. Used for valueless expressions or functions that do not return anything.]{.span10}

[i]{.span9}[nt]{.span9}

[Represents i]{.span8}[nteger numbers ]{.span8}[i]{.span8}[n the r]{.span8}[ange]{.span8}[ \[-(2\^31), 2\^31-1\]]{.span8}[.]{.span8}

[frac]{.span9}

[Represents r]{.span8}[ational numbers ]{.span8}[i]{.span8}[n the r]{.span8}[ange]{.span8}[ ]{.span8}[\[]{.span8}[-(2\^3]{.span8}[1]{.span8}[), 2\^3]{.span8}[1]{.span8}[-1]{.span8}[\]]{.span8}[ with 2\^(-3]{.span8}[2]{.span8}[) precision. Each ]{.span8}[frac]{.span6}[ is composed of two ]{.span8}[ints]{.span6}[, a nominator and a]{.span8}[n unsigned]{.span8}[ denominator. Fractions are always displayed in their simplified form. ]{.span8}[If denominator is 0, ]{.span8}[frac]{.span6}[ evaluates to ]{.span10}[infinity ]{.span6}[or ]{.span10}[neg\_infinity]{.span6}[.]{.span10}

[r]{.span9}[oll]{.span9}

[Roll variables. A roll is an expression that represents a random event, more specifically a dice roll.]{.span8}

[roll complex\_mod = 1d(2d8) + (1d8 \> 4? 4: ]{.span7}[1d4]{.span7}[);]{.span7}

[/\* Roll with complicated modifiers.]{.span7}

[When evaluated to an int, the first dice needs its faces evaluated into an int to determine how many faces such dice has.]{.span7}

[The roll's modifier is a ternary conditional, so it is evaluated to one of ]{.span7}[its expressions.]{.span7}

[\*/]{.span7}

[Arrays]{.span9}

[\<t]{.span11}[ype]{.span11}[\>]{.span11}[\[\] ]{.span11}[-]{.span10}[ ]{.span11}[Array variable ]{.span10}[of type ]{.span10}[type]{.span6}[. Arrays have variable size and can have multiple dimensions.]{.span10}

[Declaration and Initialization]{.span9}

[\<type\> \<name\>; ]{.span11}[-- Variable declaration.]{.span10}

[\<type\>\[\] \<name\>; ]{.span5}[-- Array declaration. Declares a new empty array of type ]{.span8}[type]{.span6}[.]{.span10}

[\<type\>\[\<]{.span11}[int]{.span11}[\>\] \<name\>; ]{.span11}[-- Array declaration. Declares a new empty array of type ]{.span10}[type ]{.span6}[and size equal to the value of the ]{.span10}[int ]{.span6}[expression.]{.span10}

[Built-in ]{.span4}[F]{.span12}[unction]{.span12}[alit]{.span12}[ies]{.span12}

[Unary Operations]{.span9}

[Casting]{.span13}

[(]{.span5}[f]{.span5}[rac]{.span5}[)]{.span5}[ ]{.span5}[\<int\>]{.span5}[ ]{.span5}[-- The resulting ]{.span8}[frac]{.span6}[ ]{.span10}[expression ]{.span10}[has the original ]{.span10}[int ]{.span6}[as ]{.span10}[i]{.span10}[ts]{.span10}[ nominator and 1 as ]{.span10}[i]{.span10}[ts]{.span10}[ denominator.]{.span10}

[(int)]{.span11}[ ]{.span11}[\<frac\>]{.span11}[ ]{.span11}[-- The resulting ]{.span10}[int]{.span6}[ ]{.span10}[expression ]{.span10}[is ]{.span10}[equal to the ]{.span10}[frac]{.span6}['s nominator divided by its denominator.]{.span10}

[(int) \<]{.span11}[roll]{.span11}[\> ]{.span11}[--]{.span10}[ ]{.span11}[The resulting ]{.span10}[int]{.span6}[ ]{.span10}[expression ]{.span10}[is ]{.span10}[a possible result of the roll. The result is generated following the logic of the roll expression. ]{.span10}[Casting from ]{.span10}[roll]{.span6}[ to ]{.span10}[int]{.span6}[ can be implicit.]{.span10}

[(]{.span11}[roll) \<int\> ]{.span11}[-- The resulting ]{.span10}[roll]{.span6}[ expression is composed of only a modifier.]{.span10}

[(]{.span11}[\<target\_type\>\[\]) \<origin\_type\>\[\]]{.span11}[ ]{.span11}[-- The resulting array is an element-]{.span10}[wise]{.span10}[ cast of the first array into ]{.span10}[t]{.span6}[arget\_type]{.span6}[.]{.span10}

[Logical ]{.span13}[N]{.span14}[egation]{.span14}

[!]{.span11}[\<int\> ]{.span11}[-- The resulting expression is equal to 1 if the ]{.span10}[int ]{.span6}[expression is 0 and 0 otherwise. ]{.span10}[A]{.span10}[pplied]{.span10}[ element-wise for arrays.]{.span10}

[Negation, Increment and Decrement]{.span14}

[-\<]{.span11}[expression]{.span11}[\> ]{.span11}[-- The resulting expression is equal to the negative of ]{.span10}[expression]{.span6}[. ]{.span10}[If ]{.span10}[expression ]{.span6}[is an array, then the negation is applied element-wise.]{.span10}

[\<variable\>++ ]{.span5}[-- ]{.span8}[Adds 1 to]{.span8}[ the value of ]{.span8}[variable]{.span6}[ in the order ]{.span10}[variable]{.span6}[+1. ]{.span10}[A]{.span10}[pplied]{.span10}[ element-wise for arrays. ]{.span10}[The resulting expression is equal to the new value of ]{.span10}[variable.]{.span6}

[++\<variable\>]{.span11}[ -- Adds 1 to the value of ]{.span10}[variable ]{.span6}[in the order 1+]{.span10}[variable]{.span6}[. ]{.span10}[A]{.span10}[pplied]{.span10}[ element-wise for arrays. ]{.span10}[The resulting expression is equal to the new value of ]{.span10}[variable.]{.span6}

[\<]{.span11}[variable\>\-- ]{.span11}[-- Subtracts 1 to the value of ]{.span10}[variable ]{.span6}[in the order ]{.span10}[variable]{.span6}[-1. ]{.span10}[A]{.span10}[pplied]{.span10}[ element-wise for arrays. ]{.span10}[The resulting expression is equal to the new value of ]{.span10}[variable.]{.span6}

[\--\<variable\> ]{.span11}[-- Subtracts 1 to the value of ]{.span10}[variable ]{.span6}[in the order -1+]{.span10}[variable]{.span6}[. ]{.span10}[A]{.span10}[pplied]{.span10}[ element-wise for arrays. ]{.span10}[The resulting expression is equal to the new value of ]{.span10}[variable.]{.span6}

[Binary Operations]{.span9}

[Assignment]{.span13}

[\<type\> \<]{.span5}[v]{.span5}[ar]{.span5}[\> = \<expression\>]{.span5}[;]{.span5}[ ]{.span5}[-- ]{.span8}[Declares the variable ]{.span8}[v]{.span6}[ar]{.span6}[ ]{.span6}[of type ]{.span10}[type ]{.span6}[and ]{.span10}[i]{.span10}[nitializes it]{.span10}[ to it the value of ]{.span10}[expression]{.span6}[.]{.span10}

[\<]{.span11}[var]{.span11}[\> = \<expression\> ]{.span11}[-- Assigns the value of ]{.span10}[expression ]{.span6}[to the variable ]{.span10}[var]{.span6}[. ]{.span10}[The ]{.span10}[r]{.span10}[esulting]{.span10}[ expression is of the same type and value ]{.span10}[a]{.span10}[s]{.span10}[ ]{.span10}[var]{.span6}[.]{.span10}

[\<]{.span11}[var\> ]{.span11}[\<op\>]{.span11}[= \<expression\> ]{.span11}[-- Assigns ]{.span10}[the value of ]{.span10}[the operation ]{.span10}[op]{.span6}[ between]{.span10}[ var]{.span6}[ and]{.span10}[ expression]{.span6}[ to]{.span10}[ var.]{.span6}[ ]{.span6}[The resulting expression is equal to the new value of ]{.span10}[var]{.span6}[.]{.span10}

[D]{.span14}[ies]{.span14}

[Dies are written in d-notation, which consists of two values separated by the letter 'd'. The ]{.span10}[value of the ]{.span10}[first ]{.span10}[e]{.span10}[xpression]{.span10}[ is the amount of dies, and the ]{.span10}[value of the]{.span10}[ second ]{.span10}[e]{.span10}[xpression]{.span10}[ is the amount of faces of those dies.]{.span10}

[Rolls can also have modifiers. These modifiers can be composite of any expression that evaluates to a ]{.span10}[roll ]{.span6}[or ]{.span10}[int]{.span6}[.]{.span10}

[\<quantity\>d\<value\> ]{.span11}[\<modifiers\>]{.span11}

[Example:]{.span7}

[roll ]{.span7}[simple]{.span7}[ = 1d4; //]{.span7}[simple roll of a 4-sided dice.]{.span7}

[roll mult = 2d6; //simple roll of 2 6-sided dies.]{.span7}

[roll mod = 1d20 + 1; //roll with simple modifier.]{.span7}

[roll mult\_mod = 1d4 + 1d6 + 1d8; //roll with two modifiers, each being a roll.]{.span6}

[\<amount\>d\<faces\>l\<]{.span11}[filter]{.span11}[\> ]{.span11}[-- This roll is composed of ]{.span10}[amount ]{.span6}[dies of ]{.span10}[faces]{.span6}[-sided dies, but only the top ]{.span10}[filter]{.span6}[ are considered. For example, let a roll of 4d6 have the result {2, 3, 4, 4}, or 13 in total. If that roll had been 4d6l3 instead, the result would only consider the top 3 results, so it would have been {3, 4, 4} instead, having a total value of 11.]{.span10}

[\<]{.span11}[amount\>d\<faces\>s\<filter\>]{.span11}[ -- This roll is composed of ]{.span10}[amount]{.span6}[ dies of ]{.span10}[faces]{.span6}[-sided dies, but only the bottom ]{.span10}[filter]{.span6}[ are considered. In the example above, if the roll had been 4d6s3 then the result would have been {2, 3, 4}, or ]{.span10}[9 in total.]{.span10}

[Addition]{.span13}

[\<]{.span11}[int]{.span11}[\>]{.span11}[+]{.span11}[\<i]{.span11}[nt]{.span11}[\>]{.span11}[ ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is an ]{.span10}[int]{.span6}[ ]{.span10}[expression ]{.span10}[whose value is equal to the sum of the two ]{.span10}[int]{.span6}[ expressions.]{.span10}

[\<int\>+\<frac\>]{.span11}[ or]{.span15}[ \<frac\>+\<int\> ]{.span11}[-]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is a ]{.span10}[frac]{.span6}[ whose value is equal to the sum of the ]{.span10}[cast of the ]{.span10}[int]{.span6}[ ]{.span10}[expression]{.span10}[ ]{.span10}[into a ]{.span10}[frac ]{.span6}[expression]{.span10}[ ]{.span6}[and the ]{.span10}[original]{.span10}[ ]{.span10}[frac]{.span6}[ ]{.span10}[expression]{.span10}[.]{.span10}

[\<]{.span11}[frac\>+\<frac\> ]{.span11}[- The resulting expression is a ]{.span10}[frac ]{.span6}[whose value is the sum of the two ]{.span10}[frac ]{.span6}[expressions.]{.span10}

[\<]{.span11}[int\>+\<roll\> ]{.span11}[-]{.span10}[ ]{.span11}[The resulting ]{.span10}[expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to the sum of the original ]{.span10}[int ]{.span6}[expression and a cast from the ]{.span10}[roll ]{.span6}[expression into ]{.span10}[int]{.span6}[.]{.span10}

[\<]{.span11}[roll\>+\<int\>]{.span11}[ or]{.span15}[ \<roll\>+\<roll\> - ]{.span11}[The resulting expression is a ]{.span10}[roll]{.span6}[.]{.span10}

[Subtraction]{.span13}

[\<]{.span11}[int]{.span11}[\>]{.span11}[-]{.span11}[\<i]{.span11}[nt]{.span11}[\>]{.span11}[ ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is an ]{.span10}[int]{.span6}[ ]{.span10}[expression ]{.span10}[whose value is equal to the difference of the two ]{.span10}[int]{.span6}[ expressions.]{.span10}

[\<int\>-\<frac\>]{.span11}[ or]{.span15}[ \<frac\>-\<int\> ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is a ]{.span10}[frac]{.span6}[ whose value is equal to the difference of the ]{.span10}[cast of the ]{.span10}[int]{.span6}[ ]{.span10}[expression]{.span10}[ ]{.span10}[into a ]{.span10}[frac ]{.span6}[expression]{.span10}[ ]{.span6}[and the ]{.span10}[original]{.span10}[ ]{.span10}[frac]{.span6}[ ]{.span10}[expression]{.span10}[.]{.span10}

[\<]{.span11}[frac\>-\<frac\> ]{.span11}[--]{.span10}[ ]{.span11}[T]{.span10}[he resulting expression is a ]{.span10}[frac ]{.span6}[whose value is the difference of the two ]{.span10}[frac ]{.span6}[expressions.]{.span10}

[\<]{.span11}[int\>-\<roll\> ]{.span11}[-- The resulting ]{.span10}[expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to the difference of the original ]{.span10}[int ]{.span6}[expression and a cast from the ]{.span10}[roll ]{.span6}[expression into ]{.span10}[int]{.span6}[.]{.span10}

[\<]{.span11}[roll\>-\<int\>]{.span11}[ or]{.span15}[ \<roll\>-\<roll\>]{.span11}[ -- The resulting expression is a ]{.span10}[roll]{.span6}[.]{.span10}

[Multiplication]{.span13}

[\<]{.span11}[int]{.span11}[\>\*\<i]{.span11}[nt]{.span11}[\>]{.span11}[ ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is an ]{.span10}[int]{.span6}[ ]{.span10}[expression ]{.span10}[whose value is equal to the product of the two ]{.span10}[int]{.span6}[ expressions.]{.span10}

[\<int\>\*\<frac\>]{.span11}[ or]{.span5}[ \<frac\>\*\<int\>]{.span11}[ ]{.span16}[--]{.span10}[ ]{.span16}[The ]{.span10}[resulting]{.span10}[ expression is a ]{.span10}[frac]{.span8}[ whose value is equal to the product of the ]{.span10}[cast of the ]{.span10}[int]{.span8}[ ]{.span10}[expression]{.span10}[ ]{.span10}[into a ]{.span10}[frac ]{.span8}[expression]{.span10}[ ]{.span8}[and the ]{.span10}[original]{.span10}[ ]{.span10}[frac]{.span8}[ ]{.span10}[expression]{.span10}[.]{.span10}

[\<]{.span11}[frac\>\*\<frac\> ]{.span11}[-- The resulting expression is a ]{.span10}[frac ]{.span6}[whose value is the product of the two ]{.span10}[frac ]{.span6}[expressions.]{.span10}

[\<]{.span11}[int\>\*\<roll\> ]{.span11}[--]{.span10}[ ]{.span11}[The resulting ]{.span10}[expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to the product of the original ]{.span10}[int ]{.span6}[expression and a cast from the ]{.span10}[roll ]{.span6}[expression into ]{.span10}[int]{.span6}[.]{.span10}

[\<]{.span11}[roll\>\*\<int\>]{.span11}[ or]{.span15}[ \<roll\>\*\<roll\>]{.span11}[ -- The resulting expression is a ]{.span10}[roll]{.span6}[.]{.span10}

[Division]{.span13}

[\<int\>/\<int\> ]{.span5}[--]{.span8}[ ]{.span5}[The resulting expression is a ]{.span8}[frac ]{.span6}[expression whose nominator is the first ]{.span10}[int ]{.span6}[expression and whose denominator is the unsigned version of the second ]{.span10}[int ]{.span6}[expression. If the denominator is negative, the nominator is multiplied by -1.]{.span10}

[\<int\>/\<frac\> ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is a ]{.span10}[frac]{.span6}[ whose value is equal to the fraction of the ]{.span10}[cast of the ]{.span10}[int]{.span6}[ ]{.span10}[expression]{.span10}[ ]{.span10}[into a ]{.span10}[frac ]{.span6}[expression]{.span10}[ ]{.span6}[o]{.span10}[ver]{.span10}[ the ]{.span10}[original]{.span10}[ ]{.span10}[frac]{.span6}[ ]{.span10}[expression]{.span10}[.]{.span10}

[\<frac\>/\<int\> ]{.span11}[--]{.span10}[ ]{.span11}[The ]{.span10}[resulting]{.span10}[ expression is a ]{.span10}[frac]{.span6}[ whose value is equal to the fraction of the ]{.span10}[original]{.span10}[ ]{.span10}[frac]{.span6}[ ]{.span10}[expression ]{.span10}[o]{.span10}[ver]{.span10}[ the]{.span10}[ ]{.span10}[cast of the ]{.span10}[int]{.span6}[ ]{.span10}[expression]{.span10}[ ]{.span10}[into a ]{.span10}[frac ]{.span6}[expression]{.span10}[.]{.span10}

[\<]{.span11}[frac\>/\<frac\> ]{.span11}[--]{.span10}[ ]{.span11}[The resulting expression is a ]{.span10}[frac ]{.span6}[whose value is the ]{.span10}[d]{.span10}[ivision]{.span10}[ of the two ]{.span10}[frac ]{.span6}[expressions.]{.span10}

[\<]{.span11}[int\>/\<roll\> ]{.span11}[--]{.span10}[ ]{.span11}[The resulting ]{.span10}[expression is ]{.span10}[a]{.span10}[ frac]{.span6}[ ]{.span6}[expression whose value is equal to the fraction of the original ]{.span10}[int ]{.span6}[expression and a cast from the ]{.span10}[roll ]{.span6}[expression into ]{.span10}[int]{.span6}[.]{.span10}

[\<]{.span11}[roll\>/\<int\> or \<roll\>/\<roll\>]{.span11}[ -- Division. The resulting expression is a ]{.span10}[frac ]{.span6}[expression whose nominator and denominators are implicit casts from ]{.span10}[roll ]{.span6}[into ]{.span10}[int ]{.span6}[expressions.]{.span10}

[Remainder]{.span13}

[\<int\>%\<int\>]{.span5}[ -- The resulting expression is an ]{.span8}[int ]{.span6}[expression whose value is equal to the remainder of the division of the first expression by the second expression.]{.span10}

[L]{.span14}[ogical]{.span14}

[\<expression\_one\>==\<expression\_two\> ]{.span11}[-- The resulting expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to 1 if the expressions have the same value or 0 if the expressions have different values.]{.span10}

[If the type of any of the expressions is ]{.span10}[roll]{.span6}[, it is evaluated to an ]{.span10}[int ]{.span6}[expression before the comparison.]{.span10}

[When used on two array variables of the same type, the resulting expression is equal to 1 if every element of the two arrays are also equal in value.]{.span10}

[\<expression\_one\>===\<expression\_two\> ]{.span11}[-- The resulting expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to 1 if the expressions are identical or 0 if the expressions are not. ]{.span10}[roll ]{.span6}[expressions are compared bit-wise, so even if they are ]{.span10}[functionally the same they will be considered different if they are worded differently.]{.span10}

[Example:]{.span6}

[int ]{.span6}[equals]{.span6}[ = ]{.span6}[(]{.span6}[1d4 + 1d6]{.span6}[)]{.span6}[ === ]{.span6}[(]{.span6}[1d]{.span6}[6]{.span6}[ + 1d4]{.span6}[)]{.span6}[; //]{.span6}[equals]{.span6}[ is 0.]{.span6}

[e]{.span6}[quals = 1d6 === 1d6; //]{.span6}[equals]{.span6}[ is 1.]{.span6}

[When used in array variables, the resulting expression will be equal to 1 if and only if the two array variable are two different references to the same array.]{.span10}

[Example:]{.span6}

[int\[\] a = {1, 2, 3};]{.span6}

[int\[\] b = a;]{.span6}

[int\[\] c = {1, 2, 3};]{.span6}

[int equals = a === b; //equals is 1]{.span6}

[equals = a === c; //equals is 0]{.span6}

[int compare = a == c; //]{.span6}[compare]{.span6}[ is 1]{.span6}

[\<expression\_one\> != \<expression\_two\> ]{.span11}[-- ]{.span10}[The resulting expression is an ]{.span10}[int ]{.span6}[expression whose value is equal to 1 if the expressions have the same value or 0 if the expressions have different values.]{.span10}

[If the type of any of the expressions is ]{.span10}[roll]{.span6}[, it is evaluated to an ]{.span10}[int ]{.span6}[expression before the comparison.]{.span10}

[When used on two array variables of the same type, the resulting expression is equal to 1 if every element of the two arrays are also equal in value.]{.span10}

[\<expression\_one\> \> \<expression\_two\> ]{.span11}[-- ]{.span10}[The resulting expression is equal to 1 if the value of ]{.span10}[expression\_one ]{.span6}[is greater than the value of ]{.span10}[expression\_two ]{.span6}[and equal to 0 otherwise.]{.span10}

[If either expression is of type ]{.span10}[roll ]{.span6}[then it will be evaluated to ]{.span10}[int ]{.span6}[before the comparison.]{.span10}

[If the expressions are both array expressions and the first array is larger than the second, then the resulting expression is equal to 1.]{.span10}

[\<expression\_one\> \< \<expression\_two\> ]{.span11}[-- ]{.span10}[The resulting expression is equal to 1 if the value of ]{.span10}[expression\_one ]{.span6}[is lesser than the value of ]{.span10}[expression\_two ]{.span6}[and equal to 0 otherwise.]{.span10}

[If either expression is of type ]{.span10}[roll ]{.span6}[then it will be evaluated to ]{.span10}[int ]{.span6}[before the comparison.]{.span10}

[If the expressions are both array expressions and the first array is ]{.span10}[s]{.span10}[maller]{.span10}[ than the second, then the resulting expression is equal to 1.]{.span10}

[\<expression\_one\> \>= \<expression\_two\> ]{.span11}[-- The resulting expression is equal to 1 if the value of ]{.span10}[expression\_one ]{.span6}[is greater than or equal to the value of ]{.span10}[expression\_two ]{.span6}[and equal to 0 otherwise.]{.span10}

[If either expression is of type ]{.span10}[roll ]{.span6}[then it will be evaluated to ]{.span10}[int ]{.span6}[before the comparison.]{.span10}

[If the expressions are both array expressions and the first array is larger than or the same size as the second, then the resulting expression is equal to 1.]{.span10}

[\<expression\_one\> ]{.span11}[\<]{.span11}[= \<expression\_two\> ]{.span11}[-- The resulting expression is equal to 1 if the value of ]{.span10}[expression\_one ]{.span6}[is lesser than or equal to the value of ]{.span10}[expression\_two ]{.span6}[and equal to 0 otherwise.]{.span10}

[If either expression is of type ]{.span10}[roll ]{.span6}[then it will be evaluated to ]{.span10}[int ]{.span6}[before the comparison.]{.span10}

[If the expressions are both array expressions and the first array is smaller than or the same size as the second, then the resulting expression is equal to 1.]{.span10}

[\<expression\_one\> && \<expression\_two\> ]{.span11}[-- The resulting expression is equal to 1 if the value of neither expression is 0 and 0 otherwise.]{.span10}

[\<expression\_one\> \|\| \<expression\_two\> ]{.span11}[-- The resulting expression is equal to ]{.span10}[0]{.span10}[ if the value of ]{.span10}[b]{.span10}[oth]{.span10}[ expression]{.span10}[s]{.span10}[ is 0 and ]{.span10}[1]{.span10}[ otherwise.]{.span10}

[Ternary Operations]{.span17}

[Ternary Conditional]{.span13}

[\<]{.span5}[condition]{.span5}[\>?\<if\_expression\>:\<else\_expression\> ]{.span5}[-- The resulting expression is equal to ]{.span8}[else\_expression ]{.span6}[if ]{.span10}[conditio]{.span6}[n]{.span6}[ is equal to 0, and ]{.span10}[if]{.span6}[\_expression ]{.span6}[otherwise.]{.span10}

[S]{.span17}[ections]{.span17}

[Scopes]{.span13}

[(]{.span5}[\<]{.span5}[expression]{.span5}[\>]{.span5}[)]{.span5}[ -- Evaluates the contents of ]{.span8}[expression ]{.span6}[before the rest of the expression ]{.span10}[it is inserted in]{.span10}[.]{.span10}

[\<]{.span11}[function\>(\<arguments\>) ]{.span11}[-- ]{.span10}[An argument is a]{.span10}[n expression whose type must be acceptable by the function]{.span10}[, and all arguments are separated by commas ]{.span10}[within ]{.span10}[arguments]{.span6}[.]{.span10}

[{\<expression\>} ]{.span11}[-- Every variable inside ]{.span10}[expression ]{.span6}[is invisible to the rest of the code. When in front of functions, defines the scope of those functions.]{.span10}

[\#]{.span11}[\<expression\> ]{.span11}[-- ]{.span10}[Preprocessing. More details further.]{.span10}

[Comments and Documentation]{.span13}

[//\<comment\> ]{.span5}[-- Everything written in ]{.span8}[comment]{.span6}[ up to the end of the line is ignored by the interpreter.]{.span10}

[/\*\<multi-line comment\>\*/]{.span11}[ -- Multi-line comment. Everything written in ]{.span10}[multi-line comment]{.span6}[ is ignored by the interpreter. ]{.span10}[The beginning (/\*) and end (\*/) of the comment may be in different lines.]{.span10}

[/\*\*]{.span11}[\<documentation\>\*/ ]{.span11}[-- Multi-line documentation. Markdown syntax. Every line ]{.span10}[in]{.span10}[ ]{.span10}[documentation]{.span6}[ must begin with an asterisk (\*) to be properly interpreted by the Markdown parser. ]{.span10}[Ignored by the interpreter.]{.span10}

[Constants]{.span9}

[null ]{.span5}[-- Declared variables that are not initialized, empty arrays and undefined expressions have their value equal to ]{.span8}[null]{.span6}[.]{.span10}

[infinity ]{.span11}[-- A ]{.span10}[frac ]{.span6}[whose denominator is equal to 0 and whose nominator is positive ]{.span10}[i]{.span10}[s displayed as ]{.span10}[infinity]{.span6}[.]{.span10}

[neg\_infinity ]{.span11}[-- ]{.span10}[ ]{.span10}[A ]{.span10}[frac ]{.span6}[whose denominator is equal to 0 and whose nominator is ]{.span10}[displayed]{.span10}[ ]{.span10}[neg\_infinity]{.span6}[.]{.span10}

[nan ]{.span11}[-- A ]{.span10}[frac ]{.span6}[whose both nominator and denominator is equal to 0.]{.span10}

[Functions]{.span9}

[Conditional]{.span13}

[if(\<condition\>) \<if\_]{.span5}[scope]{.span5}[\>]{.span5}[ ]{.span15}[else ]{.span18}[\<else\_scope\>]{.span18}[ ]{.span15}[-- Evaluates ]{.span8}[if\_scope]{.span6}[ ]{.span6}[if ]{.span10}[condition ]{.span6}[is not equal to 0, otherwise evaluates ]{.span10}[else\_scope]{.span6}[.]{.span10}

[Loops]{.span13}

[while(\<condition\>) ]{.span5}[\<loop\_scope\>]{.span5}[ ]{.span5}[-- Loops through ]{.span8}[loop\_]{.span6}[scope]{.span6}[ ]{.span6}[if ]{.span10}[condition ]{.span6}[is not equal to 0.]{.span10}

[for(\<initial\_expression\>;\<condition\>;\<final\_expression\>) ]{.span11}[\<]{.span11}[loop\_scope\>]{.span11}[ -- Evaluates ]{.span10}[initial\_expression]{.span6}[, then if ]{.span10}[condition]{.span6}[ is not equal to 0, loops through ]{.span10}[loop\_]{.span6}[scope]{.span6}[, and finally evaluates ]{.span10}[final\_expression]{.span6}[.]{.span10}

[break;]{.span11}[ -- ]{.span10}[Immediately breaks out of the loop scope, if in one.]{.span10}

[continue; ]{.span11}[-- Immediately finishes the current loop ]{.span10}[evaluation]{.span10}[, skipping to the next.]{.span10}

[Functions]{.span13}

[\<type\>]{.span5}[ \<name\>(]{.span5}[\<arguments\>]{.span5}[) {\<function\_scope\>} ]{.span5}[-- Defines a scope that may be called by ]{.span8}[name ]{.span6}[within the program. ]{.span10}[The function ]{.span10}[must ]{.span10}[resolve to a variable of type ]{.span10}[type]{.span6}[. ]{.span10}[Every argument inside ]{.span10}[arguments ]{.span6}[is a ]{.span10}[\<type\> \<arg\_name\> ]{.span11}[double that defines the type of each argument and the name for the argument that the function will use internally.]{.span10}

[return \<expression\>; ]{.span11}[-- Immediately breaks out of the function's scope, evaluating the function's expression to ]{.span10}[expression]{.span6}[.]{.span10}

[except \<int\>; ]{.span11}[-- Immediately breaks out of the program, printing an error code to the console.]{.span10}

[Built-in Functions]{.span13}

[int ]{.span5}[mcm(int a, int b) ]{.span5}[-- Returns an ]{.span8}[int]{.span6}[ equal to the ]{.span10}[minimum]{.span10}[ common multiplier of ]{.span10}[a]{.span6}[ and ]{.span10}[b]{.span6}[.]{.span10}

[int ]{.span11}[mcd(int a, int b)]{.span11}[ -- Returns an ]{.span10}[int ]{.span6}[equal to the maximum common divider of ]{.span10}[a ]{.span6}[and ]{.span10}[b]{.span6}[.]{.span10}

[\<int/frac\> ]{.span5}[abs(]{.span5}[\<]{.span5}[int/frac\> ]{.span5}[input]{.span11}[) ]{.span5}[-- Returns the absolute value of ]{.span8}[i]{.span6}[nput]{.span6}[.]{.span10}

[\<type\> ]{.span11}[min(\<expression\_one\>, \<expression\_two\>) ]{.span11}[-- Returns whichever of the given expressions is ]{.span10}[smaller]{.span10}[.]{.span10}

[int ]{.span11}[min(]{.span11}[roll input]{.span11}[) ]{.span11}[-- Returns ]{.span10}[an ]{.span10}[int ]{.span6}[equal to ]{.span10}[the minimum possible value of ]{.span10}[i]{.span6}[nput]{.span6}[.]{.span10}

[\<type\> ]{.span11}[min(]{.span11}[\<]{.span11}[type\>\[\] input]{.span11}[) ]{.span11}[-- Returns whichever element of ]{.span10}[i]{.span6}[nput]{.span6}[ ]{.span6}[is the smallest.]{.span10}

[\<type\> ]{.span11}[max(\<expression\_one\>, \<expression\_two\>) ]{.span11}[-- Returns whichever of the given expressions is larger.]{.span10}

[int ]{.span11}[max(]{.span11}[r]{.span11}[oll input]{.span11}[)]{.span11}[ -- Returns ]{.span10}[an]{.span10}[ int]{.span6}[ equal to]{.span10}[ the maximum possible value of ]{.span10}[i]{.span6}[nput]{.span6}[.]{.span10}

[\<type\> ]{.span11}[max(]{.span11}[\<]{.span11}[type\>\[\] input]{.span11}[) ]{.span11}[-- Returns whichever element of ]{.span10}[i]{.span6}[nput]{.span6}[ is the largest.]{.span10}

[\<type\>\[\] ]{.span11}[sort(]{.span11}[\<type\>\[\] input]{.span11}[) ]{.span11}[-- Sorts and returns ]{.span10}[i]{.span6}[nput]{.span6}[.]{.span10}

[\<type\>\[\] ]{.span11}[r]{.span11}[educe(\<type\>\[\] input) ]{.span11}[-- Returns]{.span10}[ input ]{.span6}[without repeated elements.]{.span10}

[frac ]{.span11}[avg(\<int/frac\> ]{.span11}[n\_0]{.span11}[, \<int/frac\> ]{.span11}[n\_]{.span11}[1]{.span11}[)]{.span11}[ -- Returns a ]{.span10}[frac ]{.span6}[equal to the average of two numbers, (]{.span10}[n\_]{.span6}[0]{.span6}[+]{.span10}[n\_]{.span6}[1]{.span6}[)/2.]{.span10}

[frac ]{.span11}[mean(]{.span11}[\<t]{.span11}[y]{.span11}[pe\>\[\] input]{.span11}[) ]{.span11}[-- Returns ]{.span10}[a]{.span10}[ frac]{.span6}[ equal to]{.span10}[ ]{.span6}[the mean value of ]{.span10}[i]{.span6}[nput]{.span6}[.]{.span10}

[frac ]{.span11}[mean(]{.span11}[roll input]{.span11}[)]{.span11}[ -- Returns ]{.span10}[a ]{.span10}[frac ]{.span6}[equal to ]{.span10}[the mean value of ]{.span10}[i]{.span6}[nput]{.span6}[, the average between its max and min values.]{.span10}

[frac ]{.span11}[median(roll input) ]{.span11}[-- Returns ]{.span10}[a ]{.span10}[frac]{.span6}[ equal to the median value of ]{.span10}[input]{.span6}[.]{.span10}

[frac ]{.span11}[expected(]{.span11}[r]{.span11}[oll input]{.span11}[)]{.span11}[ -- Returns ]{.span10}[a]{.span10}[ frac]{.span6}[ equal to]{.span10}[ ]{.span6}[the expected value of ]{.span10}[i]{.span6}[nput]{.span6}[. The expected value of a roll is calculated by the sum of all results weighted by their likelihood.]{.span10}

[int\[\] ]{.span11}[all(]{.span11}[r]{.span11}[oll input]{.span11}[) ]{.span11}[-- Returns an ]{.span10}[i]{.span6}[nt]{.span6}[ ]{.span6}[array containing all values ]{.span10}[i]{.span6}[nput]{.span6}[ takes, ]{.span10}[sorted.]{.span10}

[int\[\] ]{.span11}[possible(roll input) ]{.span11}[-- Returns an ]{.span10}[int ]{.span6}[array containing all values ]{.span10}[input ]{.span6}[can take. It is functionally ]{.span10}[equal to ]{.span10}[reduce(all(input))]{.span6}[.]{.span10}

[int\[\] each(\<roll\>) ]{.span11}[-- Returns an array with the result of each dice of an arbitrary generation of ]{.span10}[roll]{.span6}[, in order of appearance. Modifiers are applied only to the last dice. The size of this array ]{.span10}[is not deterministic ]{.span10}[and depends]{.span10}[ on the modifiers. ]{.span10}[Example: (1d4)d6 can have anywhere between 2 and 5 dies, one d4 and at least 1d6 up to 4d6.]{.span6}

[int\[\]\[\] every(\<roll\>) ]{.span11}[-- Returns a 2-dimensional array with every possible result of the dies of ]{.span10}[roll]{.span6}[. ]{.span10}[WARNING: The array has the potential to get very large very quickly. Make sure ]{.span11}[roll]{.span15}[ does not contain many dies.]{.span11}

[frac\[\] ]{.span11}[odds(roll input) ]{.span11}[-- Returns a ]{.span10}[frac]{.span6}[ array containing the odds of ]{.span10}[input]{.span6}[, in the order of ]{.span10}[possible(input)]{.span6}[.]{.span10}

[frac ]{.span11}[chance(int val, roll gen) ]{.span11}[-- Returns a]{.span10}[ frac]{.span6}[ equal to]{.span10}[ ]{.span6}[the chance that ]{.span10}[gen ]{.span6}[will generate the value ]{.span10}[val]{.span6}[. If ]{.span10}[gen]{.span6}[ cannot generate ]{.span10}[val]{.span6}[, returns ]{.span10}[0/1.]{.span10}

[\<type\> read(\<type\> input) ]{.span11}[-- Returns input from the user via console. Waits for input before continuing.]{.span10}

[void print(\<expression\>) ]{.span11}[-- Prints the value of ]{.span10}[expression ]{.span6}[to the console, ]{.span10}[followed by a new line.]{.span10}

[\<type\>\[\] push(\<type\>\[\] array, \<type\> element) ]{.span11}[-- Adds ]{.span10}[element ]{.span6}[to the end of ]{.span10}[array]{.span6}[ and returns the modified array.]{.span10}

[\<type\>\[\] insert(\<type\>\[\] array, \<type\> element, int index)]{.span11}[ -- Adds ]{.span10}[element ]{.span6}[to ]{.span10}[array]{.span6}[ at ]{.span10}[index]{.span6}[, pushing elements of higher index forward. Returns the modified array.]{.span10}

 

[Order of Operations]{.span4}

----------------- ----------------------------------------------------------------------------- ---------------------------------------------------------------------------------------
  [Order]{.span5}   [Operation]{.span5}                                                           [Syntax]{.span5}
  [1]{.span3}       [Expression scope]{.span3}                                                    [(\<expression\>)]{.span3}
  [2]{.span3}       [Division]{.span3}                                                            [\<expression\>/\<expression\>]{.span3}
  [3]{.span3}       [Dice]{.span3}                                                                [\<]{.span3}[exp]{.span3}[\>d\<exp\>]{.span3}[\<op\>\<exp\>]{.span3}
  [4]{.span3}       [Negation / ]{.span3}[Multiplication / ]{.span3}[Remainder]{.span3}           [-]{.span3}[\<exp\> / ]{.span3}[\<exp\>\*\<exp\> / ]{.span3}[\<exp\>%\<exp\>]{.span3}
  [5]{.span3}       [Addition / Subtraction]{.span3}                                              [\<exp\>+\<exp\> / \<exp\>-\<exp\>]{.span3}
  [6]{.span3}       [Logical ]{.span3}[n]{.span3}[egation]{.span3}                                [!\<expression\>]{.span3}
  [7]{.span3}       [Logical ]{.span3}[b]{.span3}[inary ]{.span3}[o]{.span3}[perations]{.span3}   [\<exp\>\<op\>\<exp\>]{.span3}
  [8]{.span3}       [Ternary ]{.span3}[c]{.span3}[onditional]{.span3}                             [\<cond\>? \<exp\>: \<exp\>]{.span3}
----------------- ----------------------------------------------------------------------------- ---------------------------------------------------------------------------------------

 

[]{#section0005.xhtml}

[Preprocessing]{.span2}

[Functions]{.span4}

[import(\<path\>) ]{.span5}[-- Imports the source code of the file in ]{.span8}[path]{.span6}[ into this file. The interpreter will first parse every imported file in order before parsing this file.]{.span10}

[define \<constant\> = \<value\> ]{.span11}[-- Defines ]{.span10}[constant]{.span6}[ to a value, such that every occurrence of ]{.span10}[constant ]{.span6}[in this file is replaced by ]{.span10}[valued ]{.span6}[before parsing. ]{.span10}[constant ]{.span6}[must be written entirely in uppercase.]{.span10}

[encoding(\<enc\_name\>) ]{.span11}[-- Defines the encoding for this file. ]{.span10}[enc\_name ]{.span6}[can be either one of the following: ascii, utf8, ]{.span10}[more to be added.]{.span19}

[]{#section0006.xhtml}

[D]{.span20}[ebugging]{.span20}

[Run-time Exceptions]{.span12}

-------------------- ------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [Code]{.span5}       [Name]{.span5}                        [Description]{.span5}
  [0x000000]{.span3}   [Arbitrary Stop]{.span3}              [This exception code is an arbitrary stop to be thrown by the user.]{.span3}
  [0x000001]{.span3}   [Array Index out of Bounds]{.span3}   [This exception code is thrown if an array is accessed with an index that is either larger or equal to its size, or if the given index is negative.]{.span3}
  [0x000002]{.span3}   [Null Pointer]{.span3}                [This exception is thrown if arithmetic is attempted with the ]{.span3}[null]{.span5}[ constant.]{.span8}
  [0x000003]{.span3}   [Invalid Cast]{.span3}                [This exception is thrown if an expression is cast to a type which is not described. A few examples are]{.span3}[ 2-dimensional array to a 1-dimensional array and ]{.span16}[roll ]{.span7}[to ]{.span16}[frac]{.span7}[.]{.span16}
  [0x000004]{.span3}   [Type Mismatch]{.span3}               [This exception is thrown if an expression is of a different type than it should be. ]{.span3}[Usually caught by the interpreter.]{.span3}
  [0x000005]{.span3}   [Invalid Dice]{.span3}                [This exception is thrown if ]{.span3}[any of the expressions in a dice is invalid. A dice cannot have a negative number of faces or be filtered through a negative number.]{.span3}
-------------------- ------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

[Interpreter ]{.span4}[Exceptions]{.span12}

[Every exception thrown by the interpreter points exactly ]{.span3}[to where the error was caught, for ease of correction.]{.span3}

---------------------- ------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [Code]{.span5}         [Name]{.span5}                  [Description]{.span5}
  [0x00000000]{.span3}   [Syntax Error]{.span3}          [Thrown by the interpreter if any syntactical rule is broken. These rules can be invalid symbol placement, not finishing a line with semi-colons, improper scope closing, etc.]{.span3}
  [0x000001]{.span3}     [Type Mismatch]{.span3}         [Thrown by the interpreter if a variable is initialized to ]{.span3}[a value of]{.span3}[ improper ]{.span3}[type]{.span3}[, if a function returns a value of improper type or if an expression expected to be of a specific type is of another type.]{.span3}
  [0x000002]{.span3}     [Invalid Path]{.span3}          [Thrown by the interpreter in the preprocessing phase. If the path is invalid or does not point to a DiceCode source code file then it is considered invalid.]{.span3}
  [0x000003]{.span3}     [Preprocessing Error]{.span3}   [Thrown by the interpreter if there is any syntactical error inside preprocessor code.]{.span3}
---------------------- ------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

[]{#section0007.xhtml}

[S]{.span20}[ample]{.span20}[ Program]{.span2}

[// This is a program that automates ]{.span21}[and analyses ]{.span21}[D&D 5e stats]{.span21}

[int\[6\] stats;]{.span21}

[int\[6\] ]{.span21}

[roll stat\_roll = 4d6l3;]{.span21}

[for(int t = 0; t \< 6; t++) ]{.span21}[stats\[t\] = roll;]{.span21}

 
