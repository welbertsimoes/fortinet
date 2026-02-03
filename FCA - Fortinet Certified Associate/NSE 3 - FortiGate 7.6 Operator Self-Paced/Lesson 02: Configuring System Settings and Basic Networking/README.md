# Lesson 02: Configuring System Settings and Basic Networking

Anotações aqui...

# Configurações do Sistema e Rede Básica

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Configurar contas adicionais de administrador
- Configurar interfaces de rede
- Configurar VLANs
- Configure o FortiGate como um servidor DHCP
- Configure rotas estáticas
- Monitore rotas estáticas

O FortiGate possui uma conta padrão de administrador com permissões de configuração completas no dispositivo. Agentes mal-intencionados estão cientes dessa conta, tornando-aum alvo comum para seus ataques.

É boa prática criar contas adicionais de administrador para gerenciar seus firewalls FortiGate. Usar contas de administrador separadas traz as seguintes vantagens:

- Isso reduz a dependência da conta padrão de administrador.
- Reduz o risco ao limitar o acesso com base nos cargos do cargo. Por exemplo, um administrador pode monitorar apenas logs, enquanto outro tem todos os direitos de configuração.
- Ele garante responsabilidade ao acompanhar as mudanças de configuração para usuários específicos.

Por causa de seus papéis administrativos, novas contas de administrador não são criadas da mesma forma que os usuários comuns, nem possuem as mesmas configuraçõs.

Use os seguintes passos para criar uma conta de administrador:

- Vá em Administradores > Sistema > Criar um novo Administrador >
- Especifique o nome da conta
- Especifique onde a conta será armazenada, se localmente ou remotamente
- Digite e depois confirme uma senha, ou o grupo de autenticação remota, ou ambos
- Selecione o perfil de administrador da conta. Opcionalmente, ative autenticação em dois fatores, hosts confiáveis e restrições de provisão de contas de convidade, se aplicável.

Independentemente das opções selecionadas, você deve atribuir um perfil de administrador a cada conta. Perfis de administrador definem o que o administrador tem permissão para fazer ao fazer login no FortiGate. O FortiGate inclui vários perfis padrão, mas você pode criar perfis personalizados, para atender às suas necessidades específicas. Para cada uma das seções de configuração disponíveis, você pode atribuir acesso somente leitura, acesso de leitura-gravação ou sem acesso.

Interfaces físicas e virtuais permitem que o tráfego flua entre redes internas, e entre a internet e as redes internas. O FortiGate oferece opções para configurar interfaces que podem escalar conforme sua organização cresce.

Você pode configurar uma variedade de configurações nas interfaces do FortiGate, incluindo:

- **Alias:** Um nome que identifica a interface para referência
- **Endereço IP:** O endereço IP público ou privado usado para se conectar a interface.
- **Acesso administrativo:** Os protocolos que podem ser usados para se conectar à interface para fins administrativos, como https, ping e ssh
- **Servidores DHCP:** Um servidor que atribui dinamicamente endereços IP a hosts na rede conectada à interface.

VLANs são uma tecnologia que permite dividir sua LAN física em múltiplas LANs lógicas. Cada VLAN forma um domínio de broadcast separado. Uma tag é adicionada a cada quadro ethernet para identificar a VLAN à qual ela pertence. Firewalls FortiGate podem utilizar VLANs de várias formas: para isolar dispositivos, reduzir tráfego desnecessário e oferecer melhor controle sobre o fluxo de dados dentro da rede.

O FortiGate oferece várias formas de usar VLANs dependendo do modo que está rodando e do modelo do dispositivo. Clique em cada item para saber mais sobre cada opção.

- **Modo NAT:** O FortiGate opera como um dispositivo de camada 3, o que significa que pode rotear tráfego entre diferentes VLANs e realizar NAT. VLANs são configuradas como subinterfaces em portas físicas, e cada subinterface está associada a um ID específico de VLAN. Múltiplas VLANs podem coexistir na mesma interface física, caso possuam IDs de VLAN diferentes. O FortiGate controle o tráfego entre VLANs internas e redes externas, como a internet. Você pode aplicar políticas de segurança a cada subinterface VLAN individualmente, permitindo controle de acesso granular e um manejo otimizado do tráfego.
- **Modo Transparente:** O FortiGate como uma ponte de camada 2. Nesse modo, o FortiGate passa o tráfego marcado por VLAN, mas ainda aplica recursos de segurança como varredura antivírus, filtragem web e prevenção de intrusões. No entando, ele não suporta certos serviços como VPNs SSL, servidores DHCP ou NAT completo. O modo transparente é ideal quando as mudanças de rede precisam ser mínimas, pois você pode colocar o FortiGate entre dois troncos VLAN sem precisar alterar a configuração de outros switches. Os administradores devem criar subinterfaces VLAN correspondentes tanto em interfaces internas quanto externas, e então definir políticas de segurança para permitir o fluxo de tráfego. O FortiGate inspeciona pacotes removendo tags, aplicando filtragem e depois reclassificando-os antes de encaminhar.
- **VLAN Virtual:** Alguns modelos FortiGate suportam um switch VLAN virtual, que permite que portas de switch de hardware operem como um switch gerenciado de camada 2. As portas podem ser atribuídas a VLANs específicas ou configuradas como portas tronco para transportar múltiplas VLANs. Essa configuração é útil em cenários de HA ou para estender VLANs entre dispositivos.

