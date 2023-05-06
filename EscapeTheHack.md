<head>
  <link rel="stylesheet" href="style.css">
</head>

# [CTF_EscapeTheHack] <br>

<table border="0">
    <tr>
        <td>

``CTF - BesidesSP 2022 17th edition`` <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236530718-7287be6b-8bae-40d0-b761-9f4ba921e8e3.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236531269-71ff8620-6c7e-4be7-a197-225c5296a5ee.png" width="700px" />
</div> <br>

Iniciando o CTF rodei o ``nmap`` para enumerar portas e também uma enumeração de diretórios com o ``gobuster``, posteriormente, executei com o ``dirb``. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236532151-aa1a3b8f-0520-4d48-b7c7-d4afd55f72ed.png" width="700px" />
</div> <br>

Encontrei o diretório ``/dashboard``, onde finalmente entrei no game e criei meu usuário de guerra ``3ll10t``. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236532378-4a91a16a-a647-438f-a087-7a83c3c8831a.jpg" width="250px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236534287-0e7b366d-5e18-406e-a004-9cdca3ddb8e2.png" width="700px" />
</div> <br>

Outro diretório interessante foi o ``/secret``, o qual trouxe a primeira flag e um link para download de um arquivo. Detalhe, a flag estava oculta na página hehe. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236534755-79785c24-f36c-45c5-8439-f5666fc67fd8.png" width="700px" />
</div> <br>

```makefile 
flag{37d42478c922df57bdebc1479b8760ff}
```
<br>

Analisando o arquivo, foi possível identificar o formato e uma dica comentada. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236548720-8fcd6d9e-e189-4f62-a3ec-5a0c7b390a87.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236548868-4bf1bbbc-41fe-4d35-adf6-46e711df3374.png" width="700px" />
</div> <br>


<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236549006-a4dbc852-6db7-465c-851f-886096ce71e1.png" width="700px" />
</div> <br>

Tratando-se de uma imagem, podemos imaginar que tenha algo relacionado a **``esteganografia``**. Para isso, entre as opções, temos uma tool chamada **``stegcracker``**,
na qual é possível fazer um brute-force para encontrar informações ocultas na imagem, combinando ``stegcrakcer + wordlist``. <br>

Ao executar a tool não tive sucesso. Pois, embora sendo uma imagem, não estava com a extensão jpg, jpeg ou algum outro formato que a tool identificasse ser uma imagem. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236549453-676a63b0-e250-4a1d-8530-5662d48fbec4.png" width="700px" />
</div> <br>

Criei uma cópia do arquivo com uma extensão válida para executar no **``stegcracker``** e rodei novamente. <br>
Encontrado a password ``mankeysdeda`` e um output do arquivo em **``flag01.jpeg.out.``** <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236550658-d6360d7e-9ee5-4ac5-82ab-711d4e06d544.png" width="700px" />
</div> <br>

Visualizando o arquivo, foi possível pegar uma dica para acessar um diretório, o que trouxe à flag e um arquivo para download. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236550918-acfe834c-de0a-4cb9-8365-52405c316560.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236550969-2a4f8ad1-6c2f-42a6-898c-27b57f91ca2c.png" width="700px" />
</div> <br>

```makefile
flag{e5f8f939ee3273255464223f6b31a612}
```
<br>

Após capturar a flag, o próximo passo foi descompactar o ``file.tar.gz``. O qual trouxe 04 ``arquivos.data``. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236551338-729f1cda-e308-4dcd-817c-e1db9fcf87a1.png" width="700px" />
</div> <br>

Ao executar o file ``<file.data>``, foi possível identificar que o primeiro arquivo na verdade tratava-se de um PDF. <br>


<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236551578-49ff640a-0b3c-44a0-af50-5e257baa4f92.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236551617-735ab62c-b6f9-4e6d-a94c-3525d4cba156.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236551677-5ffeb056-d7d3-41f3-a747-cced1aa4b4d6.png" width="700px" />
</div> <br>

Como não foi possível visualizar o PDF, tentei o mesmo procedimento feito na flag anterior. Criei uma cópia do ``file.data`` para file.pdf. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236552307-71ff4cc5-5a89-43e8-82bd-2f35b64dd1cd.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236552542-55a4e290-d4a3-4785-94e2-a681f724e8f3.png" width="700px" />
</div> <br>

Mesmo assim não foi possível visualizar. Entre algumas tentativas de tools no Kali sem sucesso, recorri a um conhecido site que faz diversos processos em arquivos, entre eles "repair" reparar, principalmente PDFs.
Fiz upload do "file.pdf" para o site, com a opção de "repair" recuperar o arquivo. Após a conclusão do processo, realizei o download e foi possível visualizar a string oculta no arquivo indicando o caminho da flag. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236553138-03053357-fa84-4361-970d-07c74812a194.png" width="700px" />
</div> <br>

Outra opção, aprendida posteriormente seria da seguinte forma.
``cat flag0* > flags.pdf``

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594406-aeab8f2b-7cf0-46ef-a8ea-39d1d23eb034.png" width="700px" />
</div> <br> 
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594443-c4ffe555-0b6d-4563-8ff9-1e7e36a47290.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594454-e02c71ad-2b59-4d72-9faa-bf84d394fa96.png" width="700px" />
</div> <br>

Utizando a hash do PDF foi possível chegar ao objetivo. <br>
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594482-5fa101c6-f54e-4fda-9c9b-d61bad1f2c20.png" width="700px" />
</div> <br>

