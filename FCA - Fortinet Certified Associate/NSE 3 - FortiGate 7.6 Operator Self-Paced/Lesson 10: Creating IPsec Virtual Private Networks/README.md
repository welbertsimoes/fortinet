# Lesson 10: Creating IPsec Virtual Private Networks

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Entenda o que são as Redes Privadas Virtuais (VPNs) IPsec e por que elas são usadas
- Entenda como funcionam as VPNs IPsec do FortiGate
- Configure VPNs IPsec usando dispositivos FortiGate

## **IPsec VPNs**

IPsec é um conjunto de protocolos padrão da indústria usado para criar conexões seguras entre dispositivos localizados em redes diferentes, frequentemente geograficamente distantes. Essas conexões seguras são conhecidas como redes privadas virtuais, ou VPNs.

## **Características das VPNS IPsec**

Dependendo da configuração utilizada, o IPsec pode oferecer alguns ou todos os seguintes recursos:

- Autenticação de dados, para verificar a origem dos dados
- Integridade dos dados, para evitar adulteração de dados
- Confidencialidade dos dados, para criptografar o tráfego
- Proteção anti-replay, para prevenir ataques de replay

## **Vantagens do uso de VPNs IPsec**

Esses recursos são extremamente importantes porque, na maioria das implementações, o tráfego VPN passa por redes não seguras como a internet. Uma vantagem importante que as VPNs IPsec têm em relação a outras soluções é que não exigem a intervenção dos provedores de serviço. Tudo o que você precisa para estabelecer um túnel VPN seguro é a alcançabilidade do IP entre as duas extremidades da conexão.

## **Tipos de VPNs**

O IPsec pode ser usado para criar dois tipos de VPNs: VPNs de acesso remoto e VPNs site-to-site, ex:

- Uma VPN de acesso remoto permite que um dispositivo cliente se conecte a uma rede remota. VPNs são comumente usadas por teletrabalhadores que precisam de uma forma segura de acessar arquivos e serviços hospedados na rede da empresa enquanto estão em casa ou viajando. Em VPNs remotas, o cliente sempre inicia a conexão. Usuários remotos normalmente usam uma senha para acessar a rede do local de trabalho, mas outras soluções são suportadas, incluindo autenticação multifator (MFA). A FortiGate aceita FortiClient e vários produtos de outros fornecedores como clientes VPN remotos.
- Uma VPN site-to-site permite que redes em dois locais físicos diferentes se conectem de forma segura. Por exemplo, uam VPN site-to-site pode permitir que os computadores de uma filial acessem recursos hospedados no prédio da sede ou até mesmo em outras filiais. Na VPN site-to-site, qualquer um dos lados pode iniciar a conexão. Quando você usa múltiplos túneis VPN site-to-site, pode criar topologias hub-and-spoke, mesh parcial e full mesh. A FortiGate pode estabelecer VPNs site-to-site com outros dispositivos FortiGate, assim como com dispositivos de outros fabricantes, incluindo provedores de serviços em nuvem como AWS e Azure.

## **Conectando por VPNs**

Em ambos os tipos de VPNs, após a conexão ser estabelecida, os dispositivos de uma rede podem alcançar os dispositivos da outra rede. Quando conectados por uma VPN, dispositivos em redes diferentes passam a fazer parte da mesma rede lógica.

## **Protocolo de Troca de Chaves na Internet**

Independentemente do tipo de VPN IPsec utilizado, o protocolo IKE é usado para criar os túneis dinamicamente. O fortiGate suporta as duas versões disponíveis do IKE: IKEv1 e IKEv2. Embora o IKEv2 inclua várias melhorias de segurança em relação ao IKEv1, este último ainda é amplamente utilizado em muitas implantações de VPN. Ao usar o IKEv1, o processo de VPNIPsec passa por duas etapas: Fase 1 e Fase 2.

### **IKEv1 Protocol | Phase 1**

Na Fase 1, os dois dispositivos peer autenticam entre si e estabelecem um canal seguro que serão usados para negociar os parâmetros de segurança da Fase 2. Esse primeiro canal atua como o plano de controle da conexão VPN. Os parese podem ser configurados com várias combinações ou propostas. Cada proposta consiste em vários parâmetros de segurança.

