# Lesson 14: FortiGate High Availability (HA)

## **Objetivos:**

- Descreva o que é alta disponibilidade (HA) e seus benefícios.
- Escreva como o FortiGate HA funciona
- Configure FortiGate HA
- Aplique as melhores práticas gerais ao usar o HA

## **O que é Alta Disponibilidade HA?**

Alta disponibilidade (HA) do FortiGate é um recurso que permite qe múltiplos firewalls Fortigate trabalhem juntos como um cluster, proporcionando redundância, melhorando a confiabilidade da rede e minimizando o tempo de inatividade. Se um dispositivo FortiGate no cluster sair offline devido a problemas de hardware, conectividade ou manutenção programada, outra unidade assume automaticamente para garantir o fluxo contínuo de tráfego.

O Fortigate HA mantém a aplicação contínua de segurança e conectividade sincronizando dados de configuração e de sessão entre dispositivos no cluster. Isso o torna especialmente valioso para organizações que exigem alta disponibilidade e tolerância a falhas em sua infraestrutura de rede.

## **Por que usar HA?**

O FortiGate HA oferecebe vários benefícios importantes:

- **Redundância:** O processo automático de failover elimina o risco de um único ponto de falha e mantém à continuidade do negócio durante interrupções inesperadas e atualizações do sistema.
- **Configuração e sincronização de sessões:** Os dados relevantes de configuração são sincronizados entre todos os membros do cluster para garantir um failover contínuo. As informações da sessão também podem ser compartilhadas para permitir que o tráfego contíuno continue sem interrupção após um failover
- **Gerenciamento simplificado:** Todas as alterações de configuração relacionadas ao cluster feitas na unidade primária são sincronizadas com todos os outros membros.

## **Como funciona o HA?**

* **Camada 1 -** Durante a criação e o failover, o cluster HA elege um dispositivo para servir como primário. O processo de eleição primária também ocorre durante um failover. Por padrão, o primeiro dispositivo adicionado ao cluster assume o papel principal. O dispositivo principal gerencia as operações do cluster e processa o tráfego. Todas as mudanças de configuração feitas no primário são automaticamente eniadas para o secundário.

Todos os outros dispositivos são designados como secundários, com funções que variam dependendo do modo HA em uso.

Uma vez configurado, os membros do dispositivo se comunicam usando interfaces de batida cardíaca para monitorar a saúde do cluster. Essas interfaces detectam falhas rapidamente e iniciam o failover quando ocorrem.

* **Camada 2 -** Por padrão, o dispositivo primário é selecionado comparando vários parâmetros entre os membros do cluster, na seguinte ordem:

- **1 -** O dispositivo com o maior número de interfaces monitoradas em status UP
- **2 -** O dispositivo com maior tempo de atividade de HA, por pelo menos 5 minutos
- **3 -** O dispositivo com maior prioridade
- **4 -** O dispositivo com o maior número de série

* **Camada 3 -** Opcionalmente, você pode ativiar a opção de substituição para que o cluster verifique o valor de prioridade antes do uptime do HA. Isso facilita especificar qual dispositivo deve ser o primário, atribuindo a ele o valor de maior prioridade. Uma desvantagem dessa opção é que, se o primário ficar temporariamente indisponível, ele acionará um processo de failover duas vezes, uma quanto cai e outra quando voltar a funcionar.

## **Protocolos usados em um cluster HA**

No core fo FortiGate HA está o protocolo de clusterização FortiGate (FGCP). A FGCP gerencia a descoberta dos membros, elege o FortiGate primário, sincroniza os dados entre os membros e monitora sua saúde. Ele realiza todas essas tarefas através das interfaces de batida cardíaca configuradas.

O FGCP também atribui endereços MAC virtuais a cada interface da unidade principal. Quando ocorre um failover, os endereços MAC necessários são encaminhados para a nova unidade primária. Isso garante que os clientes não precisem atualizar suas tabelas ARP, reduzindo o tempo de inatividade e a perda de pacotes.

Você pode ativar a captação de sessão para sincronizar a tabela de sessão TCP da unidade principal para todos os membros do cluster. Se a primária falhar, a primária recém-eleita retoma essas sessões a partir de sua tabela sincronizada, garantindo a mínima interrupção nas conexões tcp ativas. Configuração adicional é necessária para sincronizar o tráfego que não seja TCP.

## **Quais informações são sincronizadas?**

Os membros do dispositivo sincronizam todas as informações necessárias para o funcionamento adequado do cluster. A tabela neste slide mostre quais informações estão sincronizadas e quais não são.

## **Modos HA**

Existem dois modos de operação de HA disponíveis: ativo-passivo (A-P) e ativo-ativo (A-A).

No modo ativo-passivo, o dispositivo principal lida com todo o tráfego, enquanto os dispositivos secundários permanecem em modo de espera. Se a primária falhar, uma nova primária é eleita entre os dispositivos secundários disponíveis.

No modo ativo-ativo, todos os dispositivos processam o tráfego simultaneamente. O dispositivo principal atribui e distribui sessões suportadas aos dispositivos secundários. Essa é a opção recomendada par aambientes de alta taxa por que, além da redundância alcançada, o tráfego é distribuído uniformemente entre todos os membros do cluster.

## **Requisitos HA**

Antes de configurar o FortiGate JA, certifique-se de que os dispositivos que deseja adicionar tenham o mesmo modelo de hardware ou VM, firmware, licenciamento, configuração do disco rígido e modo de operação.

Além disso, durante a criação do cluster, os seguintes parâmetros devem corresponder.

- ID de grupo HA
- Nome do Grupo
- Senha
- Configurações da interface do batimento cardíaco

## **Melhores Práticas**

A seguir, algumas boas práticas gerais para se considerar ao trabalhar com a FortiGate HA:

- Use pelo menos duas interfaces dedicadas ao batimento cardíaco para redundância e detecção de falhas mais rápida. Isso também ajuda a evitar um cenário de cérebro dividido, onde mais de uma unidade tenta ser a primária. Conexões duplas conse cutivas entre unidades HA são altamente recomendadas.
- Use conexões idênticas para interfaces internas e externas: conecte cada unidade HA aos mesmos switches usando portas e cabos idênticos.
- Certifique-se de que todas as unidades usem a mesma versão de firmware e modelo de hardware para evitar problemas de compatibilidade.
- Evite trocas manuais nas unidades secundárias. Sempre faça alterações de configuração apenas a partir do primário.
- Ative o monitormaneot de links em interfaces críticas como wan e lan para detectar falhas de porta.
- Teste regularmente, verificando periódicamente a funcionalidade de failover para garantir que o cluster funcione corretamente em situações do mundo real.


