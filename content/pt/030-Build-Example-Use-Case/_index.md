---
title: "Criar Caso de Uso de Contestação de Transação"
chapter: true
weight: 30
locale: "pt-BR"
---

## Criar Caso de Uso de Contestação de Transação

Agora chegou a hora de criar um fluxo de bot usando um slot de lista dinâmica. Como não podemos esperar que todos tenham acesso à mesma plataforma externa para obter uma matriz de dados, criamos uma API simulada que ajudará a realizar nosso caso de uso. 

O caso de uso que desenvolveremos hoje será para contestar uma transação em um banco. Pense nos 3 tipos de slots que abordamos na introdução: lista, lista dinâmica e expressão regular. Suas transações mais recentes certamente são uma lista, mas são dinâmicas porque são diferentes para cada pessoa e frequentemente você adiciona novas transações à lista (algumas pessoas mais do que outras). Portanto, esta é uma oportunidade de usar um tipo de slot de lista dinâmica que extrai as transações mais recentes por meio de uma chamada de API e usa essa lista dinâmica como a lista para o tipo de slot. 

Vamos dividir isso em 5 etapas: 

1. Criar a ação de dados (data action)
2. Construir o fluxo do Genesys Bot - *este é o foco do nosso workshop* 
3. Construir um fluxo de mensagem de entrada
4. Criar uma configuração e instalação de Web Messenger para testes
5. Testando o que Construimos