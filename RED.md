# RED

###### Solved by @rafaelolimpioamaro

## Desafio: RED
#### Introdução

Este desafio marca o fim da série ["conjunto_de_Questoes_para_Documentacao"] da Escola de Segurança Cibernética, disponível na plataforma [picoCTF](https://play.picoctf.org/assignments). A série é composta por 4 exercícios introdutórios que abordam tanto o estudo da [criptografia](https://pt.wikipedia.org/wiki/Criptografia) quanto o funcionamento da própria plataforma. O objetivo principal é oferecer uma base sólida nos conceitos fundamentais da criptografia moderna, por meio de desafios progressivos, práticos e acessíveis a iniciantes.

- [Página do desafio](https://play.picoctf.org/practice/challenge/469)

Neste caso, o desafio RED consiste em encontrar a flag oculta em uma imagem aparentemente simples.

#### Análise Inicial

Ao acessar o enunciado do desafio, nos deparamos com a seguinte mensagem:
> *"RED, RED, RED, RED
Download the image: red.png"*   
> *"VERMELHO, VERMELHO, VERMELHO, VERMELHO
Baixe a imagem: red.png"

Além disso, foram fornecidas as seguintes dicas:
> *"The picture seems pure, but is it though?"*  
> *"Red?Ged?Bed?Aed?"*  
> *"Check whatever Facebook is called now."*  

> *"A imagem parece pura, mas é?"*  
> *"Vermelho? Ged? Cama? Aed?"*  
> *"Verifique o nome do Facebook agora."*  


#### Resolução

Após baixar e abrir o arquivo, encontrei apenas um simples quadrado vermelho:

[![Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-3c97cd79.jpg](https://i.postimg.cc/3x3bpTJ4/Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-3c97cd79.jpg)](https://postimg.cc/3dbB5zGY)

Pesquisando um pouco mais, descobri que uma das técnicas comuns para esconder informações em imagens é a Esteganografia por LSB (Least Significant Bit – Bit menos significativo).
Você pode entender melhor essa técnica neste artigo: [Esteganografia por LSB](https://hackingnaweb.com/criptografia/esteganografia-por-lsb/). Com isso em mente, utilizei a ferramenta online[cyberchef](https://cyberchef.io/), que permite realizar diversas operações de criptografia e esteganografia.
Ao carregar a imagem no CyberChef e aplicar a operação correta de decodificação, consegui extrair a flag oculta:

[![Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-33737233.jpg](https://i.postimg.cc/9XrbqB5h/Imagem-do-Whats-App-de-2025-09-06-s-18-22-04-33737233.jpg)](https://postimg.cc/t7GWKW4S)


#### Conclusão
A flag encontrada foi:
>`picoCTF{r3d_1s_th3_ult1m4t3_cur3_f054dn355_}`

Esse desafio me mostrou novas formas de ocultar mensagens e destacou a importância de analisar com atenção arquivos ou imagens aparentemente comuns, já que podem esconder informações valiosas em seus bits menos significativos.