<p>Aula 3 - Gerador de Ficheiros (continuação)<br />
<br />
Exercícios<p>

<p>1. Melhore o <i>gerador.py</i> de forma a que aceite um conjunto de co-autores para além do autor principal. <strong>O que fazer:</strong> Criar um input que defina o nome de um co-autor.<br /></p>

<p>O que fazer:<br /></p>
    
<p><strong>Enquanto</strong> o <i>input</i> não for vazio, ele deverá pedir repetidamente o nome de um co-autor, criando uma lista de autores.</p>

```
Insira um título: A Mensagem
Insira o autor: Fernando Pessoa
Insira um co-autor: Pedro
Insira um co-autor: Tiago
Insira um co-autor: Francisca
Insira um co-autor:
Insira a data da publicação: 1934/12/01
```

<p>Deverá imprimir:<br /></p>

```
titulo: A Mensagem
autor: Fernando Pessoa
co-autores: Pedro; Tiago; Francisca;
data: 1934/12/01
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

co_list = [] #variável recebe uma lista vazia

while True: #(enquanto) esse script/laço não quebrar/romper...
    co = input("Insira um co-autor: ")
    if co != "": #...(se) o input para co-autor for diferente de vazio...
        co_list.append(co) #...adicione o input a lista (co_list)...
        continue #...e (continue) repita o script/laço
    else: #(caso contrário) se o input para co-autor for vazio...
        break #...(quebre) pare o script/laço
        
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
```


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
count = 0 #variável count recebe zero...

while True: #até que esse script/laço quebre/pare
    co = input(f"Insira um co-autor ({count}/5): ") #input recebe (ou não) algum valor
    if co != "": #(se) o valor for diferente de vazio ""
        if count < 4: #(se)a variável count for menor que 4...
          co_list.append(co) #...adiciona o input na lista de co-autores (co_list)...
          count = count + 1 #...a variável count recebe +1...
          continue #...e (continua) repete o laço
        else: #(caso contrário) ou seja se a variável count já não for menor do que 4...
          print("AVISO: Limite de co-autores atingido (5/5)") #...imprima esta mensagem ao usuário...
          break #...e break/encerra esse script
    else: #(caso contrário) se o input for vazio ""
        break # break/encerra esse script

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
      continue #...e repita o loop/laço
    elif co not in co_list and count < 4: #(ou se) o input não está contido na lista (co_list) e count < 4...
      co_list.append(co) #...adicione o input a lista (co_list)...
      count = count + 1 #...e count recebe + 1
      continue #...e repita o loop/laço
    else: #(caso contrário) se o input não está contido na lista mas, count > 4...
      print("AVISO: Limite de co-autores atingido (5/5)") #...imprima esta mensagem ao usuário...
      break #encerre esse script/laço
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

```
titulo: A Mensagem
autor: Fernando Pessoa
co-autores:
    - Pedro
    - Tiago
    - Francisca
    - Carolina
    - Guilherme
data: 1934/12/01
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
if a == "YAML" or a == "":
    if z == "":
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: \n" + "-" 
        + (" \n-".join(co_list))) #formatação da lista se YAML com .join()
        print(c)
        ficheiro = open(f'{b}.yaml', 'w') 
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("Título: " + (x) + "\nAutor: " + (y) + "\nco-autores: \n" + "-" 
        + (" \n-".join(co_list)) + "\nData: " + (z)) #formatação da lista se YAML com .join()
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

```
{
   "titulo": "A Mensagem",
   "autor": "Fernando Pessoa",
   "co-autores": [
      "Pedro",
      "Tiago",
      "Francisca",
      "Carolina",
      "Guilherme"
   ],
   "data": "1934/12/01"
    }
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
if a == "JSON":
    if z == "":
        c = str("{\n" + "\t'Título': " + "'" + (x) + "'" + ",\n" + "\t'Autor': " 
        + "'" + (y) + "',\n" + "\t'co-autores': [\n\t\t" + "'" + ("',\n\t\t'".join(co_list)) 
        + "'\n" + "\t],\n" + "}") #formatação da lista se JSON com .join()
        print(c)
        ficheiro = open(f'{b}.json', 'w') 
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("{\n" + "\t'Título': " + "'" + (x) + "'" + ",\n" + "\t'Autor': " + "'" 
        + (y) + "',\n" + "\t'co-autores': [\n\t\t" + "'" + ("',\n\t\t'".join(co_list)) 
        + "'\n" + "\t],\n" + "\t'data': " + "'" + (z) + "'\n" + "}") #formatação da lista se JSON com .join()
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
        + "</co-autor>\n" + "\t</co-autores>" + "\n</obra>") #formatação da lista se XML com .join()
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("<obra data=" + "'" + (z) + "'" + ">\n" + "\t<titulo>" + (x) + "</titulo>" + "\n\t<autor>" 
        + (y) + "</autor>" + "\n\t<co-autores>" + "\n\t\t<co-autor>" + ("</co-autor>\n\t\t<co-autor>".join(co_list)) 
        + "</co-autor>\n" + "\t</co-autores>" + "\n</obra>") #formatação da lista se XML com .join()
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
