<p>Aula 3 - Gerador de Ficheiros (continuação)<br />
<br />
Exercícios<p>

<p>1. Melhore o <i>gerador.py</i> de forma a que aceite um conjunto de co-autores para além do autor principal. <strong>O que fazer:</strong> Criar um input que defina o nome de um co-autor.<br /></p>

<p>O que fazer:<br /></p>
    
<p><strong>Enquanto</strong> o <i>input</i> não for vazio, ele deverá pedir repetidamente o nome de um co-autor, criando uma lista de autores.</p>
    
<p>&emsp;Insira um título: A Mensagem<br />
&emsp;Insira o autor: Fernando Pessoa<br />
&emsp;Insira um co-autor: Pedro<br />
&emsp;Insira um co-autor: Tiago<br />
&emsp;Insira um co-autor: Francisca<br />
&emsp;Insira um co-autor:<br />
&emsp;Insira a data da publicação: 1934/12/01</p>

<p>Deverá imprimir:<br /></p>

<p>&emsp;titulo: A Mensagem<br />
&emsp;autor: Fernando Pessoa<br />
&emsp;co-autores: Pedro; Tiago; Francisca;<br />
&emsp;data: 1934/12/01
</p>


```python
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = [] #criação de um lista vazia

while True: #(enquanto) esse laço não quebrar/romper...
    co = input("Insira um co-autor: ")
    if co != "": #...(se) o input para co-autor for diferente de vazio...
        co_list.append(co) #...adicione o input a lista (co_list)...
        continue #...(continue) repita o laço
    else: #(caso contrário) se o input para co-autor for vazio...
        break #...(quebre) pare o laço
        
z = input("Insira a data da publicação: ")
a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
if a == "YAML" or a == "":
    if z == "":
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: " + ("; ".join(co_list)) + ";") #formatação da lista
        print(c)
        ficheiro = open(f'{b}.yaml', 'w') 
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: " + ("; ".join(co_list)) + ";" + "\nData: " + (z))
        print(c)
        ficheiro = open(f'{b}.yaml', 'w') 
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor: Pedro
    Insira um co-autor: Tiago
    Insira um co-autor: Francisca
    Insira um co-autor: 
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): yaml
    Nome do ficheiro: mensagem
    Título: A Mensagem
    Autor: Fernando Pessoa
    co-autores: Pedro; Tiago; Francisca;
    Data: 1934/12/01


<p>2. Estabeleça também um limite para o número de co-autores que uma obra pode ter (por exemplo: <i>5</i>). O programa deve pedir o nome dos co-autores enquanto este limite não for excedido ou o input de um co-autor não for vazio.</p>

<p>O programa deverá ter o seguinte comportamento:</p>

<p><i>Insira um título: A Mensagem<br />
Insira o autor: Fernando Pessoa<br />
Insira um co-autor (0/5): Pedro<br />
Insira um co-autor (1/5): Tiago<br />
Insira um co-autor (2/5): Francisca<br />
Insira um co-autor (3/5): Carolina<br />
Insira um co-autor (4/5): Guilherme<br />
AVISO: Limite de co-autores atingido (5/5)<br />
Insira a data da publicação: 1934/12/01</i></p>


```python
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = []
count = 0 #variável recebe zero...

while True: #até que o laço quebre/pare
    co = input(f"Insira um co-autor ({count}/5): ")
    if co != "":
        if count < 4: #(se)a variável count for menor que 4...
          co_list.append(co) #...adiciona o input na lista de co-autores (co_list)...
          count = count + 1 #...e a variável count recebe 1
          continue
        else: #(caso contrário) ou seja se a variável count se tornar 5...
          print("AVISO: Limite de co-autores atingido (5/5)") #...imprima esta mensagem ao usuário...
          break #...e quebre o programa
    else:
        break

z = input("Insira a data da publicação: ")
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): Pedro
    Insira um co-autor (1/5): Tiago
    Insira um co-autor (2/5): Francisca
    Insira um co-autor (3/5): Carolina
    Insira um co-autor (4/5): Guilherme
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01


<p>3. Melhore o <i>gerador.py</i> de forma a eliminar entradas repetidas de co-autores.</p>


