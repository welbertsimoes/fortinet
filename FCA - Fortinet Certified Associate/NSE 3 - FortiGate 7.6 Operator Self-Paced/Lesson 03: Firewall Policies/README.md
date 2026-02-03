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

- Se a *ação* estiver definida como *DENY*, o fortigate encerra a sessão
- Se a *ação* estiver configurada para *ACEITAR*, o fortigate aceita a sesão
