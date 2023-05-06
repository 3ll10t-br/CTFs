# [Mr-Robot] <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236553488-e9b6324a-49ab-46e2-a938-895708892fe2.png" width="700px" />
</div> <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236553605-0980f8fd-cb8d-4614-9388-990f707763a3.png" width="700px" />
</div> <br>

Mesmo sem a dica, seria fácil encontrar essa key, pois trata-se de um ``Content Discovery`` muito simples, mas que acaba sendo ignorado pelos mais experientes.
Caso não faça idéia do que seja, é possível encontrar esta informação na sala do Pentester Jr, no módulo ``https://tryhackme.com/room/contentdiscovery``.

Após esta etapa, foi possível visualizar dois diretórios que poderiam levar a key que eu precisava. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236586891-a03bcf3d-bbdc-4e41-b04b-096e7f34c100.png" width="700px" />
</div> <br>

Buscando por um dos diretórios encontrados, é possível obter a primeira key. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587000-7836ae50-3fb1-4751-a83c-1bf6170fe341.png" width="700px" />
</div> <br>

No outro diretório foi possível fazer download de um arquivo. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587081-91ce2e1f-8680-49d4-8abc-76ed0ca4befe.png" width="700px" />
</div> <br>

Ao visualizar o conteúdo do arquivo, identifiquei que o mesmo era muito extenso. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587158-8bac22ba-cc80-4063-82c3-b0873a472f3c.png" width="700px" />
</div> <br>

Sendo assim, executei ``sort <file> | uniq > list.txt``, para salvar como um novo arquivo chamado ``list.txt``, porém, sem dados repetidos.
O que de fato diminuiu consideravelmente a extensão do arquivo. 
Utilizando ``wc <file>`` é possível ver a diferença de tamanho entre o ``<file>`` e o ``list.txt``.

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587284-9724e421-a7c1-4c0c-8c8b-8b5e64233325.png" width="700px" />
</div> <br>

Por hora deixei o arquivo ``list.txt`` de lado e executei o ``Gobuster`` para enumeração de diretórios. <br>
Entre os dados ocultos, um tornou-se o alvo que me levou a aproximar-se das duas keys restantes.

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587381-7c95e9cc-d198-4789-bb98-a14bf0927aea.png" width="700px" />
</div> <br>

Dentre algumas tentativas, tentei acessar como user elliot, o que trouxe uma boa notícia, a senha estava errada, porém o usuário existe. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587437-7f5324a2-1abe-4a36-8eb8-14433e9f7bf0.png" width="700px" />
</div> <br>

A partir deste ponto, tratando-se de WordPress, utilizei o ``wpscan`` com o user elliot e como password adicionei a ``lista.txt`` criada anteriormente.

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587533-65e9c090-0ba3-459f-8be0-4604fe711ac6.png" width="700px" />
</div> <br>

Xeque! <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587563-717a5741-3b65-48c4-922c-71037ef236f6.png" width="700px" />
</div> <br>

Usando as credenciais, acessei o painel: <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587608-45161e2e-5546-4468-9f53-bd82ee84859e.png" width="700px" />
</div> <br>

Appearance > Editor > 404 Template <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587661-cc72004e-feea-4d4c-b2d4-f92d01508699.png" width="700px" />
</div> <br>

Subtituí o ``404 Template`` por um reverse shell em php. <br>

```makefile
https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php
```

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587795-7fb9a007-4160-4f4e-850f-6bece0e05985.png" width="700px" />
</div> <br>

Após trocar o IP e PORTA, abri um nc na minha máquina. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236587923-fed3122f-dfe3-4e8c-8f3f-efcf47f49dfa.png" width="700px" />
</div> <br>

- nc listening na minha máquina
- payload.php dentro do 404 Template no alvo configurado com meu IP e porta <br>

Direcionei a navegação para o caminho do 404 Template. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236588354-b4addd4b-d5c7-4e85-816f-798742e46f9f.png" width="700px" />
</div> <br>

Shell! <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236588811-125111c1-d614-4935-9dc5-d7d9a3b057cf.png" width="700px" />
</div> <br>

A partir desse momento eu pensei em fazer uma busca por: <br>

- ``search -f *.txt``
- ``search -f *.key``
<br>
Mas optei por entrar em alguns diretórios e ver o que encontrava por lá. Em um desses diretórios, encontrei um usuário, o qual tinha dois arquivos.
Um dos arquivos - permissão negada, o outro arquivo trouxe as credenciais em hash. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236589799-8623d41f-634e-49e2-99cf-a013cca47f7c.png" width="700px" />
</div> <br>

Poderia ter quebrado a hash com hashcat ou john, mas por questão de tempo, optei por nossa querida crackstation ``https://crackstation.net/``.

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236590792-c7cc3b9f-a021-4a8e-a153-d30c7151bd1b.png" width="700px" />
</div> <br>

Após quebrar a hash e descobrir a senha do usuário (now u see 😅), foi possível dar um cat no arquivo negado anteriormente, e pegar a segunda key.

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236590836-6ad528b1-c527-49f6-b952-a8d8d2319084.png" width="700px" />
</div> <br>

Após pegar a segunda key, tentei acessar outro diretório em busca da última key, porém o acesso foi negado, por falta de privilégios. <br>

```makefile
find / -perm -4000 2> /dev/null
```
<br>

Para verificar quais os programas executáveis que estão ativos na máquina. Criando um gap para uma possível interação e escalação de privilégio. <br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236590908-6756d003-7ab0-40e2-9afa-662df5ddb6c2.png" width="700px" />
</div> <br>

``https://gtfobins.github.io/``
<br>

Para encontrar o bypass referente ao executável identificado na etapa anterior ``find / -perm -4000 2> /dev/null``.
<br>
Executei o bypass, obtive a escalação de privilégios, e consequentemente pegando assim a terceira e última key que faltava.<br>

<div align="center">
<img src="https://user-images.githubusercontent.com/108879046/236590978-69ffb90d-bc35-44fc-a652-c8a96467a869.png" width="700px" />
</div> <br>

``<y0uC4n’tSt0pUs4ll/>``





