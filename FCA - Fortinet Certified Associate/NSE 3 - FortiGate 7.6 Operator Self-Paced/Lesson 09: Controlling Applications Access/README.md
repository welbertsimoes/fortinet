# Lesson 09: Controlling Applications Access

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Entenda o controle da aplicação
- Explique como funciona o controle de aplicações do FortiGate para limitar o acesso
- Configure o controle de aplicação FortiGate
- Monitore o controle da aplicação FortiGate

**Controle de Aplicações**

Para melhorar a segurança e atender aos padrões da conformidade, a capacidade de controle de aplicações no FortiGate ajuda a impor o uso aceitável e o fluxo de tráfego resultante das aplicações de rede, conforme definido em uma política.

**Funções do Controle de Aplicação**

O controle de aplicações pode identificar o tráfego de rede gerado por aplicações específicas e tomar as ações apropriadas, como monitorar e bloquear tráfego, ou aplicar modelagem de tráfego para todos ou um conjunto específico de usuários de uma política de firewall.

Ser capaz de controlar o fluxo de tráfego de aplicaçẽos de rede pode não ser um requisito prioritário dentro da arquitetura cliente-servidor tradicional que utiliza um protocolo de conexão definido sobre um número de porta padrão.

No entando, a necessidade de controlar o tráfego de aplicações está se tornando cada vez mais relevante dentro da arquitetura peer-to-peer, onde muitos servidores precisam enviar tráfego usando protas dinâmicas, como BitTorrent.

**Controle do Acesso a Aplicações**

Protocolos peer-to-peer utilizam técnicas evasivas para burlar as políticas tradicionais de firewall. Portanto, o controle de aplicações FortiGate envolve a correspondência de padrões conhecidos aos padrões de transmissão da aplicação.

O banco de dados para assinaturas de controle de aplicações é fornecido pela FortiGuard Labs.

A análise de tráfego é realizada pelo motor IPS, que utiliza inspeção b aseada em fluxo. Assim, a correspondência de padrão é realizada diretamente em todo o fluxo de bytes do pacote, independentemente do protocolo ou do número da porta.

**Configurações de controle de Aplicação**

No perfil de Controle de Aplicação, você pode configurar as configurações de controle de aplicação, que devem ser aplicadas posteriormente na política de firewall.

No perfil de Controle de Aplicação, as assinaturas da aplicação são agrupadas por categoria, e você pode definir cada categoria para monitorar, permitir, bloquear ou quarentena.

Para fornecer mais detalhe, você pode configurar cada assinatura de aplicação ou grupo de assinaturas especificamente usando a opção de sobrescritura. Por exemplo, a opção de substituição permite bloquear aplicativos do Facebook enquanto ainda permite que os usuários colaborem usando chat do Facebook.

**Configuração do Controle de Aplicações**

Para resumir a configuração baseada em perfil que limita o acesso a aplicações específicas, ex:

- **TASK 1 -** Crie um perfil de controle de aplicação ou modifique um pré-configurado.
- **TASK 1 -** Modificar ações nas categorias de aplicação ou configurar a substituição de aplicação.
- **TASK 1 -** Selecione o perfil correto de controle de aplicação na política do firewall.
- **TASK 1 -** Verifique a configuração tentando acessar o aplicativo correspondente.
- **TASK 1 -** Use logs FortiGate para monitorar limitações de acesso às aplicações.
