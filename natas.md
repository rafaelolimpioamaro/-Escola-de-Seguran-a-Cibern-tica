# Natas solutions 0->15

###### Solved by @rafaelolimpioamaro

## Introdução

**Natas** é um wargame de segurança web focado em vulnerabilidades e técnicas reais de exploração HTTP.  
Diferente de desafios binários, aqui o objetivo é explorar:

- HTML / CSS / JS
- HTTP Headers
- Cookies
- Directory traversal
- SQL Injection
- Compreensão de mecanismos de autenticação
- Manipulação de requisições

Cada nível mostra uma página web simples, porém com uma vulnerabilidade que permite acessar a senha para o próximo desafio.

> **Nunca use essas técnicas para invadir sites reais.**  
> Esse conteúdo é educacional e voltado para ambientes controlados.


## Desafio: Natas 0

No natas 0 coseguimos encotrar a senha para o acessálo no início do site, sem precisar fazer nada, apenas acessando o site, conforme a imagem a seguir.

[![Screenshot-2025-11-17-13-54-33.png](https://i.postimg.cc/3rCH03mP/Screenshot-2025-11-17-13-54-33.png)](https://postimg.cc/dD1fzPWB)

Quando acessamos o natas 0, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-13-56-55.png](https://i.postimg.cc/3xZB2bnk/Screenshot-2025-11-17-13-56-55.png)](https://postimg.cc/tsYWjD0b)

Para podermos encontrar a chave para o natas 1, precisamos inspecionar o site do natas 0, assim que inspecionamos, já nos deparamos com a chave do natas 1, conforme a imagem a seguir:

[![Screenshot-2025-11-17-13-57-08.png](https://i.postimg.cc/nr0F4xjy/Screenshot-2025-11-17-13-57-08.png)](https://postimg.cc/gLLbpfKs)

## Desafio: Natas 1

Quando acessamos o natas 1, nos deparamos com a seguinte dica para poder encontrar a senha do natas 2:

[![Screenshot-2025-11-17-13-58-11.png](https://i.postimg.cc/Ssg3Vxdt/Screenshot-2025-11-17-13-58-11.png)](https://postimg.cc/XGysY3Tw)

Nessa página, conforme a dica nos diz, a inspeção através do botão esquerdo está bloqueada, assim precisamos entrar na inspeção através do comando "Crtl+Shift+I", dessa forma conseguimos acessar a isnpeção do site. Agora precisamos buscar pela senha do natas 2, em que podemos ve-la logo no iníio da inspeção, confore a imagem:

[![Screenshot-2025-11-17-13-59-41.png](https://i.postimg.cc/4yz8q4Qs/Screenshot-2025-11-17-13-59-41.png)](https://postimg.cc/gL2q6W7T)[![Screenshot-2025-11-17-13-59-41.png](https://i.postimg.cc/4yz8q4Qs/Screenshot-2025-11-17-13-59-41.png)](https://postimg.cc/gL2q6W7T)

## Desafio: Natas 2

Ao acessar o natas 2, nos deparamos com a seguinte dica para encontrar a senha do natas 3:

[![Screenshot-2025-11-17-14-00-54.png](https://i.postimg.cc/K8Vn7StR/Screenshot-2025-11-17-14-00-54.png)](https://postimg.cc/68r2wPjX)

No Natas 2, a senha não se encontra no código-fonte da página, o que nos direciona a buscar outros recursos acessíveis no servidor. Uma boa prática é verificar diretórios públicos. Ao acessar /files/, encontramos alguns arquivos listados, entre eles users.txt. Esse arquivo contém a senha necessária para avançar para o próximo nível. As imagens abaixo mostram o processo completo.

[![Screenshot-2025-11-17-14-02-40.png](https://i.postimg.cc/J0PXG91n/Screenshot-2025-11-17-14-02-40.png)](https://postimg.cc/q66qFD6V)

[![Screenshot-2025-11-17-14-02-47.png](https://i.postimg.cc/qRr6QkqK/Screenshot-2025-11-17-14-02-47.png)](https://postimg.cc/PL6q5nmf)

## Desafio: Natas 3
Quando acessamos o natas 3, nos deparamos com a seguinte dica:

[![Screenshot-2025-11-17-14-03-48.png](https://i.postimg.cc/C5qy1VCK/Screenshot-2025-11-17-14-03-48.png)](https://postimg.cc/1Vs7C2jx)

No Natas 3, diferentemente do nível anterior, a senha não está visível no código-fonte. A página sugere investigar outras áreas do site. Um caminho comum em desafios web é verificar o arquivo robots.txt, utilizado por mecanismos de busca para indicar quais diretórios não devem ser indexados. Ao acessá-lo, encontramos um diretório listado em Disallow apontando para /s3cr3t/. Esse local funciona como uma pista oculta. Ao visitar esse diretório, há um arquivo users.txt, e dentro dele está a senha necessária para desbloquear o próximo nível. As imagens abaixo ilustram todo o processo de descoberta.

[![Screenshot-2025-11-17-14-05-34.png](https://i.postimg.cc/KzKcnwrY/Screenshot-2025-11-17-14-05-34.png)](https://postimg.cc/mzsG4dnx)

[![Screenshot-2025-11-17-14-05-56.png](https://i.postimg.cc/ZKsfQQ62/Screenshot-2025-11-17-14-05-56.png)](https://postimg.cc/ZC3FBV7x)

[![Screenshot-2025-11-17-14-06-02.png](https://i.postimg.cc/PJPDvSNy/Screenshot-2025-11-17-14-06-02.png)](https://postimg.cc/8fgcqBRf)


## Desafio: Natas 4
Quando acessamos o natas 4, nos deparamos com a seguinte dica:

[![Screenshot-2025-11-17-14-06-52.png](https://i.postimg.cc/HLYV76hm/Screenshot-2025-11-17-14-06-52.png)](https://postimg.cc/HrNpq9mv)

No Natas 4, a página informa que o acesso é permitido somente se o usuário vier do Natas 5. Isso significa que a aplicação valida o cabeçalho HTTP Referer. Para contornar essa restrição, utilizamos o Burp Suite para interceptar a requisição. Durante a interceptação, alteramos manualmente o valor do Referer de natas4 para natas5, simulando que a navegação partiu do nível anterior. Após reenviar a requisição com o cabeçalho modificado, o servidor a aceita e exibe a senha necessária para acessar o Natas 5. As imagens abaixo mostram todo o processo passo a passo.

[![Screenshot-2025-11-17-14-08-50.png](https://i.postimg.cc/8zJG59DV/Screenshot-2025-11-17-14-08-50.png)](https://postimg.cc/jDbm38L8)

[![Screenshot-2025-11-17-14-09-45.png](https://i.postimg.cc/cHmy2NMq/Screenshot-2025-11-17-14-09-45.png)](https://postimg.cc/R6NDJyDG)

## Desafio: Natas 5
Quando acessamos o natas 5, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-11-15.png](https://i.postimg.cc/TYBSkw8F/Screenshot-2025-11-17-14-11-15.png)](https://postimg.cc/crMXCdLB)

Aparece que o acesso não foi permitido, assim utilizaremos novamente o "Burp Suite" para podermos permitir o acesso. Quando fazemos a interceptação, podemos analisar algo chamado "loggedin" sendo igual a 0, vamos tentar alterar o valor para 1 e enviar. Após, fazermo isso a senha é nos mostrada. As imagens mostram os passos:

[![Screenshot-2025-11-17-14-11-22.png](https://i.postimg.cc/8CLjFjDN/Screenshot-2025-11-17-14-11-22.png)](https://postimg.cc/4KNJq4mS)

[![Screenshot-2025-11-17-14-11-35.png](https://i.postimg.cc/7YQCdFmP/Screenshot-2025-11-17-14-11-35.png)](https://postimg.cc/KRBvgs6C)

## Desafio: Natas 6
Quando acessamos o natas 6, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-12-09.png](https://i.postimg.cc/Kjt2fgqk/Screenshot-2025-11-17-14-12-09.png)](https://postimg.cc/m1ZJ2hGB)

No Natas 6, a página apresenta um campo para inserir uma chave secreta antes de liberar a senha do próximo nível. Ao analisar o código-fonte, percebemos que a lógica do formulário inclui um arquivo externo localizado em includes/secret.inc. Ao acessar esse arquivo diretamente, encontramos a chave secreta utilizada pelo sistema. Basta retornar à página do Natas 6, inserir essa chave no campo indicado e o site exibe a senha para o próximo nível. As imagens abaixo mostram cada etapa do processo.

[![Screenshot-2025-11-17-14-12-36.png](https://i.postimg.cc/wMXCLYMJ/Screenshot-2025-11-17-14-12-36.png)](https://postimg.cc/JHhYCgb4)

[![Screenshot-2025-11-17-14-12-41.png](https://i.postimg.cc/J75YNqKD/Screenshot-2025-11-17-14-12-41.png)](https://postimg.cc/fkkvZYGD)

[![Screenshot-2025-11-17-14-13-00.png](https://i.postimg.cc/5Nk3gkzS/Screenshot-2025-11-17-14-13-00.png)](https://postimg.cc/1fww5BJ8)

## Desafio: Natas 7
Quando acessamos o natas 7, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-13-51.png](https://i.postimg.cc/Wp56pfX5/Screenshot-2025-11-17-14-13-51.png)](https://postimg.cc/Yjmmb8cF)

No Natas 7, ao acessar a página "About" e inspecionar o código, observamos uma referência a um caminho no servidor: /etc/natas_webpass/natas8. Esse diretório aponta para o arquivo que contém a senha do próximo nível. Ao acessar diretamente esse recurso pelo navegador, o sistema exibe a senha necessária para avançar. As imagens abaixo ilustram o processo passo a passo.

[![Screenshot-2025-11-17-14-18-39.png](https://i.postimg.cc/BvCPYXyJ/Screenshot-2025-11-17-14-18-39.png)](https://postimg.cc/QBHMVxhz)

[![Screenshot-2025-11-17-14-25-19.png](https://i.postimg.cc/FRRzTG3x/Screenshot-2025-11-17-14-25-19.png)](https://postimg.cc/p9wPTf09)
## Desafio: Natas 8
Quando acessamos o natas 8, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-26-19.png](https://i.postimg.cc/bYSk8NSh/Screenshot-2025-11-17-14-26-19.png)](https://postimg.cc/6TwyfKhj)

No Natas 8, ao examinar o código-fonte, percebemos que a variável encodedSecret não armazenava a chave em texto puro, mas em um formato codificado. Observando a função fornecida, identificamos que o processo de encoding ocorre em três etapas: primeiro a string é convertida para hexadecimal, depois invertida e por fim codificada em Base64. Para recuperar a chave correta, precisamos reverter todo esse processo: decodificar Base64, desfazer a inversão da string e converter de hexadecimal para texto. Após obter o valor original da chave secreta e inseri-la no campo da página, o sistema revela a senha para o próximo nível. As imagens abaixo mostram o procedimento completo.

[![Screenshot-2025-11-17-14-26-43.png](https://i.postimg.cc/hPbJPJDd/Screenshot-2025-11-17-14-26-43.png)](https://postimg.cc/ykx6L8S1)

[![Screenshot-2025-11-17-14-46-39.png](https://i.postimg.cc/hGhhrp9R/Screenshot-2025-11-17-14-46-39.png)](https://postimg.cc/rdX8yGnf)

[![Screenshot-2025-11-17-14-46-43.png](https://i.postimg.cc/XqgV3CfS/Screenshot-2025-11-17-14-46-43.png)](https://postimg.cc/1Vfxr47J)

[![Screenshot-2025-11-17-14-47-01.png](https://i.postimg.cc/2SyzR33G/Screenshot-2025-11-17-14-47-01.png)](https://postimg.cc/bZXX1yxS)

## Desafio: Natas 9
Quando acessamos o natas 9, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-47-51.png](https://i.postimg.cc/xdGp63n8/Screenshot-2025-11-17-14-47-51.png)](https://postimg.cc/QBtqt5BZ)

No Natas 9, ao analisar o código-fonte, percebemos que o backend executa comandos do sistema operacional concatenando diretamente o valor do parâmetro needle com um comando grep. Em outras palavras, o valor enviado pelo usuário é inserido de forma insegura dentro de um comando de terminal, permitindo Command Injection. A estrutura básica era algo como:

> grep -i $key dictionary.txt

A variável $key recebe diretamente o valor enviado pelo usuário, através do parâmetro HTTP needle. Como não há sanitização adequada, conseguimos injetar comandos adicionais usando ;, que executa instruções sequenciais no shell. Assim, basta fornecer um valor como:

> needle=; cat /etc/natas_webpass/natas10

Com isso, o grep recebe um parâmetro vazio, e o comando cat é executado ao lado, exibindo o conteúdo do arquivo com a senha do próximo nível. A primeira linha retornada é a chave de acesso ao Natas 10.

As imagens abaixo mostram passo a passo o processo de exploração.

[![Screenshot-2025-11-17-14-50-53.png](https://i.postimg.cc/d14HYQhg/Screenshot-2025-11-17-14-50-53.png)](https://postimg.cc/r0RCGkC9)

[![Screenshot-2025-11-17-14-54-12.png](https://i.postimg.cc/4y0WY8bK/Screenshot-2025-11-17-14-54-12.png)](https://postimg.cc/GTkFNxfr)


## Desafio: Natas 10
Quando acessamos o natas 10, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-17-14-59-33.png](https://i.postimg.cc/v879D2hN/Screenshot-2025-11-17-14-59-33.png)](https://postimg.cc/14t4jHLG)

No nível Natas 10, a página apresenta uma interface semelhante ao desafio anterior, permitindo buscar palavras dentro de um arquivo usando grep. Porém, agora o código inclui uma tentativa de filtragem, justamente para evitar a injeção de comandos que funcionou no Natas 9. 
No Natas 9, era possível fechar o comando grep com ; e injetar outro comando shell. No Natas 10, o desenvolvedor tentou mitigar o problema usando:
> preg_match("/[;|&]/", $key)
Ou seja, "';' '|' e '&'" foram bloqueados.

O grep aceita expressões regulares, e expressões regulares podem ser exploradas para lê múltiplos arquivos.

O truque: buscar uma regex que faça o grep abrir um arquivo arbitrário.

Exemplo utilizado, devido alguns desafios anteriores estar no diretório nats_webpass:
> "r/etc/natas_webpass/natas11"

Esse input não é bloqueado pelo regex do servidor, porque não contém ;, | ou &.
Quando o grep recebe esse padrão, ele tenta ler tanto o dicionário quanto o arquivo fornecido.
Se o arquivo existe, ele aparece no output. Assim conseguimos encontrar a senha do próximo nível. As imagens abaixo mostram passo a passo o processo de exploração.

[![Screenshot-2025-11-17-14-59-38.png](https://i.postimg.cc/TYCDJyZ9/Screenshot-2025-11-17-14-59-38.png)](https://postimg.cc/Vd0vYNsr)

[![Screenshot-2025-11-17-15-05-35.png](https://i.postimg.cc/N0TFSLzj/Screenshot-2025-11-17-15-05-35.png)](https://postimg.cc/5H4fF9Jh)

## Desafio: Natas 11
Quando acessamos o natas 11, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-28-04-31-19.png](https://i.postimg.cc/BnPnPXsb/Screenshot-2025-11-28-04-31-19.png)](https://postimg.cc/4YZgr4YR)

No Natas 11, o site informa que os cookies são protegidos com XOR encryption e nos permite apenas alterar a cor de fundo da página. Ao inspecionar o cookie data, percebemos que ele contém um JSON serializado e depois criptografado com XOR e codificado em Base64. A vulnerabilidade está em como o XOR foi implementado: ao comparar o cookie original criptografado com a versão não criptografada do valor padrão ({"showpassword":"no","bgcolor":#ffffff"}) (utilizamos o site [w3schools](https://www.w3schools.com/php/phptryit.asp?filename=tryphp_compiler&ref=learnhacking.io)), conseguimos deduzir a chave usada pelo servidor, já que aplicar XOR no texto cifrado com o texto plano retorna a chave. Com a chave descoberta, basta construir um novo JSON idêntico, mas com "showpassword":"yes", criptografá-lo novamente com a mesma chave e converter para Base64 (aqui utilizamos o site [CyberChef](https://gchq.github.io/CyberChef/)). Ao substituir o cookie no navegador por essa nova versão e recarregar a página, o servidor entende que somos administradores e revela a senha do Natas 12. As imagens abaixo mostram o procedimento completo.

https://gchq.github.io/CyberChef/

[![Screenshot-2025-11-28-04-31-57.png](https://i.postimg.cc/RhbvNzD8/Screenshot-2025-11-28-04-31-57.png)](https://postimg.cc/hQxk5Ngb)

[![Screenshot-2025-11-28-04-34-50.png](https://i.postimg.cc/bN27QbDG/Screenshot-2025-11-28-04-34-50.png)](https://postimg.cc/VdmZwJF1)

[![Screenshot-2025-11-28-09-59-27.png](https://i.postimg.cc/BbRRrZzY/Screenshot-2025-11-28-09-59-27.png)](https://postimg.cc/wRcWJzgL)

[![Screenshot-2025-11-28-10-00-55.png](https://i.postimg.cc/xCC7qbVV/Screenshot-2025-11-28-10-00-55.png)](https://postimg.cc/9461n0fL)

[![Screenshot-2025-11-28-10-02-28.png](https://i.postimg.cc/d3ZxjP0d/Screenshot-2025-11-28-10-02-28.png)](https://postimg.cc/XB3LnPd7)

[![Screenshot-2025-11-28-10-03-05.png](https://i.postimg.cc/m2CbTKSy/Screenshot-2025-11-28-10-03-05.png)](https://postimg.cc/VdsyRGpJ)


## Desafio: Natas 12
Quando acessamos o natas 12, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-28-10-06-22.png](https://i.postimg.cc/BnNf63Pq/Screenshot-2025-11-28-10-06-22.png)](https://postimg.cc/LJqbCrV7)

A solução do Natas Level 12 explora uma vulnerabilidade de upload de arquivos. O site permite o envio de imagens, mas renomeia a extensão do arquivo para .jpg via um campo oculto no HTML antes do envio. Para contornar isso, iremos utilizar o burp suite para interceptar e modifica o elemento HTML, alterando o valor da extensão de .jpg para .php. Isso permite o upload do nosso arquivo criado com um script PHP malicioso ("<?php echo shell_exec($_GET['e'].' 2>&1'); ?>"). Após o upload , acessamos o arquivo PHP gerado no servidor passando comandos via parâmetro na URL (por exemplo, ?e=cat /etc/natas_webpass/natas13), o que executa o comando no servidor e revela a senha para o próximo nível. As imagens abaixo mostram o procedimento completo.

[![Screenshot-2025-11-28-10-09-21.png](https://i.postimg.cc/G28Wqs7f/Screenshot-2025-11-28-10-09-21.png)](https://postimg.cc/gXpt0rPy)

[![Screenshot-2025-11-28-10-13-44.png](https://i.postimg.cc/nctyGrvn/Screenshot-2025-11-28-10-13-44.png)](https://postimg.cc/3WnfKKSq)

[![Screenshot-2025-11-28-10-15-59.png](https://i.postimg.cc/TYCt53Q5/Screenshot-2025-11-28-10-15-59.png)](https://postimg.cc/7fJ3pDFq)

[![Screenshot-2025-11-28-10-30-47.png](https://i.postimg.cc/653dSLL3/Screenshot-2025-11-28-10-30-47.png)](https://postimg.cc/LhcYgPWK)

[![Screenshot-2025-11-28-10-32-46.png](https://i.postimg.cc/25BGtFYj/Screenshot-2025-11-28-10-32-46.png)](https://postimg.cc/v1b5gnDC)

[![Screenshot-2025-11-28-10-32-59.png](https://i.postimg.cc/XJsrcmPb/Screenshot-2025-11-28-10-32-59.png)](https://postimg.cc/8JrkTKDK)


## Desafio: Natas 13
Quando acessamos o natas 13, nos deparamos com a seguinte mensagem:
[![Screenshot-2025-11-28-10-35-51.png](https://i.postimg.cc/Y2y44cg5/Screenshot-2025-11-28-10-35-51.png)](https://postimg.cc/jCPq9FMc)

A solução do Natas Level 13 é uma evolução do nível anterior, focada em burlar uma validação mais rigorosa que utiliza a função exif_imagetype() para garantir que o arquivo enviado é realmente uma imagem. Para contornar essa segurança, é necessário falsificar o cabeçalho do arquivo, adicionando a assinatura de um formato de imagem válido, como GIF87a ou GIF89a, logo no início do código da web shell PHP (GIF87a<?php ... ?>). Isso engana o servidor, fazendo-o acreditar que se trata de um GIF. Além disso, assim como no nível 12, deve-se interceptar a requisição ou alterar o HTML no navegador para garantir que o arquivo seja salvo com a extensão .php e não como imagem. Após o upload bem-sucedido, o script é acessado via URL, permitindo a execução do comando "?e=cat /etc/natas_webpass/natas14" no servidor para ler a senha do próximo nível. Conforme o passo a passo demontrado nas imagens abaixo: 

[![Screenshot-2025-11-28-10-36-03.png](https://i.postimg.cc/rFBKJSf3/Screenshot-2025-11-28-10-36-03.png)](https://postimg.cc/jLhxqJ04)

[![Screenshot-2025-11-28-14-07-20.png](https://i.postimg.cc/q7Lq4W4m/Screenshot-2025-11-28-14-07-20.png)](https://postimg.cc/2q1rxcqv)

[![Screenshot-2025-11-28-14-11-40.png](https://i.postimg.cc/GpqLZYxN/Screenshot-2025-11-28-14-11-40.png)](https://postimg.cc/f3SQdVFj)






## Desafio: Natas 14
Quando acessamos o natas 14, nos deparamos com a seguinte mensagem:
[![Screenshot-2025-11-28-14-20-21.png](https://i.postimg.cc/RhjVgBLr/Screenshot-2025-11-28-14-20-21.png)](https://postimg.cc/N2kc0Znb)

A solução do Natas Level 14 foca na exploração de uma vulnerabilidade clássica, SQL Injection. O site apresenta um formulário de login que concatena diretamente a entrada do usuário na consulta do banco de dados sem a devida proteção. Ao analisar o código-fonte, percebe-se que a query é montada com aspas duplas. O atacante consegue então manipular o campo "username" inserindo admin" OR 1=1 --. Essa entrada fecha a string do nome de usuário, injeta uma condição que é sempre verdadeira (OR 1=1) e comenta o restante da consulta (usando --), anulando a verificação de senha. Isso faz com que o banco de dados retorne todos os registros da tabela de usuários, satisfazendo a verificação do código PHP de que "uma ou mais linhas" foram retornadas, o que libera a exibição da senha para o próximo nível. Estes passos estão representados nas imagens abaixo:

[![Screenshot-2025-11-28-14-20-30.png](https://i.postimg.cc/bwRSwZRd/Screenshot-2025-11-28-14-20-30.png)](https://postimg.cc/cvrLD42N)

[![Screenshot-2025-11-28-14-41-36.png](https://i.postimg.cc/s26B5bq7/Screenshot-2025-11-28-14-41-36.png)](https://postimg.cc/NyXfcCgj)

[![Screenshot-2025-11-28-14-41-44.png](https://i.postimg.cc/NMKKDpv6/Screenshot-2025-11-28-14-41-44.png)](https://postimg.cc/WFPpbm3z)




## Desafio: Natas 15
Quando acessamos o natas 15, nos deparamos com a seguinte mensagem:

[![Screenshot-2025-11-28-14-43-15.png](https://i.postimg.cc/9FdrLDsW/Screenshot-2025-11-28-14-43-15.png)](https://postimg.cc/w7Bqvj6P)

A solução para o Natas Level 15 utiliza a ferramenta SQLMap. Diferente do nível anterior, o servidor não retorna erros de SQL nem dados da consulta, apenas indica se um usuário existe ou não. A vulnerabilidade reside na falta de sanitização do parâmetro username na consulta SELECT. O ataque consiste em inferir dados bit a bit (neste caso, a senha) fazendo perguntas booleanas ao banco de dados (ex: "a primeira letra da senha é 'a'?"). Usando o SQLMap, configura-se o alvo, as credenciais de autenticação (natas15), e parâmetros específicos (--level=5, --risk=3, e --string="This user exists") para automatizar essas perguntas. A ferramenta então enumera o banco de dados (-D natas15), a tabela (-T users) e extrai as colunas desejadas (-C username,password), revelando finalmente a senha do usuário natas16 para o próximo nível. As imagens demonstram passo a passo dessa ferramenta.

[![Screenshot-2025-11-28-14-43-27.png](https://i.postimg.cc/CxJdVWFQ/Screenshot-2025-11-28-14-43-27.png)](https://postimg.cc/QF9jQYKQ)

[![Screenshot-2025-11-28-15-35-19.png](https://i.postimg.cc/tgTJR2Jp/Screenshot-2025-11-28-15-35-19.png)](https://postimg.cc/G4WdqPv5)

[![Screenshot-2025-11-28-15-35-31.png](https://i.postimg.cc/prNLZvZX/Screenshot-2025-11-28-15-35-31.png)](https://postimg.cc/LYTS9rwr)

[![Screenshot-2025-11-28-15-35-45.png](https://i.postimg.cc/PJmrV739/Screenshot-2025-11-28-15-35-45.png)](https://postimg.cc/Wq1vh5Pw)

[![Screenshot-2025-11-28-15-36-18.png](https://i.postimg.cc/65XQ49qf/Screenshot-2025-11-28-15-36-18.png)](https://postimg.cc/yWLKwCFD)

## Conclusão

Os desafios do Natas 0 ao 15 demonstram, de forma progressiva, como vulnerabilidades simples podem evoluir para cenários complexos e realistas no contexto de segurança web. Ao longo dos níveis, é possível compreender que cada falha explorada — seja em formulários HTML, cabeçalhos HTTP, permissões de diretório, manipulação de cookies, injeção de comandos ou SQL Injection — nasce quase sempre de decisões inseguras no desenvolvimento, como a falta de sanitização de entrada, validações superficiais ou confiança excessiva no lado do cliente. Mais do que encontrar senhas, cada exercício reforça a importância de entender o funcionamento interno de aplicações web, interpretar o comportamento do servidor e pensar como um atacante. Ao mesmo tempo, evidencia o lado ético do aprendizado: explorar vulnerabilidades apenas em ambientes controlados e compreender que o objetivo final não é explorar sistemas reais, mas adquirir conhecimento para evitá-las, projetar aplicações seguras e atuar de forma responsável na área de segurança da informação.