### **IKEv1 Protocol Phase 1 Parameters**

Para uma Fase 1 bem sucedida, os seguintes parâmetros devem coincidir em pelo menos uma das propostas de cada dispositivo par:

- Modo IKE: Main ou agressivo
- Autenticação
- Algoritmo de criptografia
- Algoritmo de hash
- Grupo Diffle Helman

Outros parâmetros não precisam coincidir por que podem ser negociados. A fase 2 só pode começar após a conclusão bem-sucedida da Fase 1.

### **IKEv1 Protocol | Phase 2**

Na Fase 2, ambos os dispositivos peer determinam qual tráfego deve ser enviado pela VPN  e como ele será autenticado e criptografado. Nesta fase, é criado um subtúnel do túnel da Fase 1 principal. Esse subtúnel atua como o plano de dados.

### **IKEv1 Protocol Phase 2 Parameters**

Assim como na Fase 1, os pares podem ser configurados com várias propostas da Fase 2. Para uma Fase 2 bem-sucedida, os seguintes parâmetros devem coincidir em pelo menos uma proposta em ambos os pares:

- Algoritmo de criptografia
- Algoritmo de hash
- Grupo Helman Diffle (Somente se for usado PFS, o que é altamente recomendado)

Outros parâmetros não precisam coincidir, já que podem ser negociados.

### **Configuring IKEv1 Protocol Phase 2**

O tráfego a ser protegido deve ser indicado listando as sub-redes locais e remotas que irão se comunicar pelo túnel:

- Em uma VPN de acesso remoto, ambas as sub-redes são configuradas no lado do servidor.
- Em uma VPN site-to-site, as sub-redes de cada par devem espelhar umas às outras.

### **IKEv2 Protocol**

O IKEv2 foi projetado com várias melhorias em relação ao IKEv1, tanto em segurança quanto em desempenho. É o protocolo recomendado para novas implementações de VPN IPsec, a menos que o hardware disponível não o suporte. Embora compartilhe muitas semelhanças com seu antecessor, o IKEv2 não inclui duas fases e não é compatível com o IKEv1.

## **Benefícios de usar IKEv2 em relação ao IKEv1**

Alguns dos benefícios de usar o IKEv2 em relação ao IKEv1 incluem:

- O uso de menos mensagens reduz a latência e a largura de banda usada durante a negociação dos túneis
- O uso de números de sequência e confirmações em suas mensagens
- O suporte ao EAP adiciona mais flexibilidade, escalabilidade e interoperabilidade durante o processo de autenticação
- Suporte a PPK (chaves pré-compartilhadas Postquantum)
- O suporteà autenticação assimétrica permite que os pares utilizem diferentes métodos de autenticação
- Suporte a algoritmos de segurança mais fortes. Por exemplo, o FortiGate suporta PRF-SHA para hashing e AES-GCM para criptografia, ambos com vários comprimentos de bits disponíveis.
- Melhor resiliência contra ataques de DoS


## **Encapsulando a Carga Útil de Segurança (ESP)**

Firewalls FortiGate suportam protocolo ESP para autenticação e criptografia do tráfego VPN. O ESP fornece criptografia de dados, integridade dos dados e autenticação de origem dos dados, mas não fornece autenticação de identidade. No entando, a autenticação de identidade é fornecida pelo IKE durante a negociação da Fase 1.

A tabela a seguir mostra alguns dos algoritmos de criptografia e hash mais conhecidos suportados pelo ESP no FortiGate, ex:

