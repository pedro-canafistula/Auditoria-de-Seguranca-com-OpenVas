# Auditoria de Seguranca com OpenVas

## Objetivo

Este projeto tem como objetivo realizar uma auditoria de segurança em uma rede local utilizando o OpenVAS.A meta é identificar e mitigar vulnerabilidades, garantindo um ambiente seguro e confiável.

## Ferramentas e Tecnologias
Durante o projeto, as seguintes ferramentas e tecnologias foram utilizadas:

- VirtualBox: Software de virtualização utilizado para criar e gerenciar as máquinas virtuais que compõem o ambiente de teste.

- Ubuntu Server: Sistema operacional utilizado para hospedar o servidor web e banco de dados no ambiente de teste, proporcionando um cenário realista para as varreduras de vulnerabilidades.

- Windows 7: Sistema operacional alvo das varreduras, utilizado para analisar vulnerabilidades específicas de sistemas legados.

- Lubuntu: Versão leve do Ubuntu, usada como uma máquina virtual adicional no ambiente de teste.

- Kali Linux: Distribuição Linux focada em testes de segurança, utilizada para instalar e configurar o OpenVAS, além de executar varreduras de vulnerabilidades.

- OpenVAS: Ferramenta principal de varredura de vulnerabilidades, utilizada para identificar falhas de segurança em diferentes sistemas e serviços.

- Apache2: Servidor web configurado no Ubuntu Server, simulado como alvo de testes de segurança para detecção de vulnerabilidades.

- Nmap: Ferramenta utilizada para escanear a rede e identificar os dispositivos ativos, criando uma lista de IPs para as varreduras do OpenVAS.

- MySQL: Banco de dados configurado como parte do ambiente de teste, permitindo a prática de varredura de vulnerabilidades em um ambiente completo.

  
## Descrição do Projeto
Este projeto tem consiste em configurar e testar um ambiente de rede para auditoria de segurança utilizando a ferramenta OpenVAS. O ambiente foi criado com múltiplas máquinas virtuais para simular uma rede corporativa realista, onde foram implementados diversos serviços, como servidor web, banco de dados e sistemas operacionais diversos.

# Etapas do Projeto

## 1. **Configuração do Ambiente**
A primeira etapa do projeto foi dedicada à configuração do ambiente de rede virtual, que serve como base para a auditoria de segurança. Foram criadas e configuradas diversas máquinas virtuais (VMs) com diferentes sistemas operacionais e serviços, simulando um ambiente corporativo realista.

### 1.1- Configuração das VMs

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

### 1.2- Configuração da Rede NAT
Após configurar as VMs, foi criada uma rede NAT dedicada para isolar o ambiente de testes. Essa configuração permite que as VMs se comuniquem entre si e, ao mesmo tempo, mantém o ambiente de testes separado da rede doméstica, garantindo maior segurança e controle.

#### 1.2.1- Criação da Rede NAT:

No VirtualBox, foi configurado o adaptador de rede de cada VM para utilizar o modo NAT.<br>
Isso permite que as VMs tenham acesso à internet, se necessário, mas mantém as operações de rede isoladas da rede doméstica.

