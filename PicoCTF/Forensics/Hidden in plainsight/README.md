Desafio: https://play.picoctf.org/practice/challenge/524?category=4&difficulty=1&page=1

---

## Passo 1: Analisando metadados da imagem

O desafio fornece uma imagem no formato JPEG.  
Como primeiro passo, utilizei a ferramenta exiftool para inspecionar os metadados do arquivo.  
Entre as informações que foram retornadas, o campo Comment chamou atenção por conter um código em base64:

`c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9`

---

## Passo 2: Decodificando o comentário em base64

Para analisar esse código, utilizei a a decodificação base64:

`echo c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9 | base64 -d`

O resultado foi:

`steghide:cEF6endvcmQ=`


Isso indica o uso da ferramenta steghide e traz uma nova string também em base64, presumi que fosse alguma senha ou chave de acesso.

---

## Passo 3: Obtendo a senha para o steghide

A nova string base64 cEF6endvcmQ= foi então decodificada:

`echo cEF6endvcmQ= | base64 -d`


O resultado da decodificação foi:

`pAzzword`

---

## Passo 4: Extraindo o arquivo oculto

Com a senha, foi utilizada a ferramenta steghide para extrair o conteúdo escondido na imagem:

`steghide extract -sf img.png`

Quando solicitado, foi fornecida a senha pAzzword.  
A extração gerou um arquivo chamado flag.txt.

---

## Passo 5: Obtendo a flag

Ao abrir o arquivo flag.txt, foi possível visualizar a flag do desafio:

`picoCTF{h1dd3n_1n_1m4g3_e7f5b969}`

Desafio concluído com sucesso.

