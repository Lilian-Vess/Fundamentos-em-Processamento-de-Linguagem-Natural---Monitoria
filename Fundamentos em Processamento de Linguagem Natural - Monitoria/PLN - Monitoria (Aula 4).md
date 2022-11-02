<p>Aula 4 - Gerador de Ficheiros (continuação)<br />
<br />
Correção dos Exercícios da Aula 3 + Exercício de Ordenação</p>

<p>1 - Melhore o <i>gerador.py</i> de forma a imprimir os nomes dos co-autores por ordem alfabética.</p>


```python
# a função sorted permite organizar os itens de uma lista de modo crescente ou decrescente
# https://www.w3schools.com/python/ref_func_sorted.asp
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
  if count < 5:
    co = input(f"Insira um co-autor ({count}/5): ")
    if co != "":
      if co in co_list:
        print(f"AVISO: co-autor '{co}' já existe!")
        continue
      elif co not in co_list:
        co_list.append(co)
        count = count + 1
        continue
    else:
        break
  elif count == 5:
    print("AVISO: Limite de co-autores atingido (5/5)")
    break

z = input("Insira a data da publicação: ")

a = input("Formato final (YAML, JSON ou XML): ").upper()
b = input("Nome do ficheiro: ")
if b == "": 
    b = x 
if a == "XML":
    if z == "":
        c = str("<obra>\n" + "\t<titulo>" + (x) + "</titulo>" + "\n\t<autor>" + (y) + "</autor>" 
        + "\n\t<co-autores>" + "\n\t\t<co-autor>" 
        + ("</co-autor>\n\t\t<co-autor>".join(sorted(co_list))) + "</co-autor>\n"
        + "\t</co-autores>" + "\n</obra>") #função sorted
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
    else:
        c = str("<obra data=" + "'" + (z) + "'" + ">\n" + "\t<titulo>" + (x) + "</titulo>" 
        + "\n\t<autor>" + (y) + "</autor>" + "\n\t<co-autores>" + "\n\t\t<co-autor>" 
        + ("</co-autor>\n\t\t<co-autor>".join(sorted(co_list))) + "</co-autor>\n" 
        + "\t</co-autores>" + "\n</obra>") #função sorted
        print(c)
        ficheiro = open(f'{b}.xml', 'w')
        ficheiro.write(c)
        ficheiro.close()
```

    Insira um título: A Mensagem
    Insira o autor: Fernando Pessoa
    Insira um co-autor (0/5): G
    Insira um co-autor (1/5): L
    Insira um co-autor (2/5): R
    Insira um co-autor (3/5): T
    Insira um co-autor (4/5): U
    AVISO: Limite de co-autores atingido (5/5)
    Insira a data da publicação: 1934/12/01
    Formato final (YAML, JSON ou XML): xml
    Nome do ficheiro: mensagem
    <obra data='1934/12/01'>
    	<titulo>A Mensagem</titulo>
    	<autor>Fernando Pessoa</autor>
    	<co-autores>
    		<co-autor>G</co-autor>
    		<co-autor>L</co-autor>
    		<co-autor>R</co-autor>
    		<co-autor>T</co-autor>
    		<co-autor>U</co-autor>
    	</co-autores>
    </obra>

