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
