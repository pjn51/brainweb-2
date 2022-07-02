*Quines are programs that return their own source code.* This is surprisingly difficult. For example, here's a quine in [[Python]]:

```python
_='_=%r;print (_%%_)';print (_%_)
```

If we execute this as a program, it will return this exact line of code. 

There's even such thing as a *polyquine,* which is a quine that prints it own source code in multiple languages!

```
#include/*

s='''*/<stdio.h>

main(){char*_;/*==;sub _:lvalue{$_}<<s;#';<<s#'''

def printf(a,*b):import sys;sys.stdout.write(a%b),

s

#*/

_=" #include/*%cs='''*/<stdio.h>%cmain(){char*_;/*==;sub _:lvalue{%c_}<<s;#';<<s#'''%cdef printf(a,*b):import sys;sys.stdout.write(a%%b),%cs%c#*/%c_=%c%s%c;printf(_,10,10,36,10,10,10,10,34,_,34,10,10,10,10);%c#/*%cs='''*/%c}//'''#==%c";printf(_,10,10,36,10,10,10,10,34,_,34,10,10,10,10);

#/*

s='''*/

}//'''#==
```

The above code will print its own source code in Python, C, PHP, Perl, and Ruby. See [here](https://github.com/2KAbhishek/polyquine) for the repo. 

There's even something called `quine_relay`, which is a ruby program, that creates a rust program, and so on. There are 128 languages involved, and it just goes around in a circle again and again. 

#idea/compsci 

---
```dataview
LIST
FROM [[Quines are programs that return their own source code]] AND -outgoing([[Quines are programs that return their own source code]])
```