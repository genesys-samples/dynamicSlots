---
title: "Criando o fluxo de  Mensagem de Entrada"
chapter: false
weight: 30
locale: "pt-BR"
---

## Criando o fluxo de  Mensagem de Entrada

Com nosso fluxo de bot construído, precisaremos configurar um fluxo de mensagens de entrada que roteia os clientes para esse fluxo de bot.

Dentro do Architect, mude o tipo de fluxo "Mensagem de Entrada"

![image](/images/messageflowselect.PNG)

Selecione Adicionar e forneça um nome e uma descrição ao seu fluxo. Você também pode fornecer uma fila de transferência de evento de erro que permitirá processar eventos de erro normalmente e permitir que as interações continuem a fluir para uma fila no caso de uma falha lógica.

![Create Message Flow](/images/messageflowcreate.PNG)

Nesse fluxo de mensagens, é possível processar a lógica pré-bot, como pesquisas de ação de dados. Para o objetivo deste workshop, simplesmente adicionaremos um bloco de lógica de de chamada de fluxo de bot.

Dentro da caixa de ferramentas, expanda "Bot" e arraste uma caixa "CHamar Fluxo de Bot Digital" acima do bloco de desconexão padrão dentro do construtor de fluxo.

![Call Bot Flow](/images/messageflowbot.PNG)

Dentro das opções Chamada de Fluxo de Bot que se abrem no lado direito, podemos selecionar nosso fluxo de bot Dynamic Slot que acabamos de construir. Também podemos definir slots de entrada e saída.
  * As entradas nos permitem enviar informações que já coletamos para um fluxo de bot, por exemplo, se executarmos uma ação de dados no fluxo de mensagens e encontrarmos um caso aberto, poderíamos enviar esse caso para o bot como um slot já preenchido. Não precisamos de entradas para este workshop.

  * As saídas nos permitem armazenar dados que o bot coletou do cliente para tomar mais decisões de roteamento ou script do agente. Exemplo; o cliente usa o bot para selecionar sobre o que está nos contatando, podemos usar essas informações para encaminhar para diferentes filas ou fornecer scripts diferentes para os agentes. Também não precisaremos de saídas para este exemplo.

![Call Bot Flow Options](/images/messageflowbotoptions.PNG)

O último item que adicionaremos é uma transferência para o bloco DAC. Isso não será um requisito para este workshop; no entanto, permitirá testar melhorias futuras.

Na caixa de ferramentas, localize "Transferir para ACD" e arraste-o para baixo do bloco "Chamar Fluxo de Bot Digital" e selecione sua fila. Agora você pode publicar este fluxo de mensagens de entrada.

Se você tiver experiência com o Architect, sinta-se à vontade para adicionar qualquer outra lógica que desejar.

![Transfer to ACD](/images/messageflowacd.PNG)