<head>
  <link rel="stylesheet" href="style.css">
</head>

#[CTF_EscapeTheHack] <br>

#ctf-escapethehack
#mr-robot

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

# [Mr-Robot] <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236553488-e9b6324a-49ab-46e2-a938-895708892fe2.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236553605-0980f8fd-cb8d-4614-9388-990f707763a3.png" width="700px" />
</div> <br>

