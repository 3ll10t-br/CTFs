<head>
  <link rel="stylesheet" href="style.css">
</head>

# CTF <br> 

## [CTF_EscapeTheHack] <br>

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



















