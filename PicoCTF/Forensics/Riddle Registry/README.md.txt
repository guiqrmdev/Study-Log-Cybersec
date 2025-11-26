**Link do desafio:** https://play.picoctf.org/practice/challenge/530?page=1&tag=63

Este desafio nos propõe achar uma flag escondida em um PDF com conteúdo oculto. Mostra que na verdade, mesmo tentando desvendar os textos, é mostrado que não existe nada de relevante.
Partindo do pressuposto que não conseguiria extrair nada do arquivo, usei o site https://apitemplate.io/pdf-tools/extract-pdf-metadata/ para identificar metadados.

> **Nota:** Estudando, descobri que para realizar boas práticas, não devo usar sites de terceiros e utilizar exiftool ou outros argumentos.

### Identificação da Falha
O campo Author retornou uma string codificada em Base64:
`cGljb0NURntwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV9jOTk5ZTJhNH0=`

> **Nota:** Descobri que tendo "=" no final, é um arquivo de Base64.

### Decodificação
Decodifiquei a string para revelar a flag original.

**Flag:**
`picoCTF{puzzl3d_m3tadata_f0und!_c999e2a4}`