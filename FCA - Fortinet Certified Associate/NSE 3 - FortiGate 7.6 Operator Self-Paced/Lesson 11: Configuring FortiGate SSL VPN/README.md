# Lesson 11: Configuring FortiGate SSL VPN

Objetivos:

- Descreva o que é SSL VPN e seus benegícios.
- Descreva como funciona a VPN SSL do FortiGate
- Configure a VPN SSL do FortiGate
- Aplique as melhores práticas gerais ao usar a VPN SSL

## **VPN de Camada Segura de Soquete**

A Rede Virtual Privada da Camada de Soquetes Seguros (SSL VPN) é um tipo de VPN que utiliza criptografia SSL para criar uma conexão segura e criptografada enter um dispositivo clientes é um dispositivo que atua como servidor VPN.

Embora a VPN SSL seja mais comumente usada para conceder acesso a trabalhadores remotos às suas redes corporativas, também é possível configurá-la entre dois firewalls FortiGate. Nesta lição, você aprenderá sobre a implementação do acesso remoto.

## **Benefícios do uso de VPN SSL**

Muitas organizações optam por usar VPN SSL para acesso remoto em vez de VPN IPsec. No entanto, cada tecnologia tem seus prós e contras, então você deve analisar sua situação cuidadosamente para fazer a melhor escolha.

Esses são alguns benefícios de usar VPNs SSL com FortiGate. É importante notar que alguns desses benefícios se aplicam apenas a configurações específicas, ex:

- Uso do protooclo comum: SSL é usado para criptgrafar tráfego HTTP e, por padrão, usa a porta 443. Isso significa que normalmente esse tráfego não é bloqueado por firewalls intermiediários.
- Flexibilidade: Dependendo das necessidades dos clientes, eles podem precisar apenas de um navegador para acessar um portal personalizado. Isso é especialmente útil ao lidar com dispositivos móveis. No entanto, também está disponível a opção de instalar software VPN cliente.
- Acesso granular: Administradores podem facilmente restringir quais recursos os clientes podem acessar
- Verificações de integridade para clientes Windows: Esse recurso de segurança garante que dispositivos remotos conectados a VPN estejam em conformidade com as políticas de segurança da organização. Por exemplo, ele pode verificar se o cliente tem um antivírus instalado e negar acesso se não tiver.
- Custo-efetivo: Diferente de outros fornecedores, não é necessária livença adicional para usar VPN SSL. A VPN FortiClient também pode ser disponibilizada para download gratuitamente pelo portal SSL. Além disso, o número de usuários remotos suportados é determinado apenas pelo modelo FortiGate.

## **Funcionalidade de VPN SSL**

VPN SSL estão disponíveis em dois modos: modo web e modo túnel. De acordo com suas necessidades, você pode implantar uma VPN SSL usando um modo ou ambos. Clique em cada modo para conhecer seus detalhes.

- O modo web oferece acesso a aplicações baseadas na web por meio de um navegador web. O usuário só precisa abrir a URL ou endereço IP fornecido e fazer login no portal web. É importante mncionar que o FortiGate funciona como um proxy web reverso para permitir o acesso a aplicações que não são projetadas nativamente para serem acessadas pela web. Esse modo é mais adequado para usuários que precisam acessar um conjunto limitado de recursos, como aplicativos baseados na web, sites de intranet e e-mail entre outros. As principais vantagens desse modo são que ele não requer a instalação de nenhum software cliente, e os administradores podem fornecer acesso muito detalhado aos usuários. Por outro lado, como todo o acesso é feito por uma página web, há um número limitado de aplicações e protocolos suportados. O acesso típico inclui URLs favoritos, servidores FTP, compartilhamentos do Windows e sessões remotas para outros sistemas usando Telnet, SSH, VNC ou RDP.
- O modo túnel oferece acesso total à rede para usuários remotos como se estivessem fisicamente presentes na rede corporativa. Esse modo é mais adequado para trabalhadores remotos que precisam acessar uma ampla variedade de serviços, incluindo aplicações cliente-servidor, compartilhamentos de arquivos e outros recursos típicos de rede. A capacidade de acessar todos os tipos de recursos é a grande vantagem desse modo. No entando, para habilitar isso, você deve instalar e configurar a VPN do FortiClient no dispositivo remoto. Isso pdoe gerar uma sobrecarga extra para a equipe de suporte ao lidar com usuários que não tem conhecimeto técnico e estão tentando usar seus próprios dispositivos.

## **Configuração de VPN SSL**

Configurar a VPN SSL requer várias etapas que variam de acordo com requisitos específicos. O processo é muito simples e envolve os seguintes passos gerais:

-  **Passo 1 -** Criar os usuários e/ou grupos que você deseja conceder permissões para se conectar: Você pode usar usuários ocais ou qualquer um dos servidores de autenticação remota suportados para isso.
-  **Passo 2 -** Revisar e, se necessário, editar os portais SSL VPN> o FortiGate inclui três portais SSL padrão configurados para acessoa web, túnel ou ambos. Você também pode criar portais personalizados para atender necessidades específicas de usuários específicos. Note que a VPN SSL não está ativada por padrão, então nenhum portal será visível até quevocê ative o recurso em System > feature Visibility. Além disso, o modo web também deve ser ativado como uma etapa separada para que seja possível ver o terceiro portal (acessp à web).
-  **Passo 3 -** Configurar as configurações da VPN SSL, que determinam o número de porta que será usado para receber solicitações de conexão, o certificado SSL a ser usado e as opções específicas para cada modo de VPN SSL. Nessa etapa, você também determina quais usuários vão acessar qual portal.
-  **Passo 4 -** Criar uma política de firewall para permitir o tráfego VPN, nesta estapa, você cria a política de firewall que permite que o tráfego passe pelo firewall da mesma forma que com outras políticas. Uma diferença aqui é o uso de uma interface de túnel virtual no campo From para se referir especificamente ao tráfego VPN.

## **Melhores Práticas de VPN SSL**

A seguir, algumas melhores práticas gerais a serem consideradas ao trabalhar com VPN SSL, ex:

- Selecione o modo SSL VPN apropriado: Pode ser possível que seus usuários precisem de apenas um dos modos SSL VPN. Use portais VPN SSL com modo SSL não utilizado desativado.
- Reduza o esforço administrativo usando servidores de autenticação remota: Evite usar usuários locais, sempre que possível. Ter uma solução centralizada de autenticação economiza tempo e evita erros humanos. Isso é especialmetne verdadeiro em ambientes maiores.
- Use um ceritifcado SSL váido: Substitua o ceritifcado autoassinado padrão por outro confiável para os dispostiivos dos seus usuários. Você pode comprar um ceriticado de um fornecedor confiável, ou implmentar sua própria infraestrutura PKI para alcançar isso.
- Use o príncipio do menor privilégio ao configurar políticas de firewall para tráfego VPN: Isso é verdadeiro para qualquer política de firewall, mas é especialmente importante quando você permite que dispositivos remotos se conectem a sua rede.
- Use a verificação de integridade do cliente: Para clientes Windows, sempre verifique se eles têm antivírus, firewall ou ambos instalados
- Se possível, não permita ocnexões de todos os locais: isso nem sempre é viável, mas é ideal restringir o acesso a solicitações de conexão de endereços IP públicos específicos confiáveis pela sua organização.

