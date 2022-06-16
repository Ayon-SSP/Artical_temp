
Multiple Decoraters to a single function is called chaning of decoraters
```
@make_Borders
@make_Style
def DisplayName():
    return Str
```



Let's understand 

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

In this above code we can understand that how Multiple Decoraters are helping to change the functionality 