# Multiple Decorators in Python

In simple terms, If a function has multiple decorators we call it as chain of function decorators.<br>
**Prerequisites Decorators in python**
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

#### Let's understand Chaning of Decorators with an example :
**With two decorators**<br>
@add_Borders<br>
@add_Style<br>
```
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
    #  DisplayName -> funk

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
```
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
