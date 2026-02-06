# Lesson 08: Configuring the FortiGate Intrusion Prevention System (IPS)

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Descreva o que é um sistema de prevenção de intrusões (IPS)
- Explique como um IPS pode detectar e bloquear atividades maliciosas em uma rede
- Configure o IPS do FortiGate
- Descreva as melhores práticas comuns ao trabalhar com um IPS

**Sistema de Prevenção de Intrusão (IPS)**

Sistemas de prevenção de intrusões, ou IPS, desempenham um papel muito importante na prevenção de ataques cibernéticos e na proteção das redes contra diversas ameaças. Um IPS pode detectar e bloquear atividades maliciosas na rede analisando o tráfego e identificando e bloqueando ameaças potenciais.

**Visão Geral da Funcionalidade IPS**

Para identificar tráfego malicioso, o fortigate utiliza seu motor IPS de ponta e sensores IPS. Um sensor IPS é um conjunto de assinaturas e filtros IPS que definem o escopo do que o motor IPS escaneia quando o sensor IPS é aplicado a uma política de firewall. Os sensores IPS também oferecem a capacidade de bloquear o acesso a URLs maliciosas conhecidas e endereços IP vinculados a servidores de comando e controle (C&C) de botnet. Um IPS funciona analisando o tráfego de rede em tempo real e utilizando uma variedade de técnicas para buscar padrões que possam indicar um possível ataque. Às vezes, alguams dessas técnicas se sobrepõem e se complementam para proporcionar melhores resultados.

**Técnicas de Detecção do Motor IPS FortiGate**

O motor IPS FortiGate utiliza as seguintes técnicas de detecção, entre outras:

- Decodificadores de protocolo
- Assinaturas

Uma vez que um IPS detecta atividade maliciosa, ele pode tomar várias ações que vão desde simplesmente criar um log até bloquear completamente a ameaça.

Atacantes podem enviar pacotes malformados para fazer o sistema-alvo funcionar de forma anormal ou até mesmo parar de funcionar. Antes de verificar ataques, o FortiGate utiliza um decodificador de protocolo para detectar padrões de rtáfego anômalos que não estejam em conformidade com os requisitos e padrões estabelecidos do protocolo. Isso permite que o FortiGate, por exemplo, identifique quaisquer pacotes HTTP que se desviem do padrão do protocolo HTTP. Decodificadores de protocolo FortiGate conseguem identificar a maioria dos protocolos mesmo quando usam números de porta não padrão.

Após o FortiGate identificar o protocolo, ele usa assinaturas para verificar o tráfego malicioso. Assinaturas são entradas em um banco de dados que incluem detalhes muito específicos sobre ameaças conhecidas. O IPS examina o tráfego de rede e procura correspondências no banco de dados. Quando encontra uma correspondência, o IPS realiza a ação configurada para aquela assinatura específica. Cada assinatura inclui uma ação padrão, mas você pode mudá-la para outra conforme necessário. Os firewalls FortiGate incluem milhares de assinaturas e recebem atualizações diárias da FortiGuard. No entanto, o FortiGate usa apenas as assinaturas que você especifica para examinar o tráfego. O uso de assinaturas é eficaz para detectar ameaças conhecidas, mas não detecta ameaças novas ou desconhecidas.

**Configuração do IPS do FortiGate**

Configurar o IPS FortiGate consiste em três etapas, ex:

- **TASK 1 -** Você deve selecionar o sensor IPS que será usado para analisar o tráfego. O FortiGate inclui vários sensores pré-definidos que você pode usar conforme fornecido, ou editar. Além disso, você pode criar seu próprio sensor personalizado para atender às suas necessidades específicas.
- **TASK 1 -** Você deve revisar ou editar a assinatura e os filtros incluídos no sensor. você também pode ativar o sensor para bloquear URLs maliciosas e tráfego C&C de botnet. Cada uma dessas opções é independente das outras e você deve configurá-las de acordo com suas necessidades.
- **TASK 1 -** Depois que o sensor estiver pronto, você deve aplicá-lo a uma política de firewall.


**Opções de Ações IPS**

A tabeça deste slide inclui todas as ações possíveis que o IPS FortiGate pode realizar ao detectar uma intrusão de rede.

Na maioria das vezes, um IPS não é uma do tipo "Configure e esqueça". Determinar e atualizar as ações corretas de assinatura faz parte do ajuste contínuo que você deve fazer para melhorar a eficácia da sua implementação de IPS. Sensores diferentes podem usar as mesmas assinaturas, mas com ações diferentes, dependendo do tráfego específico do cenário que examinam. Por exemplo, você pode ser mais flexível com o tráfego que se origina em locais confiáveis e mais restritivo com outros locais.

**Monitorando o IPS**

Como em qualquer outra solução de segurança, é importante monitorar os logs IPS que seu firewall gera.

A interface gráfica do FortiGate disponibiliza todas as informações registradas no **widget de Prevenção de Intrusão** incluido na **de Eventos de Segurança** em **Registro e Relatório**.

**Revisando Detalhes nos Logs do IPS**

Para uma análsie mais completa e para revisar todas as informações do tráfego IPS detectado, você deve acessar a **Logs**. Nesta seção, você pode acessar todos os detalhes relacionados aos registros relevantes.

**Melhores Práticas para IPS**

Estas são alguams das melhores práticas a seguir ao trabalhar com um IPS, ex:

- Verifique se o banco de dados IPS está atualizado: Para garantir a proteção adequada, seu IPS deve ter as informações mais recentes sobre ataques conhecidos. Durante a operação normal, o FortiGate recebe atualizações diárias do FortiGuard, mas isso pode ser afetado por quedas de rede não planejadas. Você também pdoe atualizar o banco de dados manualmente.
- Considere usar os sensores IPS fornecidos como modelos iniciais para novos sensores personalizados: os sensores padrão são um bom ponto de partida, mas você não deve modificá-los. Em vez disso, você pode cloná-los e fazer as edições necessárias no clones.
- Considere usar o IPS tanto para tráfego de entrada quanto de saída: em ambientes modernos, as ameaças vêm tanto de fora quanto de dentro da organização. Por isso, você deve configurar o IPS par aexaminar o tráfego em ambas as direções.
- Garantir que a inspeção SSL esteja em andamento para que o IPS possa examinar todo o tráfego: Sem inspeção SSL, o IPS não detectará ameaças ocultas no tráfego criptografado.
- Avalie se você precisa ajustar seus sensores IPS: Em geral, você deve sempre começar pelas ações padrão para cada assinatura. No entando, com base nos resultados obtidos, você deve avaliar se pode personalizar os sensores IPS para melhor atender aos requisitos do seu ambiente. Dessa forma, você pode minimizar falsos positivos e melhorar o desempenho do seu FortiGate.

