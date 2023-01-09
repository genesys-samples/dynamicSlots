---
title: "Criando a ação de dados"
chapter: false
weight: 10
locale: "pt-BR"
---

## Criando a ação de dados (Data Action)

Para o workshop, não podemos esperar que todos tenham acesso ao mesmo sistema de terceiros para recuperar nossa lista dinâmica, então criamos uma API simulada para todos usarem. Essa API recuperará uma lista do histórico de transações de uma pessoa fictícia. Você não especificará nenhuma entrada; a ação de dados (Data Action) simplesmente atingirá o endpoint da API e retornará o mesmo histórico de transações para cada consulta. 

Precisamos importar esta ação de dados para sua instância do Genesys Cloud CX para que você possa consultar o histórico de transações em sua instância. Siga as etapas abaixo para importar a ação de dados: 

1. Navegue até o console de administração do Genesys Cloud CX e localize as integrações
2. Crie uma nova integração do tipo Web Services Data Actions
![Web Services Data Actions](/images/webServicesDataActions.jpg)
3. Dê à integração um nome descritivo. **Nota:** Você não precisa se preocupar em configurar credenciais (Oath) para esta integração porque estamos apenas usando uma API Simulada que não requer credenciais
4. Clique no botão Ações em Integrações na Adminstracão do Genesys Cloud CX
5. Navegue até este repositório github e siga as etapas no arquivo: ReadMe https://github.com/genesys-samples/DynamicListSlotDataAction 
6. Clique em Importar na página Ações e escolha o arquivo JSON que você acabou de baixar. Na categoria de integração, escolha a integração de ação de dados de serviços da Web que acabamos de configurar
![Import Data Action](/images/importDataAction.jpg)
7. Depois de importar a ação de dados, navegue até a ferramenta de teste e clique em Executar ação. Você deve obter esta resposta.
![Data Action Test](/images/dataActionTest.jpg)
8. Clique em "Salvar e Publicar"

Agora você está pronto para chamar essa ação de dados em um fluxo de Bot Genesys.