Configurar uma interface VLAN no FortiGate é muito semelhante a configurar uma interface física. Para criar uma interface VLAN usando a interface gráfica, clique em Interfaces > Rede > Criar Nova, depois selecione Interface. No campo Tipo, esoclha VLAN. Em seguida, selecione o protocolo VLAN. A escolha mais comum é 802.1Q, que suporta até 4094 VLANs e é adequado para a maioria dos ambientes. Para rees maiores que exigem mais escalabilidade, você pode optar pelo 802.1ad. Você deve então especificar o ID da VLAN e a interface física à qual a VLAN será associada. Lembre-se de que uma única porta pode ser associada a múltiplas VLANs. Como em qualquer interface, atribua um endereço IP manualmente, dinamicamente usando DHCP ou usando outro método. Por fim, você pode configurar protocolos de acesso administrativo, habilitar o servidor DHCP e ajustar outras configurações opcionais, dependendo das suas necessidades específicas.

Um servidor DHCP atribui dinamicamente endereços IP a dispositivos na rede conectados a interface. Você pode configurar um ou mais servidores DHCP em qualquer interface FortiGate.

Uma configuração de servidor DHCP inclui:

- **Faixa de Endreços:** A faixa de endereços IP que o FortiGate atribui aos dispositivos.
- **Máscara de rede:** A máscara de rede do endereço que o FortiGate atribui aos dispositivos.
- **Gateway padrão:** O gateway padrão que o FortiGate atribui aos dispositivos. Por padrão, esse gateway é o mesmo que o endereço IP da interface.
- **Servidor DNS:** O servidor DNS que o FortiGate atribuirá aos dispositivos. Por padrão, este é o mesmo servidor DNS usado pelo FortiGate.

O roteamento estático é a forma mais básica de configurar o roteamento em um dispositivo de rede, incluindo dispositivos firewall como o FortiGate. O FortiGate tem uma rota padrão para seu gateway para fornecer acesso à rede internet. Mesmo em uma configuração mais complexa, provavelmente você encontraria rotas estáticas implantadas. Todas as rotas fazem parte da tabela de roteamento, que o FortiGate usa para igualar o tráfego recebido e determinar para onde enviar esse tráfego em seguida.

Uma rota estática inclui:

- **Destino:** O FortiGate usa o destino para alinhar o tráfego que chega à rota correta.
- **Endereço de Gateway:** Este é o endereço IP para o qual o FortiGate encaminha o Tráfego.
- **Interface:** Essa é a interface que o FortiGate usa para encaminhar o tráfego para seu destino.

A rota padrão informa ao FortiGate para onde enviar o tráfego quando os pacotes não incluem uma correspondência exata para o endereço de destino na tabela de roteamento do FortiGate. Normalment, todos os usuários que estão atrás do FortiGate precisam de uma rota padrão para ter acesso à internet.

Na rota padrão, o endereço de destino é definido como 0.0.0.0. O endereço do gateway normalmente é o endereço de outro roteador, seja um dispositivo na sua rede que fica entre o FortiGAte e a borda da rede, ou parte da rede do seu provedor se o FortiGate estiver localizado na borda da rede. Por fim, a interface é a porta FortiGate que se conecta a esse roteador, normalmente a interface WAN.

Cada rota estática que você cria passa a fazer parte da configuração do FortiGate e você pode verificar isso na interface gráfica em Network > Static Routes. Essas rotas estáticas que você cria permanecerão na configuração até que você as delete.

Várias confições podem impedir que uma rota configurada seja adicionada à tabela de roteamento e, consequentemente, não seja usada para encaminhar tráfego. As condições mais comuns são:

- A rota está mal configurada
- A porta associada à rota está fora do ar ou desativada.
- Existe uma rota melhor para encaminahr o tráfego até esse destino.

Na captura de tela mostrada no slide, você pode ver que há uma rota estática com destino 172.16.30.0/24. No entanto, como o port6 está desativado, essa rota não está incluída na tabela de roteamento que também é mostrada.

Para exibir a tabela de roteamento e verificar se uma rota esperada está faltando, você pode ir ao Painel > Rede > Roteamento estático e Dinâmico. Checar a tabela geralmmente é um dos primeiros passos que você vai dar ao resolver problemas de conectividade de rede.


