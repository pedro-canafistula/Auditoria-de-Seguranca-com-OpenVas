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

# Etapas do Projeto

## 1. **Configuração do Ambiente**
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

## Configuração da Rede NAT
Após configurar as VMs, foi criada uma rede NAT dedicada para isolar o ambiente de testes. Essa configuração permite que as VMs se comuniquem entre si e, ao mesmo tempo, mantém o ambiente de testes separado da rede doméstica, garantindo maior segurança e controle.

### Criação da Rede NAT:

No VirtualBox, foi configurado o adaptador de rede de cada VM para utilizar o modo NAT.<br>
Isso permite que as VMs tenham acesso à internet, se necessário, mas mantém as operações de rede isoladas da rede doméstica.

![image](https://github.com/user-attachments/assets/c8501fcf-5280-4832-8a4c-7d5a4e926224)


### Configuração dos Adaptadores de Rede:

Para cada VM, foi adicionado um adaptador de rede NAT através das configurações de rede da VM no VirtualBox.<br>
A configuração foi replicada em todas as VMs envolvidas no projeto para garantir que todas compartilhem a mesma rede e possam se comunicar entre si.

![image](https://github.com/user-attachments/assets/1e031b3a-1805-42c1-b766-de296e541b1c)


### Teste de Comunicação:

Após a configuração, foi realizada uma verificação para garantir que todas as VMs na rede NAT pudessem se comunicar adequadamente.<br>

![image](https://github.com/user-attachments/assets/710385b9-7205-4b6f-be0b-318d276f1e2e)


Essa configuração proporciona um ambiente controlado e seguro, essencial para a realização de testes de vulnerabilidades sem comprometer a segurança da rede doméstica.


## 2. **Instalação do OpenVAS no Kali Linux**
Nesta etapa, foi realizada a instalação e configuração do OpenVAS em uma máquina virtual rodando Kali Linux. A seguir, detalhamos cada passo do processo.

### Passo 1: Atualização do Sistema
Primeiro, atualizamos o sistema para garantir que o Kali Linux está com todos os pacotes atualizados.<br>
Para fazer isso rodamos o comando: <code>sudo apt update && sudo apt upgrade -y</code>

![img1](https://github.com/user-attachments/assets/66349858-c81c-4d82-bbd7-36e7c7ed5c3d)


### Passo 2: Instalação do OpenVAS <br>
Instalamos o OpenVAS diretamente dos repositórios do Kali Linux.<br>
Para fazer rodamos o comando: <code>sudo apt install openvas -y</code> <br>

![img2](https://github.com/user-attachments/assets/e1d48ea6-8fe9-4b4e-8c1a-b64829107f4a)


### Passo 3: Configuração Inicial do OpenVAS
Em seguida, configuramos o OpenVAS com o comando:<code>sudo gvm-setup</code> <br>

Este comando configura o ambiente e baixa os feeds de vulnerabilidades necessários.<br>

![img3](https://github.com/user-attachments/assets/62c2d53e-449a-4d5e-957b-34e05c13b977)


### Passo 4: Verificação do Status do OpenVAS
Após a configuração, verificamos se todos os serviços do OpenVAS estão funcionando corretamente:
<code>sudo gvm-check-setup</code> <br>

![img4](https://github.com/user-attachments/assets/91c58b25-855f-4cee-83c6-8854bdbe1618)


### Passo 5: Iniciar o OpenVAS
Iniciamos o OpenVAS com o comando: <code>sudo gvm-start</code>
O OpenVAS estará acessível via interface web no navegador, em https://localhost:9392.<br>

![img5](https://github.com/user-attachments/assets/a180be81-b242-4baa-bc18-834b318ed2b7)



### Passo 6: Acessar o OpenVAS via Navegador 
Acessando o OpenVAS através do navegador em https://localhost:9392 e fazendo login com as credenciais geradas (admin e a senha gerada durante a configuração) veremos a seguinte tela:<br>

![img6](https://github.com/user-attachments/assets/94e87bc4-9c45-4b7c-9328-a3161b15b23e)

Com a instalação e configuração do OpenVAS concluídas, o ambiente está preparado para realizar testes de vulnerabilidades. A partir daqui, o foco será a execução de scans nas máquinas virtuais configuradas, avançando para a próxima fase do projeto.


<!--
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


