# 🚀 Projeto de Arquitetura de Nuvem: Análise de Crédito

![Bootcamp Code Girls - DIO](https://img.shields.io/badge/Bootcamp-Code%20Girls%20DIO-blueviolet)

---

### 📋 Introdução

Este repositório documenta a concepção de uma arquitetura de nuvem para resolver um problema de negócio crucial: a automação da **análise de crédito**. Tradicionalmente, este processo é lento, manual e propenso a falhas, envolvendo a coleta e validação de documentos de forma ineficiente, o que impacta diretamente a experiência do cliente e a agilidade da instituição financeira.

Para solucionar esse desafio, o projeto propõe e detalha uma arquitetura de nuvem usando a **AWS**. O objetivo é transformar um fluxo manual em um sistema automatizado, escalável e seguro. Este projeto, desenvolvido como parte do bootcamp **Code Girls** da **Digital Innovation One (DIO)**, demonstra a aplicação de conhecimentos em design de soluções para construir um sistema robusto e eficiente que processa, analisa e valida documentos de forma autônoma. O material serve como uma especificação técnica detalhada, apresentando o fluxo de trabalho e as configurações hipotéticas necessárias para a implementação da solução.

---

### 🎯 Objetivos

O escopo deste projeto foi definido para atingir os seguintes objetivos de aprendizado:

* **Projetar uma arquitetura de nuvem** para resolver um problema de negócio complexo.
* **Documentar processos e fluxos** de forma clara e estruturada.
* **Demonstrar competência** no uso de serviços AWS para a construção de soluções robustas.

---

### 🧠 Conhecimentos Técnicos

A elaboração desta arquitetura de solução demonstra proficiência em conceitos-chave de computação em nuvem, incluindo:

* **Design de Soluções na Nuvem**: Habilidade de traduzir requisitos de negócio em uma arquitetura técnica funcional e otimizada.
* **Arquitetura Serverless e Orientada a Eventos**: Entendimento de como usar serviços como **Amazon S3** e **AWS Lambda** para criar fluxos de trabalho que reagem a eventos em tempo real.
* **Orquestração de Workflows**: Conhecimento do uso do **AWS Step Functions** para gerenciar, monitorar e garantir a execução de processos distribuídos e de várias etapas.
* **Segurança e Redes**: Compreensão de boas práticas de segurança, como a segmentação de rede usando **VPCs**, **Subnets privadas** e **Security Groups** para proteger recursos.
* **Integração de Serviços**: Capacidade de interconectar diferentes serviços da AWS (S3, Lambda, Step Functions, EC2) de forma coesa e eficiente.

---

### ⚙️ Metodologia

A metodologia adotada para este projeto consistiu na elaboração de um design de arquitetura que soluciona o problema de negócio de forma eficiente e resiliente. A solução foi projetada utilizando os princípios de arquitetura de nuvem da AWS, combinando serviços gerenciados e um fluxo de trabalho orquestrado.

#### Diagrama de Arquitetura

O diagrama a seguir ilustra a arquitetura proposta para a automação da análise de crédito, servindo como blueprint para a implementação do sistema.

![Diagrama da Arquitetura de Análise de Crédito](images/diagrama-de-arquitetura.png)

#### Fluxo do Processo de Análise de Crédito

O fluxo de trabalho foi concebido para automatizar a análise de documentos de clientes, utilizando uma abordagem **orientada a eventos**. O processo é iniciado com o upload de um documento em um bucket do **Amazon S3**, que dispara uma função **AWS Lambda**. Esta função, por sua vez, inicia um workflow orquestrado pelo **AWS Step Functions**. Dentro deste workflow, diferentes tarefas são executadas, como o uso de uma instância **Amazon EC2** para processamento intensivo de dados. O resultado final é armazenado de forma segura e notificado aos sistemas internos.

#### Detalhamento Técnico e Configurações Hipotéticas

Para a implementação da arquitetura, as seguintes configurações seriam consideradas:

* **Amazon S3**: Dois buckets seriam criados para segregar os dados de entrada (`analise-credito-inbound`) e os resultados finais (`analise-credito-results`). Uma **notificação de evento** seria configurada no bucket de entrada para acionar a função Lambda.
* **AWS Lambda**: Uma função seria provisionada para atuar como **trigger**, recebendo a notificação do S3 e iniciando o workflow do Step Functions. Outras funções seriam utilizadas para tarefas mais leves, como a integração com APIs.
* **AWS Step Functions**: Uma **máquina de estados** seria projetada para orquestrar as etapas do processo, incluindo a invocação de funções Lambda e a execução de tarefas em instâncias EC2.
* **Amazon EC2**: Uma instância de computação seria utilizada para executar modelos de scoring de crédito ou outras cargas de trabalho pesadas, operando em uma **`Private Subnet`** para garantir a segurança.
* **VPC, Subnets e Security Groups**: A infraestrutura de rede seria segmentada em `Public` e `Private Subnets`. **Security Groups** seriam configurados para permitir a comunicação segura apenas entre os serviços necessários, garantindo que a instância EC2 não esteja exposta diretamente à internet.

---

### ✅ Conclusão

A concepção desta arquitetura demonstra a capacidade de traduzir um problema de negócio em uma solução técnica viável e robusta na nuvem. O uso de **serviços gerenciados** e a **separação de responsabilidades** entre os componentes garantem que a solução seja **escalável, segura e de baixo custo de manutenção**. Este projeto solidifica o conhecimento em design de sistemas distribuídos e a aplicação de boas práticas de arquitetura de nuvem.
