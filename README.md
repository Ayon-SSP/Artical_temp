# Multiple Decorators in Python

In simple terms if a function has multiple decoraters we call it as chaning of decoraters or Multiple Decorators.
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



Let's understand Chaning of Decoraters using code

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
```GG = add_Borders(add_Style(DisplayName))
GG()
```

In this above code we can understand that how Multiple Decoraters are helping to change the functionality of a DisplayName() function twice first it's adding add_style  "<- plaintext ->" and then adding add_Borders " | plaintext | " & if need we can add more additional functionality to DisplayName() function.

<pre>
let's the base function be DisplayName()
step 1:
    First the base function wil pass as an argument to add_Style function and the text changest "TutorialsPoint" to "<-TutorialsPoint->"

step 2:
    Then the add_Style function will pass as an argument to add_Borders function and the text changest "<-TutorialsPoint->" to "|<-TutorialsPoint->|"
</pre>