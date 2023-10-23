# Enigma Elysium
Most scuffed solution of Rev
## Category
**Reverse Engeneering**
## Points
**200**
## Challange Description
>Oops, I forgot to uncomment the print statement
## Attached File
[Rev_me](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Rev/Files/rev_me.out)
## Explanation
Tried running program in [dogbolt](https://dogbolt.org) got no results.
Opened the file in notepad and just went through the contents since its a possiblity that the print statement was not converted to binary since it was a comment and hence the flag just exists in it.
![OpenedBinary](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Rev/Files/Enigma%20Esylum%20Notepad.png)
here we can see `n1gm kc0 y5 d4r de{3 4_3l 1um}`. With some common sense we can rearrange this to `d4rkc0de{3n1gm4_3ly51um}`
## Flag
`d4rkc0de{3n1gm4_3ly51um}`
