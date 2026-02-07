# Lesson 12: FortiGate System Maintenance and Monitoring

Objetivos:

- Realize tarefas comuns de manutenção do FortiGate
- Faça backup e restaure uma configuração do fortiGate
- Atualize o firmware do FortiGate
- Monitore o uso dos recursos do FortiGate
- Verifique as licenças da FortiGate
- Monitore os registros do FortiGate

## **Visão geral da manutenção e monitoramento do sistema FortiGate**

Realizar manutenção regular nos firewalls FortiGate é essencial para garantir a segurança e o desempenho idela da sua rede. As organizações devem priorizar essas tarefas para prevenir violações de segurança, otimizar o desempenho, cumprir os requisitos de conformidade e garantr a continuidade do negócio.

## **Funções da Manutenção do Sistema FortiGate**

As tarefas de manutenção mais comuns incluem fazer backup de configurações, realizar atualizações de firmware, monitorar o desempenho do sistema, examinar livenças e monitorar logs de eventos.

## **Backup de configurações do FortiGate**

Todo administrador do FortiGate deve fazer bakcup de suas configurações de sistema regularmente.

Em caso e falha no sistema ou hardware, restaurar a configuração de backup economiza tempo e esforço ao evitar a necessidade de reconfigurar o firewall do zero. Backup de configuração também são úteis ao migrar para uma nova plataforma de hardware ou ao solucionar problemas após mudanças inesperadas de configuração.

Você pode salvar backups de configuração como arquivos no PC local ou, se disponível, em um pendrive USB. Para restaurar uma configuração, você precisa saber onde o arquivo de backup está armazenado e envia-lo usando a interface gráfica.

Além disso, se seu dispositivo FortiGate tiver pelo menos 512 MB de memória flash, você pode armazenar revisões de configuração localmente no firewall e usá-las para reverter rapidamente ao estado anterior do sistema.

## **Realizando Atualizações de Firmware**

A Fortinet lança regularmente novas versões de firmware para adicionar novos recursos, resolver problemas importantes e melhorar o desempenho. Atualizar o firmware ajuda os firewalls FortiGate a se manterem atualizados sobre as últimas ameaças de segurança e garante desempenho ideal.

Na versão 7.2 e posteriores, o novo firmware FortiOS usa uma tag para indicar seu nível de maturidade. A letra F, de Features, indica que o firmware inclui novos recursos, e a Letra M, de Mature, indica que o lançamentos não inclui nenhum novo recurso principal.

Firewalls FortiGate com licença de atualização de firmware exibem uma notificação quando um novo firmware é lançado e oferecem a opção de instalá-lo. Usando esse método, o FortiGate Baixa e instala a atualização automaticamente.

Alternativamente, você pode baixar manualmente o arquivo de firmware pelo portal de suporte da Fortinet e realizar a atualização usando o arquivo baixado. Nesse caso, é iportante garantir que o firmware que você baixou seja compatível com o modelo FortiGate e que você siga o caminho de atualização suportado.

Durante a atualização, você é solicitado a fazer backup da sua configuração. É altamente recomendado que você faça um backup de configuração antes de atualizar o firmware atual, caso improvável de algo dar errado durante o processo.

## **Seguindo o Caminho de Atualização Recomendado**

Se você precisar atualizar para uma versão específica de firmware, mas houver várias versões intermediárias entre a versão atual e a versão para a qual está sendo atualizado, é importante seguir um caminho de atualização suportado para garantir um processo de atualização bem-sucedido.

O caminho de atualização é a sequência recomendada de atualizações de firmware que você deve seguir ao atualizar um dispositivo FortiGate. Essa sequência é fornecida pela Fortinet. Ele garante que a nova versão seja compatível e garanta a estabilidade do seu dispositivo.

Para permitir que o FortiGate siga automaticamente o caminho recomendado de atualização, você pode selecionar a versão de firmware desejada em Todas as Atualizações.

## **Ferramenta de Caminho de Atualização Fortinet**

Se você está realizando a atualização manualmente, deve verificar a Ferramenta de Caminho de Atualização fornecida pela Fortinet. Esta é uma ferramenta online que permite encontrar facilmente a sequência recomendada de versões de firmware para a sua plataforma específica.

## **Desempenho do Sistema de Monitoramento**

Monitorar o desempenho do FortiGate ajuda a garantir que ele está funcionando corretamente e que seu hardware está adequadamente dimensionado para lidar com o tráfego da rede. Você não quer um firewall sobrecarregado ou subutilizado.

De modo geral, você deve sempre monitorar o uso de CPU e memória. No entando, você também deve ficar de olho no espaço disponível em disco, especialmente se seus registros de tráfego estiverem armazenados localmente. Ao monitorar esses recuros-chave, você pode identificar possíveis gargalos ou problemas de desempenho.

Na maioria dos casos, você também deve monitorar outros parâmetros não relacionados ao hardware para uma visão completa do desempenho do seu firewall. Por exemplo, você pode monitorar o número de sessões, quantos logs estão sendo gerados por segundo e o número de usuários de VPN conectados.

De fábrica, a interface gráfica inclui vários widgets que você pode usar para monitorar esses recursos em tempo real. Você pode adicionar ou remover widgets conforme necessário, e alterar suas configurações e layout.


## **Examinando as Licenças FortiGate**

Firewalls fortigate exigem licenças para funcionar. Diferentes licenças oferecem acesso a uma variedade de recursos e serviços, como suporte técnico, antivírus, filtragem web e IPS.

Você pode ver o status da sua licença FortiGate em dois locais: Na interface gráfica, clicando em **sistema**, depois em **FortiGuard**, e no **Licenças** no painel. Cada recurso indica se a licença correspondente é válida e exibe sua data de expiração.

Para evitar interrupções nos serviços, evitar problemas legais e manter a conformidade, é importante renovar todas as licenças antes que expirem.

Uma licença expirada impede que o Fortigate receba atualizações de software e suporte técnico. Alguns recursos podem continuar funcionando durante um período de carência, enquanto outros param completamente.


## **Monitoramento dos Registros de Eventos**

Os logs do FortiGate fornecem informações essenciais sobre a atividade do firewall, incluindo tráfego de rede, monitorar eventos de segurança e eventos do sistema. Monitorar seus registros regularmente pode ajudar a identificar potenciais ameaças de segurança, solucionar problemas e fornecer insights sobre o desempenho da rede e do sistema.

O fortigate oferece uma interface web amigável para visualizar logs.

Todas as informações de registro estão localizadas em **Registro e Relatório.** À interface gráfica inclui várias categorias de logs para facilitar a localização dos logs de interesse. Para exibir apenas logs específicos, você pode usar filtros baseados em qualquer um dos campos incluídos em cada log.

As **de Eventos do Sistema e Eventos de Segurança** fornecem uma página resumo além das entradas de registro habituais.
