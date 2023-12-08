# arch_apostas


<!-----



Conversion time: 0.468 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β35
* Thu Dec 07 2023 17:29:03 GMT-0800 (PST)
* Source doc: arch
----->




* **Servidor de aplicação**
    * Utilizado para controlar a regra de negócio do sistema de apostas
    * Será uma aplicação distribuída em micro serviços com kubernetes
    * Um serviço da AWS como EKS pode ser utilizado para deploy 
* **Banco de dados Relacional**
    * Múltiplos serviços de banco de dados serão utilizados para armazenar dados gerais da aplicação, promoções, jogos, times, eventos
    * Banco de dados postgresql será utilizado em muitos dos serviços
    * Os serviços de RDS serão utilizados e estarão disponíveis na private subnet como banco para os micro serviços da aplicação.
* **Banco de dados NoSql **
    * O banco Dynamo DB da Amazon será utilizado como uma forma de acesso rápida a dados que precisam ser atualizados em tempo real.
    * Utilizando a disponibilidade do serviço da Amazon para o gerenciamento de odds. 
* **Disponibilidade de dados**
    * Para a distribuição de dados em tempo real, será utilizado protocolo WebSocket para os serviços de odds de apostas devido a necessidade de maior disponibilidade de recurso e dado atualizado. 
    * Será utilizado Amazon CloudFront para disponibilização dos dados para os clientes do serviço. 
* **Load Balancer**
    * Utilizado para distribuição de carga entre os serviços e entre zonas diferentes de disponibilidade em nuvem.
* **Disponibilidade de serviços**
    * Será utilizado o serviço Amazon API Gateway para disponibilizar os serviços, principalmente para disponibilização dos disponíveis através de WebSocket.
    * Buscando gerenciar a disponibilidade da aplicação, o API Gateway dará acesso aos serviços de API disponíveis na aplicação.
* **Ambiente de deploy**
    * Buscando uma aplicação serverless, com grande disponibilidade e capacidade de escalabilidade flexível, o ambiente da Amazon Cloud será utilizado para o deploy e gestão da aplicação.
    * Outros serviços menos relevantes do ambiente AWS, como subnets e ferramentas de mensageria, serão utilizados para completar a arquitetura da aplicação.
* **Private subnet**
    * Utilizando micro serviços é possível criar uma caixa preta entre os serviços e garantir comunicação segura no ambiente como um todo evitando necessidade de autenticação entre os serviços e então aumento de latência.
    * Essa rede

[https://github.com/Castrozan/arch_apostas/blob/main/Arch%20Apostas.html](https://github.com/Castrozan/arch_apostas/blob/main/Arch%20Apostas.html)



* **Elaborar o plano de equipe necessário para o desenvolvimento da arquitetura**
    * **Perfis necessários:** Dev Front End, Dev Back End, Arquiteto de Softwares, DBA, DevOps, Scrum Master, PO, PM.
    * **Metodologia de desenvolvimento a ser aplicada**
        * **Quais cerimônias? **Daily
        * **Quais documentos?** Jira
        * **Qual framework?** Scrum

**Plano de qualidade para o produto**

Utilizamos Attribute-Driven Design (ADD) para identificar e priorizar atributos de qualidade importantes para um sistema antes de se envolver na concepção detalhada da arquitetura. No caso de uma aplicação de apostas esportivas, existem várias razões pelas quais a utilização do ADD pode ser benéfica:

**Processo de Attribute-Driven Design para uma Aplicação**



* **Identificação de Requisitos e Partes Interessadas:**
    * **Entendimento do Negócio: **
        * Visita em sites de aposta identificando similaridades e core business
    * **Identificação de Atributos de Qualidade:**
        * Identificar partes interessadas para identificar atributos de qualidade críticos para a aplicação (desempenho, disponibilidade, segurança, etc.).
        * Múltiplos usuários simultâneos, necessidade de alta frequência de atualização de dados.
* **Especificação de Táticas Arquiteturais:**
    * **Seleção de Táticas:**
        * Escolher táticas arquiteturais específicas para atender aos atributos de qualidade.
        * Exemplos: Caching para desempenho, redundância para disponibilidade, disponibilidade com WebSocket.
* **Design Preliminar:**
    * **Estrutura Inicial:**
        * Criar uma estrutura arquitetural inicial com base nas táticas escolhidas.
        * Escolhemos os principais serviços e bancos de dados.
        * Identificar componentes-chave e suas interações.
* **Refinamento da Arquitetura:**
    * **Ajustes e Otimizações:**
        * Incorporar feedback das revisões e ajustar a arquitetura conforme necessário.
        * Otimizar a arquitetura para melhor atender aos atributos de qualidade prioritários.
* **Documentação:**
    * **Documentação Detalhada:**
        * Elaborar documentação detalhada da arquitetura, destacando decisões arquiteturais, táticas escolhidas e justificativas.
        * Incluir diagramas, descrições de componentes e interfaces.
* **Implementação e Testes:**
    * **Desenvolvimento:**
        * Implementar o sistema de acordo com a arquitetura definida.
    * **Testes de Atributos de Qualidade:**
        * Conduzir testes específicos para validar os atributos de qualidade identificados.
    * **Monitoramento e Melhoria Contínua:**
        * Implementar monitoramento contínuo para avaliar o desempenho e a confiabilidade em ambientes de produção.
