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
