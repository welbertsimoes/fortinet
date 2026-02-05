# Lesson 04: Authenticating Network Users

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Entenda a importância de usar autenticação de firewall
- Explique como funciona a autenticação do firewall FortiGate
- Configure a autenticação
- Monitore a autenticação

**Uso de Autenticação de Firewall**

A autenticação de firewall exige que os usuários verifiquem sua identidade para o Fortigate antes de poderem acessar recursos de rede.

Para autenticar, os usuários devem inserir suas credenciais, como nome de usuário e senha. Sem autenticação de firewall, a única informação que o FortiGate conhece sobre o usuário que está originando o tráfego é seu endereço IP de origem, que o fortigate não pode usar para determinar a identidad do usuário.

**Configuração da Autenticação do Firewall** 

Para configurar a autenticação do firewall, você adiciona um usuário ou grupo de usuário de origem a política do firewall. Isso exige que os usuários insiram credenciais no início da sessão.

O Fortigate etão usa a identidade do usuário, junto com as outras regras da política de firewall, para determinar se o tráfego deve ser permitido ou negado.

**Métodos de Autenticação** 

Você pode configurar dois tipos de autenticação de firewall no fortigate: autenticação por senha local e autenticação remota por senha. A diferença entre esses dois métodos está em saber se as credenciais do usuário são armazenadas no Fortigate ou em um servidor de autenticação remota.

**Contas de Convidados**

O método mais simples de autenticaçãoé a autenticação local por senha. As informações do usuário são armazenadas localmente no dispositivo Fortigate. Esse método funciona bem para uma única instalação do Fortigate.

Quando você usa autenticação de firewall, é necessário criar contas individuais para cada usuário que precisa de acesso à rede. Uma conta de usuário local contém tanto o nome de usário quanto a senha.

Você também pode criar grupos locais de usuários para agrupar usuários que precisam do mesmo nível de acesso. Você pode querer agrupar os funcionários por área de negócio, como finanças ou RH, ou por tipo de funcionário, como contratados ou convidados. Na maioria dos casos, é melhor prática usar um grupo em uma política de firewall em vez de contas individuais de usuário.

Você também pode usar autenticação local para grupos de convidados, que contém contas temporárias de usuário que expiram após um tempo predeterminado.

Administradores podem criar manualmente contas de convidados ou criar várias contas de convidados ao mesmo tempo usando IDs de usuário e senhas gerados aleatoriamente. Isso reduz a carga de trabalho dos administradores para grandes eventos. Uma vez criado, você pode adicionar contas ao grupo de usuários convidados e associar o grupo a uma política de firewall.

**Autenticação** 

Quando você usa uma autenticação remota, o fortigate envia as credenciais inseridas pelo usuário para um servidor de autenticação, como o fortiauthenticator. Se o servidor autenticar o usuário com sucesso, o fortigate então aplica a política de firewall correspondente ao tráfego. Na autenticação remota, o fortigate não armazena todas, ou às vezes algumas, das informações do usuário localmente.

**Autenticação de Grupos de Usuários Remotos** 

O uso de autenticação remota é desejável quando múltiplos dispositivos Fortigate precisam autenticar os mesmos usuários ou grupos de usuários, ou ao adicionar o fortigate a uma rede que já contém um servidor de autenticação.

**Adicionando autenticação às políticas do firweall**

Para usar a autenticação de firewall, você precisa incluir uma conta ou grupo de usuário na definição de origem para uma política de firewall, junto com a sub-rede interna. Após isso, quando o tráfego correponde a política de firewall, o usuário deve se autenticar antes que o Fortigate conceda acesso.

**Configuração da Autenticação Local**

Para permitir que o fortigate identifique usuários solicitando acesso, você pode configurar a autenticação local do firewall. Expanda cada tarefa para ver o processo recomendado:

- **TASK 1:** Crie uma conta de usuário no fortigate para armazenar localmente as credenciais dos usuários.
- **TASK 2:** Crie um grupo de usuários baseado no papel ou tipo do usuário e adicione o usuário ao grupo.
- **TASK 3:** Adicione o grupo de usuários como a fonte para uma política de firewall.
- **TASK 4:** Verifique a configuração fazendo com que o usuário autentique e monitore com sucesso usando logs e dashboards do fortigate.

**Configurando a Autenticação Remota**

Para permitir que o fortigate identifique usuários solicitando acesso, você pode configurar a autenticação remota do firewall. Expanda cada tarefa para ver o processo recomendado.

- **TASK 1:** Adicione o servidor remoto no fortigate.
- **TASK 2:** Crie um grupo de usuários e vá mapear usuários remotos autenticados para esse grupo.
- **TASK 3:** Adicione o grupo de usuários como a fonte para uma política de firewall.
- **TASK 4:** Verifique a configuração fazendo com que o usuário autentique e monitore com sucesso usando logs e dashboards do fortigate.




