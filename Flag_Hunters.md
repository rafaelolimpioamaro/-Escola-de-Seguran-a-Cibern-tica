# Flag Hunters

###### Solved by @rafaelolimpioamaro

## Desafio: Flag Hunters
#### Introdução

Este desafio da série ["conjunto_de_Questoes_para_Documentacao"] da Escola de Segurança Cibernética, disponível na plataforma [picoCTF](https://play.picoctf.org/assignments). A série é composta por 4 exercícios introdutórios que abordam tanto o estudo da [criptografia](https://pt.wikipedia.org/wiki/Criptografia) quanto o funcionamento da própria plataforma. O objetivo principal é oferecer uma base sólida nos conceitos fundamentais da criptografia moderna, por meio de desafios progressivos, práticos e acessíveis a iniciantes.

- [Página do desafio](https://play.picoctf.org/practice/challenge/472)

Neste desafio, o objetivo é analisar o código-fonte para encontrar a flag escondida.

#### Análise Inicial

Ao acessar o desafio, nos deparamos com o seguinte enunciado:
> *"Lyrics jump from verses to the refrain kind of like a subroutine call. There's a hidden refrain this program doesn't print by default. Can you get it to print it? There might be something in it for you.
The program's source code can be downloaded here.
Additional details will be available after launching your challenge instance."*  
> *"As letras saltam dos versos para o refrão, como uma chamada de sub-rotina. Há um refrão oculto que este programa não imprime por padrão. Você pode obtê-lo para imprimir ela? Pode haver algo nele para você.
O código-fonte do programa pode ser baixado aqui.
Detalhes adicionais estarão disponíveis após o lançamento de sua instância de desafio.As letras saltam dos versos para o refrão, como uma chamada de sub-rotina. Há um refrão oculto que este programa não imprime por padrão. Você pode obtê-lo para imprimir ela? Pode haver algo nele para você.
O código-fonte do programa pode ser baixado aqui.
Detalhes adicionais estarão disponíveis após o lançamento de sua instância de desafio."

Dicas fornecida pelo desafio:
> *"- This program can easily get into undefined states. Don't be shy about Ctrl-C."*

> *" Unsanitized user input is always good, right?"*

> *" Is there any syntax that is ripe for subversion?"*

> *" - Este programa pode facilmente entrar em estados indefinidos. Não tenha vergonha de Ctrl-C."*

> *"- A entrada do usuário não higienizada é sempre boa, certo?"*

> *"- Existe alguma sintaxe que esteja pronta para a subversão?"*

#### Resolução

Ao clicar em “inicializar a instância”, o desafio fornece o comando

> *"$ nc verbal-sleep.picoctf.net 51675"*

para ser executado no prompt de comando. Entretanto, ao digitar qualquer entrada, o programa entra em um loop infinito, sem apresentar resultados úteis. Diante disso, optei por baixar o código-fonte, disponibilizado no link indicado no enunciado, a fim de realizar uma análise mais detalhada do funcionamento do desafio.

Seguindo a dica, fui observar as regras de entrada que o código apresentava:

[![Captura-de-tela-2025-09-08-204820.png](https://i.postimg.cc/RVGVwvQ2/Captura-de-tela-2025-09-08-204820.png)](https://postimg.cc/jLwbb01h)


Durante a execução do desafio, observei que o código processa cada linha da letra usando line.split(';'), o que significa que a linha é fragmentada sempre que encontra um ponto e vírgula (“;”). Essa lógica permite que, ao inserir um ponto e vírgula em minha entrada, eu consiga injetar múltiplos comandos ou fragmentos de código, separados por essa delimitação.
Explorando essa vulnerabilidade, percebi que poderia manipular o comportamento do interpretador da seguinte maneira: ao inserir " ;RETURN 0” como resposta, o código dividiria essa entrada em duas partes — “ ” e “RETURN 0”. A segunda parte então seria interpretada como um comando válido (por corresponder ao padrão RETURN [número]), redirecionando o fluxo de execução para a linha 0 do script.
Esse redirecionamento é essencial porque a flag está incorporada na variável secret_intro, que aparece antes do marcador [VERSE1]

[![Captura-de-tela-2025-09-08-211313.png](https://i.postimg.cc/PfDktTR1/Captura-de-tela-2025-09-08-211313.png)](https://postimg.cc/ThTs0MGP)

 — que é onde o leitor inicia por padrão. Ao retornar à linha 0, lugar onde a flag se encontra, o programa passa a exibir esse conteúdo oculto — permitindo finalmente que eu descubra a flag, que está armazenada no arquivo flag.txt.

Dessa, forma consegui encontrar a flag escondida:

[![Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-2500b2f8.jpg](https://i.postimg.cc/WzGK0pBK/Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-2500b2f8.jpg)](https://postimg.cc/V0ND8wLB)


#### Conclusão
Flag:
>`picoCTF{70637h3r_f0r3v3r_0ed60683}`

Ao resolver este desafio, aprendi a importância de analisar o código-fonte com atenção, identificando como determinadas funções (como o split(';')) podem introduzir comportamentos inesperados. Percebi como a manipulação de entradas pode alterar o fluxo de execução de um programa, neste caso permitindo um redirecionamento para o início do código onde a flag estava escondida.

Além disso, compreendi melhor o uso de expressões regulares (re.match) para interpretar comandos e como instruções de controle, como RETURN, podem ser exploradas em um contexto de CTF.

Do ponto de vista de segurança, o desafio mostrou de forma prática como validações insuficientes de entrada podem ser exploradas, reforçando a necessidade de implementar filtros e sanitização adequados para evitar que usuários mal-intencionados injetem comandos inesperados.

