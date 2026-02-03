# Lesson 03: Firewall Policies

Anotações aqui...

Ao final desta aula, você será capaz de alcançar estes objetivos:

- Descreva quais são as políticas de firewall
- Entenda como funcionam as políticas de firewall
- Descreva como funcionam os modos de inspeção
- Configure as políticas de firewall

Políticas de firewall são conjuntos de regras que você usa para controlar se o tráfego na sua rede é aceito pelo FortiGate e, se for aceito, como o FortiGate o processa.

As políticas de firewall definem qual tráfego corresponde a elas e o que o FortiGate faz quando o tráfego corresponde. Cada apólice possui critérios de correspondência, que você pode definir usando os seguintes objetivos:

- Interfaces de entrada e saída
- Fonte
- Destino
- Serviço
- Cronograma

Quando o tráfego corresponde a uma política de firewall, o FortiGate aplica a ação configurada nessa política de firewall

- Se a **ação** estiver definida como **DENY**, o fortigate encerra a sessão
- Se a **ação** estiver configurada para **ACEITAR**, o fortigate aceita a sesão

Tanto o campo Source quanto o campo de destino de uma política de firewall podem atender a dois critérios diferentes: sub-rede IP ou serviços de internet.

Para usar uma sub-rede IP como origem ou destino, você deve primeiro criar um endereço de firewall que corresponda a essa sub-rede. Para criar uma política que permita que usuários internos acessem a internet, você deve configurar um endereço de firewall que corresponda à sub-rede IP da rede interna e usá-lo como fonte na política de firewall.

Você também pode criar um endereço de firewall para o endereço IP de um dispositivo específico, como um servidor web. Você usaria esse endereço como destino em qualquer política de firewall que queira permitir o acesso ao servidor.

Uma opção padrão de ALL está disponível tanto para endereços IP de origem quanto de destino. A opção corresponde a todos os endreços IP possível. Para definir um usuário de origem, você configura a autenticação do firewall e então seleciona usuários específicos ou grupos de usuários.

Para usar um serviço de internet como fonte ou destino, selecione o serviço apropriado do banco de dados de serviços de internet (ISDB). O ISDB é uma lista que inclui as sub-redes IP de provedores de serviços web comumente usados, como Meta, Youtube e outros. O administrador do fortigate também pode adicionar serviço personalizados à lista.

A tabela de políticas do Fortigate contém todas as políticas de firewall. Ao corresponder o tráfego, o fortigate verifica a tabela de políticas de cima a baixo e processa o tráfego usando a primeira política que corresponde. Se não houver correspondência, o Fortigate elimina o Tráfego aplicando a política padrão de Negação Implícita do firewall, localizada na parte inferior da tabela.

Como A primeira correspondência é usada, é boa prática ter as políticas mais específicas localizadas no topo da tabela e as políticas mais gerais mais abaixo na tabela. Isso garante que a fortigate aplique a política correta ao tráfego.

Após aceitar o tráfego, o Fortigate pode aplicar outros recursos e configurações a esse tráfego com base na configuração da política do Firewall. Isso pode incluir varredura de segurança, como antivírus, controle de aplicações e filtragem web. A varredura pode bloquear o tráfego se, por exemplo, o fortigate descobrir que contém um vírus. O fortigate também aplica tradução de endereços de rede e registra o tráfego com base nas configurações da política do firewall.

Ao configurar uma política de firewall, você deve selecionar entre dois modos de inspeção: modo de inspeção baseado em fluxo e modo de inspeção baseado em proxy.

O modo de inspeção baseado em fluxo examina otráfego enquanto ele passa pelo fortigate, sem qualquer buffering. à medida que cada pacote chega, ele é processado e encaminhado sem esperar pelo arquivo completo ou página web. O fortigate não altera o original, o que significa que quaisquer recursos que modificam o conteúdo, como a aplicação segura de buscas, não são suportados neste modo.

No modo de inspeção baseado em proxy, o fortigate armazena o tráfego em buffer e o examina como um todo antes de determinar uma ação. Como o Fortigate examina os dados como um todo, ele pode examinar mais pontos de dados do que ao usar inspeção baseada em fluxo, mas usar esse modo adiciona latência à velocidade geral de transmissão. A inspeção baseada em proxy é mais minuciosa do que a inspeção baseada em fluxo, gerando menos falsos positivos e resultados negativos.


