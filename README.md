# Multiple Decorators in Python

##### Before going to Multiple Decorators let’s first understand what is Decorators

## Decorators in Python

Decorators are used to change the functionality of a function without modifying the actual function by taking the function as an argument.
### code structure for Decorators in python

```
@Dec_1
def A_funk():
    # functionality
    return If_Needed_to_return
A_funk()

```

### Code explanation :-
```
def Add_Style(funk):                  # step 2  funk -> DisplayName
    def inner():                      # step 4
        print("<-",end="")            #step 5
        funk()                        #step 6 call to funk() -> displayName() function
        print("->",end="")            #step 9
    return inner                      # step 3 inner function will call


def DisplayName():           # step 7
    print("TutorialsPoint",end="")   # step 8

gg = Add_Style(DisplayName)    # step 1: Add_Style function will take DisplayName function as an argument
gg() 

# -or- 
# Add_Style(DisplayName)()

```
### Let’s take an example where we use decorators:
The DisplayNamefunction will pass as an argument to the add_Style function and the text changest "TutorialsPoint" to "<-TutorialsPoint->"
```python
def Add_Style(funk):
    def inner():
        print("<-",end="")
        funk()
        print("->",end="")
    return inner

@Add_Style
def DisplayName():
    print("TutorialsPoint",end="")

DisplayName()
```


```
<-TutorialsPoint->
```

### Where to use decorators (with an example):
#### If decorators are not used :-
```python
import time
def funk1():
    start_time = time.time()

    # A big Task which may be any code that takes some time
    print("funk1() Task is Done")

    end_time = time.time()
    print(f"The time taken by this function is {(end_time - start_time) * 1000} Milli Second")

def funk2():
    start_time = time.time()

    # A big Task which may be any code that takes some time
    print("funk2() Task is Done")

    end_time = time.time()
    print(f"The time taken by this function is {(end_time - start_time) * 1000} Milli Second")

def funk3():
    start_time = time.time()

    # A big Task which may be any code that takes some time
    print("funk3() Task is Done")

    end_time = time.time()
    print(f"The time taken by this function is {(end_time - start_time) * 1000} Milli Second")
funk1()
funk2()
funk3()
```

In the above code, you can see that we are repeating the code in every function to calculate the time taken by a function.

To reduce the repetitive task we use Decorators.

### Now using Decorators in python
```python
import time

def time_taken(funk):
    def inner():
        start_time = time.time()
        funk()
        end_time = time.time()
        print(f"The time taken by this function is {(end_time - start_time) * 1000} Milli Second")
    return inner

@time_taken
def funk1():
    # A big Task which may be any code that takes some time
    print("funk1() Task is Done")

@time_taken
def funk2():
    # A big Task which may be any code that takes some time
    print("funk2() Task is Done")

@time_taken
def funk3():
    # A big Task which may be any code that takes some time
    print("funk3() Task is Done")

funk1()
funk2()
funk3()

```


Now, No need to repeat the code in every function to calculate the time taken by a function.


## Multiple Decorators in Python


In simple terms, If a function has multiple decorators we call it as chain of function decorators.<br>

#### code structure for Multiple Decorators in python
```
@Dec_1
@Dec_2
@Dec_3
@Dec_4
.
.
.

def A_funk():
    # functionality
    return If_Needed_to_return
A_funk()
```

#### Let's understand Chaining of Decorators with an example:
**With two decorators**<br>
@add_Borders<br>
@add_Style<br>
```python
def add_Borders(funk):
    # This function will take add_Style function as an argument
    # add_Style -> funk
    def inner():
        print("|",end="")
        funk()
        print("|",end="")
    return inner
def add_Style(funk):
    # This function will take DisplayName function as an argument
    # DisplayName -> funk

    def inner():
        print("<-",end="")
        funk()
        print("->",end="")
    return inner
@add_Borders
@add_Style
def DisplayName():
    # function which will display "TutorialsPoint"
    print("TutorialsPoint",end="")

# GG = add_Borders(add_Style(DisplayName))
# GG()

DisplayName()
```
Output: -
```
|<-TutorialsPoint->|
```
We can also use:
```
GG = add_Borders(add_Style(DisplayName))
GG()
```
#### Another example in which we are returning the strings : 
```python
def add_Borders(funk):
    def inner():
        return "|" + funk() + "|"
    return inner
def add_Style(funk):

    def inner():
        return "<-" + funk() + "->"
    return inner
@add_Borders
@add_Style
def DisplayName():
    return "TutorialsPoint"

print(DisplayName())
```
**Explanation :** <br><br>
The Decorator execution order is from bottom to top for example in our case @add_Style to @add_Borders<br>
let's the base function be DisplayName()<br><br>
**step 1:**
First the base function will pass as an argument to the add_Style function and the text changest "TutorialsPoint" to "<-TutorialsPoint->"<br>
**step 2:**
Then the add_Style function will pass as an argument to add_Borders function and the text changest "<-TutorialsPoint->" to "|<-TutorialsPoint->|"<br>
**step3:** 
it will print "|<-TutorialsPoint->|"

In this above code we can understand that how Multiple Decorators are helping to change the functionality of a DisplayName() function twice first it's adding add_style  "<- plaintext ->" and then adding add_Borders " | plaintext | " & if needed we can add more additional functionality to DisplayName() function.




There is a builtin standard library called inspect module in Python where we can use getsource() method to display the source code of any python object 