![image](https://github.com/user-attachments/assets/c8501fcf-5280-4832-8a4c-7d5a4e926224)


#### 1.2.2- Configuração dos Adaptadores de Rede:

Para cada VM, foi adicionado um adaptador de rede NAT através das configurações de rede da VM no VirtualBox.<br>
A configuração foi replicada em todas as VMs envolvidas no projeto para garantir que todas compartilhem a mesma rede e possam se comunicar entre si.

![image](https://github.com/user-attachments/assets/1e031b3a-1805-42c1-b766-de296e541b1c)


#### 1.2.3-Teste de Comunicação:

Após a configuração, foi realizada uma verificação para garantir que todas as VMs na rede NAT pudessem se comunicar adequadamente.<br>

![image](https://github.com/user-attachments/assets/710385b9-7205-4b6f-be0b-318d276f1e2e)


Essa configuração proporciona um ambiente controlado e seguro, essencial para a realização de testes de vulnerabilidades sem comprometer a segurança da rede doméstica.


## 2. **Instalação do OpenVAS no Kali Linux**
Nesta etapa, foi realizada a instalação e configuração do OpenVAS em uma máquina virtual rodando Kali Linux. A seguir, detalhamos cada passo do processo.

### 2.1- Atualização do Sistema
Primeiro, atualizamos o sistema para garantir que o Kali Linux está com todos os pacotes atualizados.<br>
Para fazer isso rodamos o comando: <code>sudo apt update && sudo apt upgrade -y</code>

![img1](https://github.com/user-attachments/assets/66349858-c81c-4d82-bbd7-36e7c7ed5c3d)


### 2.2- Instalação do OpenVAS <br>
Instalamos o OpenVAS diretamente dos repositórios do Kali Linux.<br>
Para fazer rodamos o comando: <code>sudo apt install openvas -y</code> <br>

![img2](https://github.com/user-attachments/assets/e1d48ea6-8fe9-4b4e-8c1a-b64829107f4a)


### 2.3- Configuração Inicial do OpenVAS
Em seguida, configuramos o OpenVAS com o comando:<code>sudo gvm-setup</code> <br>

Este comando configura o ambiente e baixa os feeds de vulnerabilidades necessários.<br>

![img3](https://github.com/user-attachments/assets/62c2d53e-449a-4d5e-957b-34e05c13b977)


### 2.4- Verificação do Status do OpenVAS
Após a configuração, verificamos se todos os serviços do OpenVAS estão funcionando corretamente:<br>
<code>sudo gvm-check-setup</code> <br>

![img4](https://github.com/user-attachments/assets/91c58b25-855f-4cee-83c6-8854bdbe1618)


### 2.5- Iniciar o OpenVAS
Iniciamos o OpenVAS com o comando: <code>sudo gvm-start</code>
O OpenVAS estará acessível via interface web no navegador, em https://localhost:9392.<br>

![img5](https://github.com/user-attachments/assets/a180be81-b242-4baa-bc18-834b318ed2b7)



### 2.6- Acessar o OpenVAS via Navegador 
Acessando o OpenVAS através do navegador em https://localhost:9392 e fazendo login com as credenciais geradas (admin e a senha gerada durante a configuração) veremos a seguinte tela:<br>

![img6](https://github.com/user-attachments/assets/94e87bc4-9c45-4b7c-9328-a3161b15b23e)

Com a instalação e configuração do OpenVAS concluídas, o ambiente está preparado para realizar testes de vulnerabilidades. A partir daqui, o foco será a execução de scans nas máquinas virtuais configuradas, avançando para a próxima fase do projeto.



## 3- **Execução da Varredura de Vulnerabilidades:**

Nesta etapa, foi realizada a varredura de vulnerabilidades nas VMs configuradas no ambiente de teste utilizando o OpenVAS.

### 3.1- Identificação dos IPs Ativos
Antes de configurar o scan no OpenVAS, foi necessário identificar os IPs ativos na rede interna. Para isso, utilizamos o Nmap com o seguinte comando:<br>

<code>nmap -sn 10.0.2.0/24 | grep "Nmap scan report for" | awk '{print $5}' > ./Desktop/ips_ativos.txt</code><br>
Esse comando realiza uma varredura na rede 10.0.2.0/24, filtra os resultados para mostrar apenas os IPs ativos e os salva em um arquivo chamado ips_ativos.txt na área de trabalho.

![imgx](https://github.com/user-attachments/assets/75b6fd39-579a-42db-a24e-d3274e4bdee2)


### 3.2- Configuração do Scan
Com os IPs ativos identificados, foi criado um novo scan no OpenVAS para analisar as VMs presentes na rede interna. Abaixo estão os detalhes da configuração:

Nome do Scan: [SCAN-01] [LAB ENVIRONMENT] [FULL AND FAST]<br>
Alvos: IPs listados no arquivo ips_ativos.txt<br>
Configuração de Scan: Full and fast<br>
Lista de Portas: All IANA assigned TCP<br>
Teste de Conectividade: Consider Alive<br>

![Captura de tela 2024-08-17 165002](https://github.com/user-attachments/assets/cb36a044-31e1-4432-a4c9-65cf9254ce41)


### 3.3- Execução e Resultados do Scan
Após a configuração, o scan foi iniciado. O OpenVAS começou a análise das VMs na rede, procurando por possíveis vulnerabilidades em todos os serviços e portas configurados.<br>

Ao término do scan, o OpenVAS gerou um relatório detalhado listando todas as vulnerabilidades encontradas, classificadas por nível de severidade (alta, média, baixa). Esses resultados serão usados na próxima etapa para analisar e mitigar as vulnerabilidades identificadas.

![image](https://github.com/user-attachments/assets/bec49d83-7f04-4c8d-a640-1ae963de3f24)




## 4- **Anásile dos Resultados**
Nessa etapa, nós iremos analisar os resultados obtidos durante a varredura, além de corrigir as principais vulnerabilidades encontradas.

### 4.1- Análise Detalhada de uma Vulnerabilidade Crítica
Nós escolhemos a seguinte vulnerabilidade crítica para analisar mais detalhadamente

Título: Microsoft Windows SMB Server Multiple Vulnerabilities - Remote (4013389)

ID: 8e56e7df-da92-4807-bb6c-b5c58e01d335

Descrição: Essa vulnerabilidade afeta o servidor SMB do Windows e pode permitir a execução remota de código ou negação de serviço. Um atacante remoto não autenticado pode explorar isso enviando pacotes SMB maliciosos ao sistema vulnerável.

CVE: CVE-2017-0143 ao 2017-0148

![image](https://github.com/user-attachments/assets/28bf636b-b97b-4b67-8b72-554285ab94d4)

### 4.2-  Impacto Potencial no Sistema
- Impacto: Caso explorada, essa vulnerabilidade permite que um atacante execute código arbitrário remotamente no sistema Windows, comprometendo sua integridade e segurança. Pode levar à execução de malware, ransomware, ou até mesmo controle completo do sistema alvo.
- Sistemas Afetados: Microsoft Windows 10 x32/x64, Microsoft Windows Server 2012, Microsoft Windows Server 2016, Microsoft Windows 8.1 x32/x64, Microsoft Windows Server 2012 R2, Microsoft Windows 7 x32/x64 Service Pack 1, Microsoft Windows Vista x32/x64 Service Pack 2, Microsoft Windows Server 2008 R2 x64 Service Pack 1, Microsoft Windows Server 2008 x32/x64 Service Pack 2

### 4.3-  Métodos de Exploração
A vulnerabilidade pode ser explorada remotamente, sem a necessidade de autenticação, enviando pacotes SMB maliciosos para o servidor Windows.


![image](https://github.com/user-attachments/assets/73fafaf1-a24a-4173-ab38-473d006ebea3)

<a href="https://www.exploit-db.com/exploits/41987">Clicando aqui você pode ver um exploit que se aproveita dessa vulnerabilidade</a>

### 4.4- Mitigação
Para corrigr essa vulnerabilidade é necessário aplicar o patch de segurança fornecido pela Microsoft identificado como MS17-010.

Caso possível, desative o SMBv1 no servidor, pois essa versão é a mais vulnerável e não deve ser mais utilizada em sistemas modernos.

Também é importante implementar regras de firewalll para restringir o acesso ao SMB, para evitar que máquinas não autorizadas tenham acesso a essa porta.

![image](https://github.com/user-attachments/assets/3c33e45f-ef2b-44fd-b8a9-0ad8584bd840)

## **Conclusão**
Este projeto permitiu uma visão prática sobre a identificação de vulnerabilidades em sistemas utilizando o OpenVAS. Ao longo das etapas, foi possível configurar um ambiente de teste, realizar a instalação e configuração do OpenVAS, e conduzir varreduras para detectar possíveis falhas de segurança em diferentes sistemas operacionais. Além disso, a análise aprofundada de uma vulnerabilidade específica demonstrou a importância de corrigir brechas de segurança para mitigar riscos.
<!--
## 5- **Correção da Vulnerabilidade**
Ness etapa, iremos descrever o processo de correção da vulnerabilidade "Microsoft Windows SMB Server Multiple Vulnerabilities-Remote (4013389)" e realizar uma nova varredura para confirmar que a vulnerabilidade foi corrigida.

### 5.1- Desativação do SMBv1
Desativei a versão SMBv1 no Windows para mitigar a vulnerabilidade. Executei o seguinte comando no PowerShell como administrador:
-->

## Habilidades Desenvolvidas
Durante o desenvolvimento deste projeto, foram aprimoradas e aplicadas as seguintes habilidades:

- Configuração de Ambientes de Teste: Configuração de VMs utilizando diferentes sistemas operacionais, como Ubuntu Server, Windows 7, e Lubuntu, além da implementação de uma rede NAT para simular um ambiente realista de análise de vulnerabilidades.

- Instalação e Configuração do OpenVAS: Aprendizado prático na instalação e configuração do OpenVAS no Kali Linux, incluindo o uso de comandos do Linux e manipulação de pacotes.

- Execução de Varreduras de Vulnerabilidades: Realização de varreduras detalhadas com o OpenVAS, identificando vulnerabilidades em diferentes sistemas e serviços, e exportando os resultados para análise.

- Análise de Vulnerabilidades: Estudo detalhado de vulnerabilidades específicas (ex: Microsoft Windows SMB Server Multiple Vulnerabilities), com foco em suas causas, impacto e possíveis métodos de mitigação.

- Utilização do Nmap: Aplicação do Nmap para identificar dispositivos ativos na rede e coletar dados que foram essenciais para a execução das varreduras de vulnerabilidades.