- O padrão de criptografia de dados ou DES é considerado fraco em comparação com outros algoritmos de criptografia e não é recomendado para uso em sistemas modernos.
- O padrão de criptografia tripla de dados, ou 3DES, utiliza três operações DES seguidas para fornecer um nível mais forte de criptografia. No entanto, devido ao seu desempenho lento e à curta duração da tecla, não é considerada a melhor opção
- O padrão avançado de criptografia, ou AES, está disponível com vários comprimentos de chave. Quanto maior o número de bits na chave, mais forte será a criptografia alcançada. Atualmente, ele é considerado muito seguro e é o algoritmo de criptografia mais amplamente utilizado.
- Message digest 5 ou MD5 ainda pode ser encontrado em alguns sistemas e aplicações legadas, mas não é mais recomenaddo para uso em sistemas que exigem forte segurança
- O algoritmo de hash seguro 1 ou SHA-1 não é mais recomendado para uso em sistemas que exigem forte segurança, devido a vulnerabilidades conhecidas
- O Algoritmo de Hash Seguro 2 é mais seguro que o SHA-1. Está disponível com vários comprimentos de bit. Quanto maior o número de bits usados, mais seguro será o hash resultante. É considerada uma opção segura.

## **Melhores Pŕaticas de Configuração de VPN**

A seguir, algumas boas práticas gerais que podem ajudar você a evitar problemas inesperados ao configurar VPNs com FortiGate. Clique em cada bloco para saber mais.

- Certifique-se de que seus firewalls tenham as últimas atualizações e patches de segurança instalados. VPNs são um dos alvos mais preferenciais dos cibercriminosos. Um firewall atualizado minimiza seu risco de se tornar vítima de cibercrime.
- Use níveis de criptografia e hash que atendam aos seus requisitos. Muitos modelos fortiGate incluem processadores de conteúdo (CPs) especializados que podem transferir as operações de criptografia e descriptografia da CPU. no entando, se seu dispositivo não possui essa capacidade, lembre-se de que o uso de algoritmos de criptografia e hash mais fortes exige mais recursos de CPU, o que pode afetar o desempenho do dispositivo
- Verifique se ambos os pares suportam os mesmos recursos de IPsec. Dispositivos mais antigos, ou de outros fabricantes, podem não suportar os mesmos níveis de criptografia, hashing e assim por diante, suportados pelo fortiGate. Você deve verificar quais recursos de IPsec são suportados, pois eles precisam coincidir para poder estabelecer uma conexão VPN IPsec
- Certifique-se de que as portas necessárias estejam abertas em todos os firewalls no caminho de tráfego. O IKE utiliza a porta 500 do Protocolo de Datagramas do Usuário (UDP) por padrão, e a porta UDP 4500 quando o dispositivo VPN está atrás da tradução de endereços de rede (NAT). Um firewall bloqueando essas portas, como as de um provedor de serviço, impedirá o estabelecimento de conexões VPN IPsec.
- Selecione o modo correto ao usar o IKEv1
	- O modo principal é mais seguro, mas mais lento. Esse é o padrão do fortiGate para VPNs site-to-site
	- O modo agressivo é menos seguro, mas mais rápido. Esse é o padrão do FortiGate para VPNs de acesso remoto

## **Configuração de VPNs IPsec**

O FortiGate oferece um assistente intuitivo para ajudar você a configura VPNs IPsec facilmente. O assistente inclui vários modelos com configurações de segurança apropriadas para os cenários mais comuns. As configurações de segurança incluem várias propostas que combinam diferntes níveis de AED para criptografia e SHA-2 para hashing. Se, por razões legais ou de conformidade, você for obrigado a usar parâmetros específicos de segurança, pode criar um túnel personalizado. Isso permitirá que você selecione as configurações específicas que atendem às suas necessidades. Outra opção é converter um túnel criado com um template em um túnel personalizado para poder editar todas as suas configurações.

## **Monitorando Túneis VPN**

A interface gráfica do FortiGate também facilita muito o monitoramento dos túneis VPN. Além de verificar se o status do túnel está ativo ou baixo, também são mostrados detalhes sobre o volume de tráfego e até mesmo o status da Fase 1 e da Fase 2. Isso pode ser muito útil durante a resolução de problemas. Por exemplo, se apenas o túnel da Fase 2 não estiver funcionando, isso significa que os dispositivos pares conseguiram criar o túnel da Fase 1. Saber disso significa que você pode descartar a falta de conectividade como motivo da falha. Você pode verificar se os parâmetros fora mconfigurados corretamente em ambos os dispositivos e se incluem pelo menos uuma proposta de correspondência.


