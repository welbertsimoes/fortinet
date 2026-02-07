# Lesson 13: Configuring the Fortinet Security Fabric

## **Objetivos**

- Descreva a importância e os benefícios da implementação do Fortinet Security Fabric
- Descreva como o Fortinet Security Fabric funciona para proteger sua rede e simplificar a administração da rede
- Configure o Security Fabric

## **Fortinet Security Fabric**

Às redes atuais estão mais complexas do que nunca, com uma grande variedade de dispositivos, aplicações e serviços conectando e enviando tráfego por elas. Gerenciar a segurança desses cenários usando uma abordagem caso a caso pode ser um desafio, e não é mais uma forma viável de defender sua organização contra todas as ameaças.

## **Funções do Fortinet Security Fabric**

O Fortinet Security Fabric é uma arquitetura empresarial que ajuda a gerenciar essa complexidade ao fornecer uma visão única da postura de segurança da organização. Isso permite que as equipes de segurança identifiquem e respondam rapidamente a ameaças de segurança. O Security Fabric oferece segurança integrada, automatizada e coordenada em toda a infraestrutura de rede da organização.

## **Benefícios de utilizar o Fortinet Security Fabric**

Esses são alguns dos benefícios de usar o Fortinet Security Fabric:

- Uma visão unificada de toda a rede a partir de um único consolo: As topologias lógicas e físicas da rede são fornecidas. Essas topologias mostram todos os dispositivos do tecido, como estão interconectados, bem como seus detalhes de segurança e as interfaces usadas para se comunicar com outros membros do tecido.
- Sincronização de vários tipos de objetos ao longo do tecido: Isso garante consistência entre todos os membros do dispositivo do tecido.
- A classificaçãode Segurança utiliza monitoramento em tempo real para analisar sua implantação no security Fabric, identificar vulnerabilidades e destacar as melhores práticas para melhorar a segurança e o desempenho. Às verificações de classificação de segurança são acionadas automaticamente quando mudanças relevantes na configuraçãosão feitas, e os resultados fornecem uma visão detalhada da postura de segurança da sua rede ao avaliar configurações em relação as melhores práticas e padrões de conformidade como PCI, CIS e FSBP. Uma visualização resumida mostra quantos itens foram aprovados, reprovados ou estão isentos de avaliação.
- Integração com muitos tipos de dispostiivos: Isso inclui dispositivos Fortinet, assim como dispositivos e plataformas de outros fornecedores por meio de uma API.
- Detecção automática dos dispositivos finais: Novos dispositivos endpoints são automaticament edetectados, identificados e adicionados à topologia Dispositivos com FortiClient instalado proporcionam melhor integração com o tecido.
- Gerenciamento centralizado das atualizações de firmware de todos os dispositivos Fortigate, fortiap e fortiswitch a partir d fortigate raiz: As atualizações podem ser feitas imediatamente ou agendadas e, no caso do Fortigat, o caminho correto de atualização é seguido, se necessário.
- Capacidades de automação: A rede é constantemente monitorada, e ações automáticas podem ser tomadas quando ameaças são detectadas sem a intervenção dos administradores.
	- Quando um ocmputador rodando o FortiClient detecta um site malicioso, ele envia um log para o FortiAnalyzer
	- O FortiAnalyzer detecta um indicador de comprometimento (IOC) e notifica o FortiGate
	- O FortiGate instrui o servidor de gerenciamento de endpoints (EMS) a colocar esse computador em quarentena.
	- O servidor EMS envia a mensagem de quarentena para o computador
	- O computador se isola e notifica o fortigate e o servidor EMS sobre sua mudança de status
	- O Fortigate envia um notificação para um canal no Microsoft Teams.

## **Estrutura do Fortinet Security Fabric**

Para implemenar o Fortinet Security Fabric, você precisa de pelo menos dois firewalls FortiGate rodando no modo NAT. Um dos dispositivos FortiGate atua como firewall raiz do Fabric. Você também deve centralizar a digitalização. Isso requer um FortiAnalyzer ou uma solução de cloud loggin suportada. OFortiAnalyzer cloud ou o fortigate cloud podem atuar como solução de loggin na nuvem.

Dependendo do seu cenário, e para aumentar sua visibilidade e controle da rede, recomenda-se também adicionar FortiManager, fortiap, forticlient, forticlient ems, fortisandbox, forimail, fortiweb, forindr, fortideceptor e fortiswitch. Cada um desses dispositivos adiciona novas capacidades à equipe de segurança. Por exemplo, o FortiManager pode simplificcar a implantação de políticas de segurança em todos ou específicos firewalls FortiGate.

Além disso, você pode estender ainda mais seu fabric com outros dispositivos opcionais da fortinet, e até mesmo vários produtos terceiros.

## **Configurando o Fortinet Security Fabric**

Configurar o Fortinet Security Fabric consiste nos seguintes passos:

- **Passo 1 -** Configurar o FortiAnalyzer, ou uma das plataformas suportadas de cloud logs, para aceitar logs de dispositivos no tecido. 
- **Passo 2 -** Configurar o dispositivo Fortigate que atuará como raiz do fabric, essa etapa inclui configurar as configurações de log, às interfaces necessárias e o conector Security Fabri.
- **Passo 3 -** Configurar os dispositivos downstream, no caso dos dispositivos fortigate downstream, essa etapa inclui configurar as interfaces necessárias e o conector security fabric para apontar para o dispositivo raiz. Você não precisa configurar as configurações de log, pois elas são herdads da raiz. Os requisitos para outros dispositivos variam dependendo do tipo.
- **Passo 4 -** É autorizar dispositivos a partir do firewall root. Você deve autorizar qualquer dispositivo, seja adicionado manualmente ao Security Fabri ou detectado automaticamente, no fortigate root. Opcionalmente, você pode pré-autorizar dispositivos se souber seus detalhes.

