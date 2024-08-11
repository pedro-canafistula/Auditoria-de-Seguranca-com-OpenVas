# Auditoria de Seguranca com OpenVas

## Objetivo

Este projeto tem como objetivo realizar uma auditoria de segurança em uma rede local utilizando o OpenVAS.A meta é identificar e mitigar vulnerabilidades, garantindo um ambiente seguro e confiável.

## Ferramentas e Tecnologias
<!--
- **OpenVAS:** Utilizado para análise de vulnerabilidades e geração de relatórios de segurança.
- **Ubuntu Server:** Servidor configurado para hospedar o OpenVAS e realizar os scans.
- **Apache2:** Servidor web utilizado como parte do ambiente de teste.
- **VMware/VirtualBox:** Para simular a rede local e os diferentes ambientes de teste.
-->
## Descrição do Projeto
Este projeto tem consiste em configurar e testar um ambiente de rede para auditoria de segurança utilizando a ferramenta OpenVAS. O ambiente foi criado com múltiplas máquinas virtuais para simular uma rede corporativa realista, onde foram implementados diversos serviços, como servidor web, banco de dados e sistemas operacionais diversos.

## Etapas do Projeto

### 1. **Configuração do Ambiente**
A primeira etapa do projeto foi dedicada à configuração do ambiente de rede virtual, que serve como base para a auditoria de segurança. Foram criadas e configuradas diversas máquinas virtuais (VMs) com diferentes sistemas operacionais e serviços, simulando um ambiente corporativo realista.

VM 1: Windows 7
   
   * Utilizada para simular um ambiente de trabalho comum em empresas.
   * Configuração básica do sistema operacional, com foco em simular vulnerabilidades típicas de máquinas de usuários.
   
VM 2: Lubuntu

   * Escolhida por ser uma distribuição Linux leve, representando máquinas de usuários com baixo consumo de recursos.
   * Configuração de rede e preparação para participação em testes de segurança.

VM 3: Servidor Web

   * Configurado como um servidor web utilizando o Apache2 no Ubuntu Server.
   * Servidor sem interface gráfica para otimizar o desempenho.
   * Configuração de diretórios e permissões para garantir a segurança e o funcionamento adequado do serviço web.

VM 4: Servidor de Banco de Dados

   * Configurada em uma máquina virtual separada, com um sistema operacional Ubuntu Server.
   * Banco de dados MySQL instalado e configurado.
   * Criação de um usuário específico para o projeto e atribuição de permissões adequadas para operações de teste.

Após a configuração das máquinas, foram realizados testes para garantir que cada serviço e máquina virtual estavam operando corretamente dentro da rede simulada. Com o ambiente devidamente configurado, a próxima etapa envolve a execução dos testes de segurança utilizando o OpenVAS.

![image](https://github.com/user-attachments/assets/ca2776d1-00d3-4c24-88ec-a81d9d3302c6)


<!--
2. **Execução de Scans de Vulnerabilidades:**
   - Definição de escopos e políticas de scan.
   - Execução dos scans e coleta de dados.

3. **Análise dos Resultados:**
   - Interpretação dos resultados obtidos pelo OpenVAS.
   - Identificação das vulnerabilidades críticas e propostas de mitigação.

4. **Relatório Final:**
   - Geração de um relatório detalhado com as vulnerabilidades encontradas.
   - Recomendações para correções e boas práticas de segurança.
-->
## Habilidades Desenvolvidas
<!--
- Análise de vulnerabilidades em redes locais.
- Configuração e operação de ferramentas de segurança como OpenVAS.
- Interpretação de relatórios de segurança e proposta de soluções.
- Configuração de servidores e ambientes de teste em VMs.
-->
## Resultados
<!--
[Descreva os resultados alcançados com o projeto - Substitua esta linha]

A auditoria realizada permitiu a identificação de várias vulnerabilidades, das quais as mais críticas foram mitigadas com sucesso. O ambiente analisado passou a seguir as melhores práticas de segurança recomendadas.
-->
## Referências
<!--
[Links e documentos relevantes utilizados no projeto - Substitua esta linha]
-->
---


