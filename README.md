
```

```









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