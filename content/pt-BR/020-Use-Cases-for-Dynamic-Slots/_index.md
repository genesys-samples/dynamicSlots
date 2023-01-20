---
title: "Casos de Uso para Slots de Listas Dinâmicas - Dynamic List Slots"
chapter: true
weight: 10
locale: "pt-BR"
---

## Casos de Uso

Os slots dinâmicos realmente abrem as portas para a automação total dentro de um bot. Historicamente, um administrador teria que modificar quais slots um bot captura quando as ofertas ou serviços de sua organização mudam. Slots dinâmicos permitem que o bot construa sua lista de slots por interação a partir de uma fonte de dados interna ou externa. Isso significa que um cliente pode sempre interagir com os dados mais atualizados e os administradores não precisam construir as mudanças manualmente. Aqui estão alguns exemplos de casos de uso:

**Caso de Uso 1:** Uma companhia de seguros expande suas ofertas para incluir tipos e pacotes de seguros adicionais. Em vez de um administrador adicionar esses itens adicionais à lista de slotss, a API que está puxando os serviços atuais verá automaticamente as novas ofertas e as capturará como slots aceitos dentro do fluxo do bot.

**Caso de Uso 2:** Um cliente está usando um menu de autoatendimento para pedir uma pizza, mas a pizzaria ficou sem uma cobertura específica. Normalmente, isso resultaria em um callback para o cliente para informá-lo de que a cobertura não está disponível, no entanto, os slots dinâmicos permitiriam que o bot não reconhecesse mais isso como um slot aceito e pudesse recomendar outra coisa.

**Caso de Uso 3:** Um cliente está entrando em contato com um banco para contestar uma cobrança em sua conta. Os slots dinâmicos permitem que o bot baixe todas as transações recentes e as reconheça como slots referenciados. O bot pode ler as várias transações de volta para o cliente e permitir que ele diga qual transação acredita ser fraude. Para criar isso sem slots dinâmicos, um administrador teria que criar um fluxo complexo para iterar as transações do cliente e permitir que o cliente agisse a partir delas.

Para este workshop, vamos construir o Caso de Uso 3 em seu próprio ambiente.