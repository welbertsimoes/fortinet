# Lesson 15: Configuring FortiLink

## **Objetivos**

- Descreva o que é FortiLink e seus benefícios
- Descreva como o FortiLink Funciona 
- Configure FortiLink
- Aplique as melhores práticas gerais ao usar o FortiLink

## **O que é FortLink?**

FortiLink é um protocolo proprietário da Fortinet que permite aos administradores gerenciar FortiSwitches diretamete pela interface FortiGate, sem exigir uma licença adicional. O FortiLink simplifica o gerenciamento de rede ao centralizar o controle no FortiGate tanto para segurança quanto para comutação. Isso permite que dispositivos LAN se tornem parte da infraestrutura de segurança, aprimorando efetivamente o Fortinet Security Fabric.

Depois de implementado, você pode configurar todas as configurações desejadas de switches no FortiGate e envia-las automaticamente para os FortiSwitches que ele gerencia.

O número de unidades FortiSwitch suportadas depende do modelo FortiGate, variando de 8 no segmento inferior até 300 no topo de linha.

## **Por que usar o FortiLink?**

O Fortilink oferece vários benefícios importantes, incluindo:

- Gestão centralziada
- Implantação simplificada 
- Segurança aprimorada
- Escalabilidade

## **Como funciona o FortiLink?**

O Fortigate utiliza vários protocolos para controlar o FortiSwitch.

O Fortigate usa o protocolo Fortilink por padrão para descobrir fortiSwitches. Switches gerenciados conectados diretamente ao FortiGate também usam o FortiLink para enviar batimentos cardíacos. Os quadros de descoberta do Fortilink incluem informações sobre os números de série e portas dos switches.

O protocolo de Descoberta da Camada de Enlace (LLDP) é um método alternativo para descoberta de switches, também é usado durante a configuração de uma pilha de switches porque permite que os links que conectam os switches sejam configurados automaticamente como troncos.

Controle e provisionamento de pontos de acesso sem fio (CAPWAP) é um protocolo padrão originalmente projetado para centralizar o gerenciamento dos pontos de acesso wi-fi. Além de sua função original, a implementação do CAPWAP pela Fortinet realiza autenticação, autorização e verificações de saúde dos switches, estabelecneod um túnel seguro entre o FortiGate e os switches gerenciados. Também é usado como um método alternativo e legado para enviar um arquivo de imagem de firmware para um switch ao usar a ferramentas de atualização de firmware da interface gráfica FortiGate. O FortiSwitch também usa o CAPWAP para enviar logs de switch para o FortiGate

Além disso, o FortiGate utiliza outros protocolos conhecidos, como DHCP, DNS, NTP e SSH, que auxiliam nas tarefas de gerenciamento.

## **Configure o FortiLink no FortiGate**

Para configurar o fortiLink, comece ativando o recurso de controle de switch no dispositivo Fortigate. Depois crie uma interface FortiLink no **Switch Controler > Fortlink Interface.** Essa interface deve ser atribuída a uma ou mais portas FortiGate usadas para gerenciamento de Switch. Recomenda-se atribuir mais de uma porta para redundância.

Após selecionar as portas apropriadas, você deve configurar um endereço IP para a interface do FortiLink.

Dependendo do design da rede, você também pode ativar opções como servidor DHCP, autorização automática de switch ou uma interface FortiLink split. A interface dividia é usada quando você precisa conectar uma interface agregada FortiLink a mais de um FortiSwitch.

Após configurar o FortiLink, conecte ao FortiSwitch a prota FortiGate configurada para o Fortlink. Após alguns segundos, verifique se os FortSwitches foram descobertos pelo FortiGAte, em Wifi & Switch Controller > FortiSwitches Gerenciados.

Se a autorização automática não estiver ativdada, autorize manualmente os FortiSwitches. Uma vez autorizados, os switches torna-se visíveis e gerenciáveis diretamente pela interface FortiGate.

É importante notar que modelos mais recentes do FortiSwitch Transmitem por padrão os quadros de descoberta do Fortlink em todas as portas, simplificando o processo de conexão. No entando, modelos mais antigos podem exigir conexão por portas dedicadas específicas para iniciar a comunicação FortiLink.

## **Topologias FortiLink**

O FortiLink oferece opções flexíveis de implantação, permitindo que o FortiGate gerencie FortiSwitches em uma variedade de topologias adequadas a diferentes ambientes de rede. A seguir, quatro exemplos de topologias suportadas que demonstram a adaptabilidade do FortiLink em suportar arquiteturas de rede simples e avançadas com complexidade de configuração mínima. Clique em cada exemplo para saber mais.

**FortiGate ùnico:** Em um único FortiGate gerenciando uma pilha de FortiSwitches, os switches são conectados em uma topologia em cadeia ou anel, com o swtich principal conectado diretamente ao FortiGate via Fortilink. O diagrama também mostra a opção de conectar uma conexão Fortilink de reserva à última unidade FortiSwitch. Para essa configuração, você habilita o Fortlink Split-Interface com uma interface agregada que contém um link ativo e um link de espera.

**Par HA:** No caso de um cluster FortiGate A-P HA, ambas as unidades FortiGate conectam-se a primeira unidade FortiSwitch da Pilha. Opcionalmente, eles também podem se conectar a última unidade FortiSwitch, caso em que você deve ativar a Fortlink Split Interface para evitar loops na rede.

**Redes de Camada 3:** Esse recurso permite que ilhas FortiSwitch, cada uma com uma ou mais unidades fortiSwitch, operem no modo Fortilink através de redes roteadas, mesmo que não estejam diretamente conectadas ao FortiGate atuando como controlador de swtich. Isso é ideal para gerenciar locais remotos ou redes segmentadas.

**Acesso FortiSwitch com dual-homed:** A unidade FortiGate independente com topologia de acesso FortiSwitch dual-homed oferece alta densidade de portas com dois níveis de unidades FortiSwitch. Este exemplo inclui o uso de um grupo de pares multichassis link aggregation (MCLAG) entre o FortiSwitch 1 e o FortiSwitch 2. O FortiGate têm apenas um FortiSwitch.

## **Melhores Práticas**

Para garantir uma implantação bem-sucedida do FortiLink, siga estas diretrizes:

- Permitir a agregação de Links para garantir redundância e aumentar a taxa de transferência entre FortiGate e FortiSwitches
- Mantenha as versões de firmware consistentes entre FortiGate e FortiSwitch para garantir a compatibilidade.
- Planeje o uso de VLANs e portas antes da implantação para minimizar reconfigurações posteriores. Isso inclui considerar o crescimento futuro da rede.
- Monitore regularmente o status e o status e os registros dos interruptores para identificar precocemente. Você pode fazer isso via FortiGate ou usando outra solução como o FortiAnalyzer.
