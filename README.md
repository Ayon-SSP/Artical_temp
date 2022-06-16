# Multiple Decorators in Python



In simple terms if a function has multiple decoraters to a single function we call it as chaning of decoraters.
code structure
```
@Dec_1
@Dec_2
@Dec_3
@Dec_4
.
.
.
def A_funk():

```



Let's understand Chaning of Decoraters using code

```
def Borders(funk):
    # This function will take Style function as an argument
    # Style -> funk
    def inner():
        print("|",end="")
        funk()
        print("|",end="")
    return inner
def Style(funk):
    # This function will take DisplayName function as an argument
    #  DisplayName -> funk

    def inner():
        print("<-",end="")
        funk()
        print("->",end="")
    return inner
@Borders
@Style
def DisplayName():
    # function which will display "TutorialsPoint"
    print("TutorialsPoint",end="")

# GG = Borders(Style(DisplayName))
# GG()

DisplayName()
```
Output: -
```
|<-TutorialsPoint->|
```

In this above code we can understand that how Multiple Decoraters are helping to change the functionality of a DisplayName() function twice first it's adding style  "<- plaintext ->" and then adding Borders " | plaintext | " 




