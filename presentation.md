title: LabView and Matlab - The beauty and the beast
author:
  name: Prashanth G
  email: neotheicebird@gmail.com
  url: http://github.com/neotheicebird
output: index.html
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
# Introduction to Matlab -- Fundamentals
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
Structure:
```matlab
% create struct with specified fields and values
s = struct('field1', value1, 'field2', value2, ...)
s = struct % a 1x1 structure with no fields

s = struct('thing', {'ferrari', 'apple'}, 'color', {'red'})
s =

  1x2 struct array containing the fields:

    thing
    color

s(1) =

  scalar structure containing the fields:

    thing = ferrari
    color = red

```
--
###Variables
Structure
```matlab
s = struct('strings', {{'Hello', 'bye'}}, 'length', [5,3])
s.strings =
    'Hello'    'bye'

s.('length') =
    5    3

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
###Logical operations
AND `and(a,b)`, `&`
OR `or(a,b)` , `|`
NOT `not(a)` , `~`
XOR `xor(a,b)`

Short-ckt AND `&&`
short-ckt OR `||`.
Short-circuit behaviour are useful when some condiions are unknown

```matlab
compare = (exist('myfun.m') == 2) && myfun(x) > y
```
--
###If, else-if, else
```matlab
a = 4;
b = 4;
if (a<b)
    j = -1;
else if (a>b)
    j = 2;
else
    j = 3
end

weather = 'rainy';
if ((a<b) | (a>b)) & strcmp(weather, 'rainy')
    disp('Feels great!')
end
```
--
###I/O

Getting Inputs
```matlab
value_entered = input('Enter an number: ');

string_entered = input('Enter string: ', 's');
```
Display outputs:
```matlab
fav_num = input('What is your favourite number?')
fav_num % without a ';' the variable value gets displayed

disp(['User entered ', num2str(value_entered)])
```
--
###for loop -- or is it? Hmmm..

```matlab
for i = some_1D_matrix
    % for each element in the 1D matrix
    % Do something
end
```
--

###for loop -- or is it? Hmmm..

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

###for loop -- or is it? Hmmm..

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
```matlab
fibo_matrix = [1 1];
sequence_length = 10;
for i = 1:sequence_length
    fibo_matrix = [fibo_matrix, sum(fibo_matrix(end-1:end))];
end
disp(fibo_matrix)
     1     1     2     3     5     8    13    21    34    55    89   144
```
--
###While loop
```matlab
while condition
    % do something until condition not satisfied
end

tried = 0;
perfection = 1000;
while tried < perfection
    disp('try once more')
    tried = tried + 1;
end
```
--
###Break, continue, break, continue...
`break` is used to break a loop
```matlab
for i = 1:100
    disp(i)
    if i > 50
        break
    end
end
```
`continue` is used to skip a iteration
```matlab
for i = 1:20
    if mod(i, 3) ~= 0
        continue
    end
disp(i)
end
```
--
###File Handling

Some functions that come handy: `fopen()`, `fgetl()`, `textscan()`, `fclose()`.
```matlab
fid = fopen('wiki.txt', 'r');
try
    line = fgetl(fid);
    while ischar(line)
        disp(line)
        line = fgetl(fid);
    end
    % we can do more operations with the strings
catch err
    fclose(fid);
    rethrow(err);
end
```
--
###File Handling - functions
```matlab
% open a CSV file and read to a matrix
matrix = csvread('data_file.csv')
% If we want a filtered matrix
matrix = csvread('data_file.csv', 2, 0); % from row=3, col=1. (0 indexing)

% excel sheets can be read using xlsread
[num, txt, raw] = xlsread(filename);

% formatted text files can be easily parsed using textscan
C = textscan(fileID, 'format')
C = textscan(string, 'format')

str = '0.42 8.23 3.34 6.85';
C = textscan(str, '%3.1f %*1d'); % %*1d tells textscan to neglect last one d
C{1} =

    0.4000
    8.2000
    3.5000
    6.8000
```
--
###Plotting
There is a lot of plotting functions in Matlab
####plot(x, y)
```matlab
x = linspace(0, 2*pi, 100);
y = sin(x);
plot(x, y)
title('Plot of sin( x )')
xlabel('time')
ylabel('amplitude')
xlim([0 2*pi])
ylim([-1 1])
```
--
###Plotting
####plot(x, y) - multiple curves in one plot
```matlab
x = linspace(0, 5, 500);
y = exp(-x).*cos(2*pi*x);
y1 = exp(-x).*sin(-2*pi*x);

plot(x, y, 'ro', x, y1, 'b.')
```
--
###Plotting
####subplot(total_rows, total_cols, horiz_index)
```matlab
figure
subplot(2,2,1)
text(0.5, 0.5, 'subplot(2,2,1)')
subplot(2,2,2)
text(0.5, 0.5, 'subplot(2,2,2)')
subplot(2,2,3)
text(0.5, 0.5, 'subplot(2,2,3)')
```
--
###Plotting
####3D plots
```matlab
[x,y] = meshgrid([-2:.2:2]) % make a 2D plane
Z = x.*exp(-x.^2 - y.^2); % Z is a surface

figure
surf(x, y, Z, gradient(Z)) % surface plot with gradient Z

colorbar % color scale
```
Alternatives: `mesh()`, `imagesc`, `plot3()`
--
# Let's solve a problem
## word statistics
--
# Intermediate and Advanced topics
## Lets' dig deeper
--
###How to write functions?
```matlab
function result = my_function(param1, param2)
    % What should the function do?
return
```
All functions need to be placed in their own file.

```matlab
function prime_number = next_prime(number)
    % find the next prime_number
return
```
--
###How to write functions?
```matlab
% we can evaluate a function using its handle
fhandle = @my_function; % just use @ symbol

% to make function from string
fhandle = str2func('my_function')

% to evaluate the function
output = feval(@fhandle, param1, param2);
```
--
###Indexing and more magic tricks
```matlab
A = 6:10;
% we probably know this
A([3 5]) =
    8  10
A([2:4]) =
    7  8  9

A = magic(3);
A =
    8  1  6
    3  5  7
    4  9  2
% linear indexing - This is fun
A(4) = 1 % What does that mean?

% logical indexing
B = logical( [1 0 0; 0 1 0; 0 0 1]);
A(B) =
    8
    5
    2
```
--

