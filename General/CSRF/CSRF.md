# Como ocorre
O ataque funciona através da inclusão de um link ou script numa página que acede a um site no qual se sabe (ou se supõe) que o utilizador tenha sido autenticado.[5] Por exemplo, um usuário, Bob, pode estar a navegar num fórum de bate-papo onde outro usuário, Fred, postou uma mensagem. Suponha-se que Fred tenha criado um elemento da imagem HTML que faz referência a uma ação no site do banco de Bob (em vez de um arquivo de imagem), por exemplo,

<i> < img src="http://bank.example.com/withdraw?account=bob&amount=1000000&for=Fred" /> </i>

Se o banco de Bob mantém a sua informação de autenticação num cookie, e se o cookie não expirou, então a tentativa do browser de Bob de carregar a imagem irá submeter o formulário de levantamento com o seu cookie, assim, autorizando uma transação sem a aprovação de Bob. A falsificação de solicitação entre sites é um ataque do tipo Confused deputy contra um navegador Web. O deputy no exemplo do banco é o navegador Web de Bob que é confundido para fazer mau uso da autoridade de Bob na direção de Fred.

As seguintes características são comuns ao CSRF:

Envolvem sites que dependem de uma identificação do usuário
Exploram a confiança do site nessa identificação
Iludem o navegador do usuário para o envio de solicitações HTTP para um site de destino
Envolvem solicitações HTTP que têm efeitos colaterais
Os riscos são as aplicações Web que executam ações com base na confiança e autenticação das entradas dos usuários, sem exigir que o usuário autorize a ação específica. Um usuário que é autenticado por um cookie guardado no navegador web do usuário, sem saber, pode enviar um pedido HTTP a um site que confia no usuário e, assim, fazer uma ação indesejada.

Ataques CSRF em tags de imagem muitas vezes são feitas a partir de fóruns na Internet, onde os usuários têm permissão para postar imagens, mas não JavaScript.


https://www.treinaweb.com.br/blog/cross-site-request-forgery-csrf-e-abordagens-para-mitiga-lo/
