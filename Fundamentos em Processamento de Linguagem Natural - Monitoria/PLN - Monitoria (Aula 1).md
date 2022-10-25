<meta charset="utf-8">
<p>Aula 1<br />
(23-09-2022)<br />
<br />
Exercícios<p>

<meta charset="utf-8">
<p>1. Escreva um programa que imprima na consola o seguinte:<br />
Olá, Mundo!</p>


```python
-*- coding: UTF-8 -*-
print("Hello World!")
```


      File "/tmp/ipykernel_86726/3290390855.py", line 1
        -*- coding: UTF-8 -*-
         ^
    SyntaxError: invalid syntax



<meta charset="utf-8">
<p>2. Escreva um programa que imprima na consola o seguinte:<br />
<br />
#<br />
##<br />
###<br />
####<br />
#####<br /></p>


```python
# with simple prints
x = "#"
print(f"{x}\n{x}{x}\n{x}{x}{x}\n{x}{x}{x}{x}\n{x}{x}{x}{x}{x}")
```

    #
    ##
    ###
    ####
    #####



```python
# with while
x = 0
y = "#"
while x < 5:
  print(y)
  x = x + 1
  y = y + "#"
```

    #
    ##
    ###
    ####
    #####


<meta charset="utf-8">
<p>3. Escreva um programa que imprima na consola o seguinte:<br />
<br />
##########<br />
#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#<br />
#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#<br />
#&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#<br />
##########</p>


```python
# with simple prints
y = "##########"
z = "#        #"
print(f"{y}\n{z}\n{z}\n{z}\n{y}")
```

    ##########
    #        #
    #        #
    #        #
    ##########


<meta charset="utf-8">
<p>4. Escreva um programa que leia da consola um nome e imprima uma saudação.<br />
Exemplo: se o nome inserido for Pedro, o programa deverá imprimir:<br />
Olá, Pedro!</p>


```python
x = input("Qual é o seu nome? ")
print(f"Olá, {x}!")
```

    Qual é o seu nome? Pedro
    Olá, Pedro!

