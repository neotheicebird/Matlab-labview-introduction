title: LabView and Matlab - The beauty and the beast
author:
  name: Prashanth G
  email: neotheicebird@gmail.com
  url: http://github.com/neotheicebird
output: presentation.html
style: style.css
--
# Matlab and Labview
## An Introduction
--

###The Gameplan
The tutorial is going to run from 3:00pm to 6:15pm
* 3:00 to 3:45 - Basic intro to Matlab
* 3:45 to 4:15 - Quick view of some intermediate and advanced topics
* 4:15 to 4:30 - An interactive problem solving session
* 4:30 to 4:45 - Break

--

###The Gameplan

* 4:45 to 5:15 - Basic intro to Labview
* 5:15 to 5:45 - Event based programming
* 5:45 to 6:15 - An interactive problem solving session
* After that   - Go home and watch TV

--
###Which way does Matlab works best?
####There are many ways in which programming languages solve a problem:
* Procedural -- C, Pascal
* Declarative -- SQL
* Object-oriented -- Java
* Functional -- Haskell, ML family

--
###The Functional way
* Pure functions: `sin(x)`, `length(x)`
* Side effects - interaction with the outside world
    1. `pause(t)`, `rand()`
    2. Rarely used
* Opposite of Object-Oriented Programming - why?
    1. Objects are capsules containing states and methods that change states
    2. Funtional programming wants to avoid state changes

--
###The Functional way
Why do we want to avoid states and objects?
* Formal provability - I need a mathematical proof that your program works.
* Modularity - Break it into pieces
* Ease of debugging and testing - loose coupling, unit testing
* Composability - DRY (Don't repeat yourself)

--
###Variables
Numbers and matrices:
```matlab
A = 1; % all numbers are floating-point value

empty_list = [];

my_list = [1 5 2 4 3];

list_1 = 1:10; % : operator is used to make equidistant list of numbers

list_2 = zeros(4,5); % A 4x5 matrix of zeros

list_3 = ones(5); % A 5x5 matrix of ones

list_4 = 0:0.5:5;

list_5 = linspace(1,5,11)
```
--
###Variables
Strings:
```matlab
str = 'Hello, world';

blank_string = blanks(n); % a string which is n spaces

string_array = ['one  '; 'two  '; 'three']; % 2D array of chars
string_array =

one
two
three

concat_strings = ['Nice' 'day' 'right?'];
concat_strings = nicedayright?

concat_strings = strcat('remove  ', 'trailing   ', 'spaces   ');
concat_strings = 'removetrailingspaces'
```
--
###Variables
Cells:
```matlab
battery = {}; % a cell is a container which can hold any variable

happy_strings = {'one', 'two', 'three'}
happy_strings{2}
ans = two

cell_array = {'text', 2, [1 2 3], magic(3)}
cell_array =
{
  [1,1] = text
  [1,2] =  2
  [1,3] =
     1   2   3
  [1,4] =
     8   1   6
     3   5   7
     4   9   2
}
```
--
###Variables
Struct:
```matlab

```
--
###Arithmetic operations

<table style="width:800px">
<tr>
  <th>Symbol</th>
  <th>Function</th>
  <th>Operation</th>
</tr>
<tr>
  <td>+</td>
  <td>plus()</td>
  <td>Addition</td>
</tr>
<tr>
  <td>-</td>
  <td>minus()</td>
  <td>Subtraction</td>
</tr>
<tr>
  <td>*</td>
  <td>mtimes()</td>
  <td>Multiplication</td>
</tr>
<tr>
  <td>/</td>
  <td>rdivide()</td>
  <td>Division</td>
</tr>

<tr>
  <td>^</td>
  <td>power()</td>
  <td>Power</td>
</tr>
<tr>
  <td>.(operator)</td>
  <td></td>
  <td>Element-wise operation</td>
</tr>
</table>

--

###Arithmetic operations
```matlab
A = 1:5;
```
Sum of all elements:
```matlab
sum(A)
ans =  15
```
Cumulative sum:
```matlab
cumsum(A)
ans =
    1    3    6   10   15
```
--

###Arithmetic operations
```matlab
A = 1:5;
```
Product:
```matlab
prod(A)
ans =  120
```
Cumulative product:
```matlab
cumprod(A)
ans =
     1     2     6    24   120
```
--
###Relational operations

It is pretty much the same as any other languages. The operators are
`>`,`<`,`>=`,`<=`,`==`

Only operator that might be different is the NOT EQUAL operator:
`~=`
--
for loop -- or is it? Hmmm..

```matlab
for i = some_1D_matrix
    % for each element in the 1D matrix
    % Do something
end
```
--

for loop -- or is it? Hmmm..

```matlab
for i = some_1D_matrix
    % for each element in the 1D matrix
    % Do something
end
```

```matlab
for i = 1:10
    disp(i)
end
```
--

for loop -- or is it? Hmmm..

```matlab
for i = some_1D_matrix
    % for each element in the 1D matrix
    % Do something
end
```

```matlab
for i = 1:10
    disp(i)
end
```
```matlab
for i = linspace(1,10,1)
    disp(i)
end
```
--
### Zen of <s>Python</s> Matlab
>Beautiful is better than ugly.

>Explicit is better than implicit.

>Simple is better than complex.

>Complex is better than complicated.

--

### Zen of <s>Python</s> Matlab
>Flat is better than nested.

>Sparse is better than dense.

>Readability counts.

>Special cases aren't special enough to break the rules.

--

### Zen of <s>Python</s> Matlab

>Although practicality beats purity.

>Errors should never pass silently.

>Unless explicitly silenced.

>In the face of ambiguity, refuse the temptation to guess.

>There should be one-- and preferably only one --obvious way to do it.

--

### Zen of <s>Python</s> Matlab
>Although that way may not be obvious at first unless you're Dutch.

>Now is better than never.


>Although never is often better than *right* now.

>If the implementation is hard to explain, it's a bad idea.

>If the implementation is easy to explain, it may be a good idea.

>Namespaces are one honking great idea -- let's do more of those!


