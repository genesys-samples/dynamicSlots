---
title: "Construindo o fluxo do Genesys Bot"
chapter: false
weight: 20
locale: "pt-BR"
---

## Construindo o fluxo do Genesys Bot
Um Genesys Bot Flow é necessário para realizar nosso caso de uso de contestar uma transação. A razão pela qual precisamos de um fluxo de bot é para que possamos nos comunicar com o cliente por meio de um mecanismo NLU (conversacional) sobre qual transação eles acreditam ser fraudulenta. Siga estas etapas para criar seu fluxo de bot. Há também um vídeo que você pode assistir dessas etapas no final desta seção, se preferir. 

### Criando um Fluxo de Bot Digital

1. Navegue até Genesys Cloud CX Architect e escolha Fluxo do Bot no menu suspenso de fluxos de suporte
![Bot Flow](/images/botFlow.jpg)
    - nota: se você não vir isso, certifique-se de que os Fluxos de Genesys Bot estejam ativados em sua organização e que você tenha permissões para visualizá-los e editá-los.
2. Clique para criar um novo fluxo de bot. Dê um nome descritivo e, em Modelo, escolha Fluxo de Bot em Branco
![Create Bot Flow](/images/createBotFlow.jpg)

### Chamando a ação de dados (Data Action)
1. A primeira coisa que precisamos fazer no fluxo do bot é arrastar um bloco Chamar ação de dados (Call Data Action) como o início do nosso fluxo. 
2. No menu suspenso Categoria, escolha a integração do Web Services Data Actions que você configurou anteriormente
3. No menu suspenso Ação de dados, escolha a ação de dados que importamos anteriormente 
4. Crie variáveis para ambas as saídas de sucesso de transactions.Store e transactions.Value

Agora seu fluxo deve ficar assim:
![Data Action Config](/images/dataActionConfig.jpg)

### Configurando a Variável de Slot de Lista Dinâmica
1. Dentro do fluxo do bot, no lado esquerdo, navegue até Tipos de Slot. Clique para adicionar um novo tipo de slot
2. Dê um nome descritivo, como Lista de transações, e escolha Lista dinâmica como o tipo de slot
![Dynamic List](/images/dynamicList.jpg)
3. Agora navegue até Configurações de fluxo de bot
![Bot Flow Settings](/images/botFlowSettings.jpg)
4. Em Configurações de fluxo de bot, em Tipos de slots dinâmicos (Dynamic Slot Types), adicione a variável que você criou para as armazenar na coluna de valores
    - Em teoria, você também pode escolher o valor da transação como variável. Em um cenário do mundo real, você provavelmente desejaria que cada transação tivesse um ID exclusivo em caso de transações duplicadas.
    - Não teremos sinônimos em nosso exemplo
    ![Dynamic Slot Type](/images/dynamicSlotType.jpg)
5. Agora navegue até o botão Slots em Reconhecimento de idiomas naturais. Clique para adicionar um novo slot. Dê a ele um nome descritivo e escolha Existente como o Tipode  slot associado. Escolha o tipo de slot de lista dinâmica que acabamos de criar.
![Create Slot](/images/createSlot.jpg)

### Construindo o restante do fluxo do bot
Agora precisamos tornar essa contestação de transação conversacional. Já temos os dados que precisamos de nossa ação de dados e nossos slots estão todos configurados. Vamos usar isso para guiar nossa conversa.
1. Primeiro, precisamos ler as transações para o cliente. Para fazer isso, arraste um bloco Comunicar abaixo do caminho de Sucesso da ação de dados. Depois de adicionar este clique para configurar a comunicação à direita.
![Configure Communication](/images/configureCommunication.jpg)
2. No Construtor de sequências de comunicação, adicione algum texto que diga:
```Lamentamos que você ache que houve atividade fraudulenta em sua conta. Iremos ler suas transações mais recentes e você poderá nos dizer qual delas é fraudulenta.```
![Add Text](/images/addText.jpg)
3. Agora precisamos percorrer a matriz de armazenamentos e valores de transações e lê-los. Para fazer isso, adicione um bloco de loop sob esse bloco de comunicação. Certifique-se de dar ao índice de loop um nome de variável e defina Max Loop Count para uma variável que conte o número de itens em sua matriz de variáveis Transactions.store. Esta expressão significará que o loop só acontecerá para a quantidade de lojas que puxamos de volta naquele array.
    - A função Count examinará o número de valores em nossa matriz e retornará o número total agregado de itens na matriz. Por exemplo, teremos 3 transações em nosso array; assim, a função Count retornará um valor de 3.

> **A expressão será semelhante a - Count(inclua sua variável aqui)**

![Loop](/images/loop.jpg)
4. Agora arraste outro bloco Comunicar dentro do loop e clique para configurar a Comunicação.
![loop Communicate](/images/loopCommunicate.jpg)
5. Agora, precisamos ter uma expressão que use nosso loop para obter os armazenamentos e valores da transação na matriz e lê-los em ordem sequencial. No Construtor de sequências de comunicação, alterne para Expressão e cole esta expressão: 

![Expression](/images/expression.jpg)

##### **No trecho de código abaixo, certifique-se de que as variáveis de fluxo correspondam ao que você nomeou para suas variáveis, incluindo a diferenciação de maiúsculas e minúsculas!!!**

```
MakeCommunication(
  "$", 
  ToCommunication(GetAt(Flow.transactionValues, Flow.loopIndex)), 
  "at ", 
  ToCommunication(GetAt(Flow.transactionStores, Flow.loopIndex)))
```
  - A função GetAt localiza um valor em uma matriz com base em sua posição numérica. Em nosso cenário, procuramos os valores de transação e os armazenamentos de transação e localizamos esses valores com base na posição numérica que corresponde à contagem de loop. A tabela abaixo fornece um visual em nossa função acima. Estamos usando a contagem de loop para encontrar a posição numérica e, em seguida, retornar o valor da transação e o armazenamento da transação nessa posição numérica.
  - Aqui está um exemplo do que seria retornado com esta expressão com base na tabela abaixo: "$ 100 no Walmart". Em seguida, o segundo loop leria "$ 150 no Menards" e assim por diante.
  - Reserve um segundo para revisar a expressão para ter certeza de que isso faz sentido para você

  |Contador Loop | Posição Numérica | Transaction Value | Transaction store |
  | --- | --- | --- | --- |
  |0 | 0 | 100 | Walmart|
  |1 | 1 | 150 | Menards |
  |2 | 2| 200 | DSW |



6. Agora podemos pedir ao cliente para nos dizer cocontra qual loja ele gostaria de contestar a transação. Para fazer isso, arraste um bloco Solicitar Slot sob o bloco Communicar, mas fora do loop. À direita, selecione o slot que criamos anteriormente. Para a pergunta diga:
``` Com qual loja você deseja contestar a transação```
![Ask for Slot](/images/askForSlot.jpg)
7. Por fim, vamos habilitar os Botões de resposta rápida automática para nosso Bot. Navegue até Entrada do usuário em Configurações no lado esquerdo e verifique se os Botões de resposta rápida automática estão definidos como Ligado.
![Quick Replies](/images/quickReplies.jpg)
8. Agora basta clicar em publicar e você está pronto para passar para a próxima sessão! 

É importante saber que esse fluxo de bot que construímos não é típico pelo fato de nunca termos tido um bloco Solicitar intenção. Em nosso cenário, estamos fingindo que já identificamos que toda pessoa que entrar em contato com esse bot precisa contestar uma transação.

Se você deseja assistir a um vídeo dessas etapas acima, navegue aqui: https://youtu.be/AbOdknMqabY



