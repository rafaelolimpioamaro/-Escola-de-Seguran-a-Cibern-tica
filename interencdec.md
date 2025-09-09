# interencdec

###### Solved by @rafaelolimpioamaro

## Desafio: interencdec
#### Introdução

Este é o terceiro desafio da série ["conjunto_de_Questoes_para_Documentacao"] da Escola de Segurança Cibernética, disponível na plataforma [picoCTF](https://play.picoctf.org/assignments). A série é composta por 4 exercícios introdutórios que abordam tanto o estudo da [criptografia](https://pt.wikipedia.org/wiki/Criptografia) quanto o funcionamento da própria plataforma. O objetivo principal é oferecer uma base sólida nos conceitos fundamentais da criptografia moderna, por meio de desafios progressivos, práticos e acessíveis a iniciantes.

- [Página do desafio](https://play.picoctf.org/practice/challenge/418)

O objetivo deste desafio é encontrar a flag (chave) oculta no arquivo.

#### Análise Inicial

Ao acessar o desafio, nos deparamos com o seguinte enunciado:
> *"Can you get the real meaning from this file.
Download the file here."*  
> *"Você pode obter o significado real deste arquivo.
Baixe o arquivo aqui."*

Dica fornecida pelo desafio:
> *"Engaging in various decoding processes is of utmost importance."*   
> *"Envolver-se em vários processos de decodificação é de extrema importância."*

#### Resolução

Após baixar e abrir o arquivo, me deparei com uma chave criptografada:

[![Captura-de-tela-2025-09-08-213951.png](https://i.postimg.cc/BvQfBFN0/Captura-de-tela-2025-09-08-213951.png)](https://postimg.cc/TKSsRpZ7)

Para identificar o tipo de criptografia, utilizei a ferramenta [dCode](https://www.dcode.fr/cipher-identifier), inserindo o conteúdo do arquivo:

[![Captura-de-tela-2025-09-08-215008.png](https://i.postimg.cc/KYv43RMK/Captura-de-tela-2025-09-08-215008.png)](https://postimg.cc/DSH7tf5F)

O próprio site sugeriu que o texto estava em Base64. Após realizar a primeira decodificação, percebi que a flag continuava criptografada, mas o resultado veio no formato b'...', indicando que havia outro conteúdo em Base64 dentro do texto:

[![Captura-de-tela-2025-09-08-215403.png](https://i.postimg.cc/Bbhms8Hx/Captura-de-tela-2025-09-08-215403.png)](https://postimg.cc/8f6Rmzy5)

Repeti o processo, decodificando novamente em Base64. Ainda assim, o resultado não estava legível. Nesse ponto, a ferramenta sugeriu que a nova camada de criptografia utilizava Cifra de César:

[![Captura-de-tela-2025-09-08-215528.png](https://i.postimg.cc/65gh0x05/Captura-de-tela-2025-09-08-215528.png)](https://postimg.cc/WhmrNKCQ)


Após aplicar a descriptografia da Cifra de César, finalmente consegui recuperar a flag escondida.

#### Conclusão
Flag:
>`picoCTF{caesar_d3cr9pt3d_b204adc6}`

Neste desafio, aprendi a importância de aplicar diferentes métodos de decodificação de forma sequencial, pois muitas vezes a mensagem está protegida por múltiplas camadas de criptografia. Além disso, percebi como ferramentas como o dCode podem ser úteis para identificar rapidamente o tipo de cifra utilizada e agilizar o processo de resolução.

