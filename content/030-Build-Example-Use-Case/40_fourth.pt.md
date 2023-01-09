---
title: "Criando a configuração e implantação do Web Messenger para teste"
chapter: false
weight: 40
locale: "pt-BR"
---

## Criando a configuração e implantação do Web Messenger para teste

Com o bot e o fluxo de mensagens criados, estamos prontos para criar uma configuração e implantação do messenger. Se você já criou isso e gostaria de usá-lo, sinta-se à vontade para simplesmente apontar sua implantação do Web Messenger para o fluxo de mensagens de entrada do Architect que acabamos de criar. 

### Configuração do Web Messenger
A configuração do web messenger é onde definiremos visibilidade, aparência e outros vários elementos de configuração de como o messenger se comportará.

No aplicativo principal do Genesys Cloud, navegue até Administração > Configurações do Messenger e crie um novo (Nova Configuração).

Embora existam muitas opções de configuração, forneceremos apenas um nome e selecionaremos nosso idioma padrão (rolando até a parte inferior da guia de aparência) para este workshop, conforme visto abaixo:

![Call Bot Flow](/images/Messageconfigname.PNG)

![Call Bot Flow2](/images/messageconfiglanguage.PNG)

Para obter uma explicação das opções de configuração adicionais, você pode revisar este artigo do centro de recursos - https://help.mypurecloud.com/articles/configure-messenger/

Agora você pode salvar a nova versão.

### Instalação do Web Messenger

No aplicativo principal do Genesys Cloud, navegue até Administração > Implantações do Messenger e crie uma Nova Implantação.

A implantação é onde vincularemos nossa configuração de mensageiro ao nosso fluxo de mensagens (e, finalmente, nosso fluxo de bot).

1. Dê um nome à sua configuração
2. Habilite o Status
3. Selecione sua configuração (você procurará a configuração do web messenger que acabamos de criar)
4. Permitir em todos os domínios (Isso vai tornar o teste mais simples)
5. Selecione o fluxo do Architect da Mensagem de Entrada

Depois de configurar essas opções, sua implantação deve ficar assim: 

![Message Deployment](/images/messagedeployment.PNG)