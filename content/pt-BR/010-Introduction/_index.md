---
title: "Introdução"
chapter: true
weight: 10
locale: "pt-BR"
---

### Revisão da terminologia dos fluxo de Bots com Genesys Dialog Engine

Antes de definirmos os tipos de Slot de Lista Dinâmica, vamos relembrar a terminologia dos fluxos de bots do Genesys Dialog Engine. Então, seremos capazes de vincular como os slots dinâmicos se encaixam na imagem. 

Aqui estão alguns dos principais termos a serem conhecidos com os fluxos de bot do Genesys Dialog Engine: 

- Intenção - As intenções descrevem uma meta ou tarefa que os usuários desejam realizar. Por exemplo, "Reservar um quarto" ou "Verificar o saldo da conta"
- Enunciados - Um enunciado (utterance) é um pedido falado pelo usuário. São frases que os usuários usam para descrever o que desejam fazer. Os enunciados são mapeados para intenções, de modo que, quando um enunciado é falado, ele dispara o item correspondente. Por exemplo, se a intenção for "Reservar um quarto", um enunciado pode ser "Gostaria de reservar um quarto para esta noite"
- Slots - Slots são pedaços de informação que podem ser usadas para ajudar a cumprir a intenção. No exemplo de "Gostaria de reservar um quarto para esta noite", a palavra "hoje" está preenchendo uma informação chave; a data da estadia. A data da estadia éum Slot, um espaço, uma variável chave a ser preenchida para conhecermos melhor a intenção. Podemos continuar pedindo outro slot; bucando dados sobre o tipo de quarto que eles precisam para sua estadia.
- Tipos de Slot - Um tipo de slot define como o Bot processa as informações disponíveis no slot identificado. Cada slot deve ser mapeado para um tipo de slot. No exemplo acima para coleta da data da estadia, um tipo de slot pode ajudar a definir que só estamos aceitando valores do cliente que sejam datas. Portanto, se o Bot perguntar ao cliente em que data ele deseja ficar, o cliente não poderá dizer "pizza" porque o tipo de slot não aceitará nada além de uma data.

Slots e tipos de slots são o foco do workshop de hoje, então vamos nos aprofundar um pouco mais.

### Slot & Tipos de Slot
There are three different types of Slot Types that you can create:

- Expressões Regulares - A expressão regular é usada para identificar padrões em enunciados (utterances) que correspondem a uma sequência específica de caracteres. Comumente conhecido como REGEX, este é um método amplamente utilizado. Para dar um exemplo de uso de um tipo de slot REGEX, pense nos números das contas. Se você deseja aceitar apenas uma sequência de números com 10 a 12 dígitos, por exemplo, pode ter uma expressão REGEX que permita apenas essa sequência de caracteres.
- Listas - Este é o mais fácil de entender porque é exatamente o que parece. Pense em nosso exemplo acima sobre o tipo de quarto que alguém poderia reservar em um hotel. O hotel provavelmente oferece apenas cerca de 4 a 8 tipos de quartos, portanto, este é um exemplo perfeito do uso de um tipo de slot de lista. Você também pode incluir sinônimos para as palavras em sua lista. 
- Lista Dinâmica - Embora sejam semelhantes às listas, as listas dinâmicas são úteis se o seu bot contiver muitos valores para um tipo de slot e você não quiser adicioná-los manualmente e atualizá-los manualmente à medida que sua lista muda. Eles também são úteis quando os valores da lista não são conhecidos no momento da criação do bot ou se a lista for específica para cada cliente individual. 