---
title: "Testando o que Construimos"
chapter: false
weight: 50
locale: "pt-BR"
---

## Testando o que Construimos
Agora que criamos tudo, agora podemos testar para garantir que não haja nada que precise ser consertado. Acompanhe para testar: 

1. Navegue até a página Ferramentas de mensagens da Web do Genesys Cloud Developer Center https://developer.genesys.cloud/devapps/web-chat-messenger
2. Certifique-se de fazer login na sua conta no canto superior direitot
3. Escolha a implantação do seu web messenger no menu suspenso e pressione Iniciar bate-papo (Chat)
4. Clique no ícone do web messenger que surge na caixa
![Messenger Icon](/images/messengerIcon.jpg)
5. Ao clicar no ícone e dizer 'Olá', o bot de contestação entrará em ação e lerá as transações e, em seguida, fornecerá a você a opção de qual loja contestar a transação
![Testing](/images/testing.jpg)
6. Após selecionar uma opção, nosso fluxo é configurado para rotear para uma fila. Em um cenário do mundo real, o Bot poderia processar tudo nos bastidores sem a necessidade de intervenção humana. 
7. Se desejar visualizar a parte do agente da transação, certifique-se de que seu usuário seja um membro da fila para a qual o fluxo de mensagens de entrada está roteando. Em seguida, coloque seu usuário na fila para aceitar a interação. Para obter mais informações sobre configuração de filas e como lidar com interações de mensagens de entrada, confira nosso workshop Genesys Cloud CX™️ Channel Setup: https://workshop.genesys.com/workshops/gride-demo/. 

Parabéns! Se isso funcionou para você, você concluiu o workshop com sucesso. 