```python
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = []
count = 0

while True: 
  co = input(f"Insira um co-autor ({count}/5): ")
  if co != "":
    if co in co_list: #(se) o input já está contido na lista (co_list)...
      print(f"AVISO: co-autor '{co}' já existe!") #...imprima esta mensagem ao usuário...
      continue #...e repita o laço
    elif co not in co_list and count < 4: #(se) o input não está contido na lista (co_list) e count < 4...
      co_list.append(co) #...adicione o input a lista...
      count = count + 1 #...e count recebe + 1
      continue
    else: 
      print("AVISO: Limite de co-autores atingido (5/5)")
      break 
  else:
    break

z = input("Insira a data da publicação: ")
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): Pedro
    Insira um co-autor (1/5): Pedro
    AVISO: co-autor 'Pedro' já existe!
    Insira um co-autor (1/5): Tiago
    Insira um co-autor (2/5): Francisca
    Insira um co-autor (3/5): Carolina
    Insira um co-autor (4/5): Francisca
    AVISO: co-autor 'Francisca' já existe!
    Insira um co-autor (4/5): Guilherme
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01


<p>4. Melhore a formatação do campo dos co-autores nos ficheiros gerados. No caso do ficheiro ser YAML, o resultado deverá ser o seguinte:</p>

<p><i>titulo: A Mensagem<br />
autor: Fernando Pessoa<br />
co-autores:<br />
  &emsp;- Pedro<br />
  &emsp;- Tiago<br />
  &emsp;- Francisca<br />
  &emsp;- Carolina<br />
  &emsp;- Guilherme<br />
    data: 1934/12/01</i></p>


```python
# o método .join() permite concatenar todos os itens de uma lista definindo seus respectivos separadores
# https://www.w3schools.com/python/python_lists_join.asp
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = []
count = 0

while True: 
  co = input(f"Insira um co-autor ({count}/5): ")
  if co != "":
    if co in co_list:
      print(f"AVISO: co-autor '{co}' já existe!")
      continue
    elif co not in co_list and count < 4:
      co_list.append(co)
      count = count + 1
      continue
    else: 
      print("AVISO: Limite de co-autores atingido (5/5)")
      break 
  else:
    break

z = input("Insira a data da publicação: ")

a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
if a == "YAML" or a == "":
    if z == "":
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: \n" + "-" + (" \n-".join(co_list)))
        print(c)
        ficheiro = open(f'{b}.yaml', 'w') 
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: \n" + "-" + (" \n-".join(co_list)) + "\nData: " + (z))
        print(c)
        ficheiro = open(f'{b}.yaml', 'w') 
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): Pedro
    Insira um co-autor (1/5): Tiago
    Insira um co-autor (2/5): Francisca
    Insira um co-autor (3/5): Carolina
    Insira um co-autor (4/5): Guilherme
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): yaml
    Nome do ficheiro: mensagem
    Título: A Mensagem
    Autor: Fernando Pessoa
    co-autores: 
    - Pedro 
    - Tiago 
    - Francisca 
    - Carolina
    Data: 1934/12/01


<p>No caso de ser JSON:</p>

<p><i>{<br />
   &emsp;"titulo": "A Mensagem",<br />
   &emsp;"autor": "Fernando Pessoa",<br />
   &emsp;"co-autores": [<br />
      &emsp;&emsp;"Pedro",<br />
      &emsp;&emsp;"Tiago",<br />
      &emsp;&emsp;"Francisca",<br />
      &emsp;&emsp;"Carolina",<br />
      &emsp;&emsp;"Guilherme"<br /> 
   ],<br />
   &emsp;"data": "1934/12/01"<br />
    }</i></p>


