<p>Aula 2 - Geração de um ficheiro a partir de inputs<br />
<br />
Exercícios<p>

<p>1. Criar um programa gerador.py que lê do terminal um título, um autor e um ano de publicação, e de seguida imprime os valores lidos de acordo com um formato.<br />
<br />
O que fazer:<br />
    
_Correr o programa_
    
&emsp;python3 gerador.py

_deverá pedir os seguintes inputs (os valores passados são exemplos),_
    
Insira um título: A Mensagem<br />
Insira o autor: Fernando Pessoa<br />
Insira a data da publicação: 1934/12/01<br />
    
_e de seguida deverá imprimir o seguinte,_

titulo: A Mensagem<br />
autor: Fernando Pessoa<br />
data: 1934/12/01<br />
</p>


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ")

print(f"\nTítulo: {x}\nAutor: {y}\nData: {z}")
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01
    
    Título: A Mensagem
    Autor: Fernando Pessoa
    Data: 1934/12/01


<p>2. O texto que imprimimos no exercício anterior está escrito no formato <strong>YAML</strong>. Para além do <strong>YAML</strong>, existem outros formatos, como o <strong>JSON</strong> ou o <strong>XML</strong>. Acrescente ao programa  <i>gerador.py</i>  a possibilidade de escolhermos em que formato <strong>(YAML ou JSON)</strong> é que queremos imprimir o conteúdo final.

O que fazer:

Para além dos inputs que já passávamos no exercício anterior, vamos acrescentar um novo input que definirá o formato do texto final.

_Insira o formato: ..._

<strong>Se</strong> o formato for o YAML, <strong>então</strong> o texto continuará a ser:

titulo: A Mensagem <br />
autor: Fernando Pessoa<br />
data: 1934/12/01<br />

<strong>Senão</strong>, no caso de ser JSON, deverá imprimir:

{<br />
&emsp;&emsp;"titulo": "A Mensagem",<br />
&emsp;&emsp;"autor": "Fernando Pessoa",<br />
&emsp;&emsp;"data": "1934/12/01"<br />
}</p>


```python
# \' Escape for Single Quote
# \   \ Escape
# \t TAB
# {{ Escape for Brackets 

x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ")

a = input("Formato final (YAML ou JSON): ").upper() #define o formato
if a == "YAML": 
    print(f"\nTítulo: {x}\nAutor: {y}\nData: {z}") #formato se YAML
elif a == "JSON":
    print(f"\n {{\n\t\"Título\": \"{x}\",\n\t\"Autor\": \"{y}\",\n\t\"Data\": \"{z}\"\n }}") #formato se JSON
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01
    Formato final (YAML ou JSON): json
    
     {
    	"Título": "A Mensagem",
    	"Autor": "Fernando Pessoa",
    	"Data": "1934/12/01"
     }


<p>3. Atualize o gerador.py de forma a poder especificar um ficheiro para guardar o texto que gera.<br />

<strong>O que fazer:</strong>

Acrescentar um novo <i>input</i> ao programa.

<i>Insira o nome do ficheiro onde quer guardar o resultado: ...</i>
    
Por exemplo, imaginemos que o nome do ficheiro introduzido foi <i>mensagem</i>. 

Se o formato for YAML, o programa deverá criar um ficheiro chamado <i>mensagem.yml</i>.<br />
Se for JSON, o ficheiro deverá chamar-se <i>mensagem.json</i>.</p>


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ")

a = input("Formato final (YAML ou JSON): ").upper()
b = input("Nome do ficheiro: ") #recebe nome do ficheiro
if a == "YAML":
    c = str(f"Título: {x}\nAutor: {y}\nData: {z}")
    print(c)
    ficheiro = open(f'{b}.yaml', 'w') #cria e nomeia o ficheiro com extensão [.yaml]
    ficheiro.write(c) #escreve no ficheiro o conteúdo da variável c
    ficheiro.close() #fecha e salva o ficheiro
elif a == "JSON":
    c = str(f" {{\n\t\"Título\": \"{x}\",\n\t\"Autor\": \"{y}\",\n\t\"Data\": \"{z}\"\n }}")
    print(c)
    ficheiro = open(f'{b}.json', 'w') #cria e nomeia o ficheiro com extensão [.json]
    ficheiro.write(c) #escreve no ficheiro o conteúdo da variável c
    ficheiro.close() #fecha e salva o ficheiro
```