``flag{c6e13a58698dc7a7169aea0a145e3313}``
<br>
            
Seguindo uma linha de raciocínio após a dica fornecida: <br>
```makefile
A=65
B=66
C=67

Veni, vidi, vici            
```            
<br>
            
Se temos A=65, após algumas pesquisas, foi possível identificar que se tratava da tabela ASCII a qual o 65 equivale a letra A. <br>
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594595-b4e71f7c-adc5-4775-a039-30bd5ce7de4d.png" width="700px" />
</div> <br>

Porém, temos mais uma dica Veni, vidi, vici, uma famosa frase em latim supostamente dita por Júlio César. O que me fez ligar alguns pontos levando a “Cifras”. A princípio pensei em buscar por “Cifras de César”, mas mantendo as duas dicas, busquei por identificar a cifra, ao invés de focar em um tipo. <br>

- Identificando a cifra. <br>            
         
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594684-ce2637e9-300e-42ab-ae57-05b4b4cc82e5.png" width="700px" />
</div> <br>

O resultado fortaleceu a primeira dica dada anteriormente. Sendo assim, busquei quebrar a cifra com algum ASCII decoder.
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594747-e1440a70-7bad-41df-bcc3-df59b46a81be.png" width="700px" />
</div> <br>

Recaptulando temos:

```makefile
6465687a67616c6f6f6b627420323436313531333434373332
dehzgalookbt 246151344732
```
<br>

Após horas tentando decifrar o resultado, algo sempre esteve muito intrigante, “quantidade de letras = quantidade de números”.
Chegando a conclusão de fazer a seguinte tentativa, o que levou a flag e download de um arquivo. <br>
            
```makefile
d + 2 = f 
e + 4 = i
h + 6 = n
z + 1 = a
g + 5 = l
a + 1 = b
l + 3 = o
o + 4 = s
o + 4 = s
k + 7 = r
b + 3 = e
t + 2 = v

finalbossrev            
```            
<br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236594955-113f6ee6-846a-4300-ba94-df839b604048.png" width="700px" />
</div> <br>

O arquivo aparentemente seria executável no Windows, porém, ao analisar um pouco melhor com ``file <file.exe>`` é possível identificar que trata-se de um ``ELF``. 
Ou seja, pulando a parte técnica, o arquivo pode ser executado no próprio Kali.
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595028-447e5ac7-73e3-45ee-ab8b-df01ceffdb47.png" width="700px" />
</div> <br>

Após analisar o arquivo executando o comando ``string file.exe`` foi possível identificar que o mesmo foi comprimido com ``UPX`` que até então não era do meu conhecimento. <br>
Indo atrás do UPX, encontrei uma tool ``upx-ucl`` a qual executei para fazer o ``decompress`` do file.exe. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595156-029af61d-fd8e-449d-bfd2-ebb0a1dc29de.png" width="700px" />
</div> <br>
         
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595167-035dfd45-de87-49f1-9e70-30b497be64ad.png" width="700px" />
</div> <br>
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595185-1b904236-1654-4c12-a791-08cf87272c7f.png" width="700px" />
</div> <br>

Após o decompress do file.exe, executei ```strings`` novamente, o que trouxe algumas strings aparentemente sendo hashes, e sim, algumas “flags” falsas hehe. <br>

```makefile
A partir desse ponto fiquei sem recursos...sendo esse o último desafio, essa "última flag" veio após a resolução em live com o desenvolvedor do CTF.
```
<br>
            
Analisando as hashes é possível perceber que apenas uma difere das demais. “Foi difícil perceber esse detalhe em meio a tantas hashes, após horas fazendo o CTF 😅 ”. Algumas hashes até traziam strings dizendo...“aqui não tem nada” haha...anyway. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595627-a3a40410-5b87-496b-9972-8e3451b794e2.png" width="700px" />
</div> <br>            
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595633-96275985-9c0b-4ac5-984e-d3b359fe0eb4.png" width="700px" />
</div> <br>   

Pegando a hash selecionada, identificamos estar em Base64. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595693-4e27cb13-ea48-4e70-8683-495e217fef73.png" width="700px" />
</div> <br>             
 
Resultado: <br>
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595734-d2489fa7-37ab-44ac-a974-1d4c344935e8.png" width="700px" />
</div> <br>
            
A próxima etapa foi decifrar a hash em “Cifras de César” com shift 6. Executando alguns comandos em Python, obtivemos o resultado.

```makefile
python3
msg = "<your_cipher_here>"
for i in range(len(msg)):
		print(chr(ord(msg[i]) - 6), end='')
```            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595808-01ece563-bd33-4fe1-962e-360ae36464a1.png" width="700px" />
</div> <br>
            
Retornamos ao ``file.exe`` que anteriormente foi feito o decompress, ``chmod +x file.exe`` para dar permissão e ``./file.exe`` para executar.<br> 
O programa pede para digitar a chave para descriptografar os dados, que nesse caso é a chave decifrada anteriormente com python, o que trouxe à última flag, finalizando o CTF.<br>
            
<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236595994-8231f48d-1f22-45ba-ba0b-d8ff2001c375.png" width="700px" />
</div> <br>
            
Realizei 4 dos 5 desafios, chegando a metade do último, o qual tivemos a resolução posteriormente, mas fico feliz de ter conseguido chegar até esse ponto. <br> 
Em resumo, foi um ótimo aprendizado. <br>
          
``<y0uC4n’tSt0pUs4ll>``
      </td>
    </tr>
</table>            
