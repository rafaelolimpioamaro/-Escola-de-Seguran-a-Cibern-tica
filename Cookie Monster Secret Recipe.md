# Cookie Monster Secret Recipe

###### Solved by @rafaelolimpioamaro

## Desafio: Cookie Monster Secret Recipe
#### Introdução

Este desafio marca o início da série ["conjunto_de_Questoes_para_Documentacao"] da Escola de Segurança Cibernética, disponível na plataforma [picoCTF](https://play.picoctf.org/assignments). A série é composta por 4 exercícios introdutórios que abordam tanto o estudo da [criptografia](https://pt.wikipedia.org/wiki/Criptografia) quanto o funcionamento da própria plataforma. O objetivo principal é oferecer uma base sólida nos conceitos fundamentais da criptografia moderna, por meio de desafios progressivos, práticos e acessíveis a iniciantes.

- [Página do desafio](https://play.picoctf.org/practice/challenge/469)

O objetivo deste desafio é encontrar a flag (chave) oculta na página web.

#### Análise Inicial

Ao acessar o desafio, nos deparamos com o seguinte enunciado:
> *"Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?
You can access the Cookie Monster here and good luck."*  
> *"Cookie Monster escondeu sua receita ultrassecreta de biscoito em algum lugar de seu site. Como aspirante a detetive de biscoitos, sua missão é descobrir esse segredo delicioso. Você pode ser mais esperto que o Cookie Monster e encontrar a receita escondida?
Você pode acessar o Cookie Monster aqui e boa sorte"

Dica fornecida pelo desafio:
> *"Web browsers often have tools that can help you inspect various aspects of a webpage, including things you can't see directly."
> *"Os navegadores da Web geralmente têm ferramentas que podem ajudá-lo a inspecionar vários aspectos de uma página da Web, incluindo coisas que você não pode ver diretamente."

#### Resolução

Ao clicar no link, fui direcionado ao seguinte site:
[![Captura-de-tela-2025-09-05-215849.png](https://i.postimg.cc/gJtZcbp3/Captura-de-tela-2025-09-05-215849.png)](https://postimg.cc/gXRJ45n0)

Seguindo a dica, utilizei a ferramenta Inspecionar do navegador:
 - Cliquei com o botão direito na página -> Inspecionar -> aba Rede (Network) -> filtro Doc.
 - Inserindo qualquer e-mail e senha no formulário de login e clicando em Login, observei que a página login.php aparecia listada.
[![Captura-de-tela-2025-09-05-215926.png](https://i.postimg.cc/P5KZVw76/Captura-de-tela-2025-09-05-215926.png)](https://postimg.cc/yDgkkks9)

Ao analisar os cabeçalhos dessa requisição, encontrei uma informação suspeita:
[![Captura-de-tela-2025-09-05-220627.png](https://i.postimg.cc/6Qg8FLfh/Captura-de-tela-2025-09-05-220627.png)](https://postimg.cc/Z9PYdNg9)

Dentro do campo secret_tipe, havia uma sequência codificada que parecia ser a flag. Para decodificá-la, utilizei a ferramenta [dCode](https://www.dcode.fr/en) obtendo o seguinte resultado:
[![Captura-de-tela-2025-09-05-221832.png](https://i.postimg.cc/MpwNbCk7/Captura-de-tela-2025-09-05-221832.png)](https://postimg.cc/N5NdQPjF)

#### Conclusão
Flag:
>`picoCTF{c00k1e_m0nster_l0ves_c00kies_73110ED1}`

Esse desafio foi uma ótima introdução às ferramentas de inspeção do navegador. Após alguns erros e tentativas, consegui compreender melhor como analisar requisições HTTP e explorar informações ocultas em páginas web — um conhecimento fundamental para segurança cibernética.