<p><strong>Extra</strong><br /> 
<br /> 
1. Alguns parâmetros podem ser opcionais, i.e. o utilizador pode decidir não escrever nada. Por exemplo,<br /> 

&emsp;&emsp;- se o utilizador não passar nenhuma data, não queremos colocar o campo <i>data</i> no resultado final;<br /> 


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ") #recebe data

a = input("Formato final (YAML ou JSON): ").upper()
b = input("Nome do ficheiro: ")
if a == "YAML": #(se) o formato é YAML...
    if z == "":  #...e (se) a variável data vazia
        c = str(f"Título: {x}\nAutor: {y}") #não temos data no script
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else: #(caso contrário) se a variável data não for vazia...
        c = str(f"Título: {x}\nAutor: {y}\nData: {z}") #temos data no script
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
# elif a == "JSON": #mesma estrutura acima
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 
    Formato final (YAML ou JSON): yaml
    Nome do ficheiro: mensagem
    Título: A Mensagem
    Autor: Fernando Pessoa


&emsp;&emsp;- caso não passe nenhum formato, o programa deverá assumir o formato YAML por <i>default</i>;<br /> 


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ") 

a = input("Formato final (YAML ou JSON): ").upper()
b = input("Nome do ficheiro: ")
if a == "YAML" or a == "": #(se) o formato for YAML ou vazio ("") executa-se este script
    if z == "":
        c = str(f"Título: {x}\nAutor: {y}") 
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else: 
        c = str(f"Título: {x}\nAutor: {y}\nData: {z}") 
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
```

<p>&emsp;&emsp;- se não passar nenhum nome de ficheiro, o programa deverá utilizar o título da obra como nome do ficheiro resultante;<br /></p> 


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ") 

a = input("Formato final (YAML ou JSON): ").upper()
b = input("Nome do ficheiro: ")
if b == "": #(se) o ficheiro não receber nenhum valor/nome...
    b = x #...o nome do ficheiro passará a ter o valor/nome da variável x(título)
if a == "YAML" or a == "": 
    if z == "":
        c = str(f"Título: {x}\nAutor: {y}") 
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else: 
        c = str(f"Título: {x}\nAutor: {y}\nData: {z}") 
        print(c)
        ficheiro = open(f'{b}.yaml', 'w')
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01


<p>&emsp;&emsp;- o título e o autor deverão ser obrigatórios. Isto é, caso o utilizador não passe um ou outro, o programa deverá imprimir <br /> uma mensagem de erro (por exemplo: <i>ERRO: Título não pode ser vazio!</i>) e parar.<br /></p>


```python
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ")
if x == "" or y == "": 
    print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
```

    Insira um título: 
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01
    ERRO: os campos 'título' e 'autor' não podem ser vazios.


<p>Melhore o <i>gerador.py</i> de forma a que consiga lidar com <i>inputs</i> inválidos ou incompletos.</p>


```python
while True: #(enquanto) este loop/script não se encerrar
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    z = input("Insira a data da publicação: ")
    if x == "" or y == "": #(se) 'título' ou 'autor' forem vazios...
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")#...imprime esta mensagem...
        continue #...e repete este loop/script
    else: #(caso contrário)
        break #encerra este loop/script
```

    Insira um título: A Mensagem
    Insira o autor: 
    Insira a data da publicação: 1934/12/01
    ERRO: os campos 'título' e 'autor' não podem ser vazios.
    Insira um título: 
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01
    ERRO: os campos 'título' e 'autor' não podem ser vazios.
    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01


<p>2. Implemente também o formato XML.<br />
<br />
<i>mensagem.xml</i>

<obra data="1934/12/01">
    <titulo>A Mensagem</titulo>
    <autor>Fernando Pessoa</autor>
</obra>


```python
# if a == "YAML" or a == "":...
# elif a == "JSON": ...
x = input("Insira um título: ")
y = input("Insira o autor: ")
z = input("Insira a data da publicação: ") 

a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
    
if a == "XML":
    if z == "":
        c = str(f"<obra>\n\t<titulo>{x}</titulo>\n\t<autor>{y}</autor>\n</obra>")
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str(f"<obra data=\"{z}\">\n\t<titulo>{x}</titulo>\n\t<autor>{y}</autor>\n</obra>")
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): xml
    Nome do ficheiro: mensagem
    <obra data="1934/12/01">
    	<titulo>A Mensagem</titulo>
    	<autor>Fernando Pessoa</autor>
    </obra>