```python
# o método .join() permite concatenar todos os itens de uma lista definindo seus respectivos separadores
# https://www.w3schools.com/python/python_lists_join.asp
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = []
count = 0

while True: 
  co = input(f"Insira um co-autor ({count}/5): ")
  if co != "":
    if co in co_list:
      print(f"AVISO: co-autor '{co}' já existe!")
      continue
    elif co not in co_list and count < 4:
      co_list.append(co)
      count = count + 1
      continue
    else: 
      print("AVISO: Limite de co-autores atingido (5/5)")
      break 
  else:
    break

z = input("Insira a data da publicação: ")

a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
if a == "JSON":
    if z == "":
        c = str("{\n" + "\t'Título': " + "'" + (x) + "'" + ",\n" + "\t'Autor': " 
        + "'" + (y) + "',\n" + "\t'co-autores': [\n\t\t" + "'" + ("',\n\t\t'".join(co_list)) 
        + "'\n" + "\t],\n" + "}")
        print(c)
        ficheiro = open(f'{b}.json', 'w') 
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("{\n" + "\t'Título': " + "'" + (x) + "'" + ",\n" + "\t'Autor': " + "'" 
        + (y) + "',\n" + "\t'co-autores': [\n\t\t" + "'" + ("',\n\t\t'".join(co_list)) 
        + "'\n" + "\t],\n" + "\t'data': " + "'" + (z) + "'\n" + "}")
        print(c)
        ficheiro = open(f'{b}.json', 'w') 
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): Pedro
    Insira um co-autor (1/5): Tiago
    Insira um co-autor (2/5): Francisca
    Insira um co-autor (3/5): Carolina
    Insira um co-autor (4/5): Guilherme
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): json
    Nome do ficheiro: mensagem
    {
    	'Título': 'A Mensagem',
    	'Autor': 'Fernando Pessoa',
    	'co-autores': [
    		'Pedro',
    		'Tiago',
    		'Francisca',
    		'Carolina'
    	],
    	'data': '1934/12/01'
    }


<p>No caso de ser XML:</p>


```python
<obra data="1934/12/01">
   <titulo>A Mensagem</titulo>
   <autor>Fernando Pessoa</autor>
   <co-autores>
      <co-autor>Pedro</co-autor>
      <co-autor>Tiago</co-autor>
      <co-autor>Francisca</co-autor>
      <co-autor>Carolina</co-autor>
      <co-autor>Guilherme</co-autor>
   </co-autores>
</obra>
```


```python
# o método .join() permite concatenar todos os itens de uma lista definindo seus respectivos separadores
# https://www.w3schools.com/python/python_lists_join.asp
while True:
    x = input("Insira um título: ")
    y = input("Insira o autor: ")
    if x == "" or y == "":
        print("ERRO: os campos 'título' e 'autor' não podem ser vazios.")
        continue
    else:
        break

co_list = []
count = 0

while True: 
  co = input(f"Insira um co-autor ({count}/5): ")
  if co != "":
    if co in co_list:
      print(f"AVISO: co-autor '{co}' já existe!")
      continue
    elif co not in co_list and count < 4:
      co_list.append(co)
      count = count + 1
      continue
    else: 
      print("AVISO: Limite de co-autores atingido (5/5)")
      break 
  else:
    break

z = input("Insira a data da publicação: ")

a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
if a == "XML":
    if z == "":
        c = str("<obra>\n" + "\t<titulo>" + (x) + "</titulo>" + "\n\t<autor>" + (y) + "</autor>" 
        + "\n\t<co-autores>" + "\n\t\t<co-autor>" + ("</co-autor>\n\t\t<co-autor>".join(co_list)) 
        + "</co-autor>\n" + "\t</co-autores>" + "\n</obra>")
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("<obra data=" + "'" + (z) + "'" + ">\n" + "\t<titulo>" + (x) + "</titulo>" + "\n\t<autor>" 
        + (y) + "</autor>" + "\n\t<co-autores>" + "\n\t\t<co-autor>" + ("</co-autor>\n\t\t<co-autor>".join(co_list)) 
        + "</co-autor>\n" + "\t</co-autores>" + "\n</obra>")
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): Pedro
    Insira um co-autor (1/5): Tiago
    Insira um co-autor (2/5): Francisca
    Insira um co-autor (3/5): Carolina
    Insira um co-autor (4/5): Guilherme
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): xml
    Nome do ficheiro: mensagem
    <obra data='1934/12/01'>
    	<titulo>A Mensagem</titulo>
    	<autor>Fernando Pessoa</autor>
    	<co-autores>
    		<co-autor>Pedro</co-autor>
    		<co-autor>Tiago</co-autor>
    		<co-autor>Francisca</co-autor>
    		<co-autor>Carolina</co-autor>
    	</co-autores>
    </obra>

