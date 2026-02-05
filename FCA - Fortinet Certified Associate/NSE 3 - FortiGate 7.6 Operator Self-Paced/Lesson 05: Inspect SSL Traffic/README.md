# Lesson 05: Inspect SSL Traffic

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Descrever por que o tráfego SSL deve ser inspecionado
- Descreva como funciona a inspeção SSL no FortiGate
- Configure uma inspeção SSL em uma política de firewall

**Uso de Inspeção SSL**

O HTTPS oferece proteção aplicando criptografia ao tráfego web, no entando, também apresenta um risco potencial de segurança, pois atacantes podem tentar usar tráfego criptografado para contornar as defesas normais da sua rede.

**Uso da Inspeção SSL para inspecionar o Tráfego Criptografado**

Por exemplo, Bob se conecta ao site example.com. Este site possui um certificado emitido por uma autoridade certificadora legítica (CA). Como a CA é aprovada, um certificado de verificação válido está no armazenamento de certificados do Bob, e o navegador do Bob estabelece uma sessão SSL com o site. No entando, sem que o Bob saiba, o site example.com foi infectado por um vírus. O vírus, oculto por criptografia, passa pelo fortigate sem ser detectado e entra no computador de Bob. Para evitar isso, você pode usar a inspeção SSL para inspecionar o tráfego criptografado.

**Tipos de Inspeção SSL**

Existem dois tipos diferentes de inspeção SSL Fortigate:

- **Inspeção de certificados**
- **Inspeção profunda**

**Inspeção de Certificados**

Quando você usa a inspeção do certificado SSL, o Fortigate inspeciona o handshake SSL/TLS quando uma sessão começa. Ao fazer isso, o Fortigate verifica a identidade do servidor web e garante que o protocolo HTTPS não seja usado como solução alternativa para acessar sites que você bloqueou usando filtragem web.

O único recurso de segurança que você pode usar no modo de inspeção de certificados SSL é o filtragem web. No entando, esse método não introduz erros de certificado e pode ser uma alternativa útil a inspeção profunda SSL quando você usa filtragem web.

**Inspeção Profunda**

Quando você usa a inspeção profunda SSL, também conhecida como inspeção completa, o Fortigate se passa pelo destinatário da sessão SSL de origem, depois descriptografa e inspeciona o conteúdo para identifica ameaças e bloquea-las. Se o conteúdo estiver seguro, o FortiGate o recriptografa e o envia para o destinatário real.

Você pode aplicar todos os tipos de varredura de segurança com inspeção profunda SSL, incluindo filtragem web. A inspeção profunda não apenas protege você de ataque sque usam HTTPS, como também de outros protocolos comumente usados com criptografia SSL, como SMTPS, POP3S, IMAPS e FTPS.

**Perfis de Inspeção SSL do Fortigate**

Para usar a inspeção SSL do Fortigate, você aplica um perfil de inspeção SSL à política do firewall.

O FortiOS inclui quatro perfis de inspeção SSL pré-carregados, três dos quais são somente leitura:

- Certificado-inspeção
- Inspeção profunda
- Sem inspeção

Você pode editar o quarto perfil pré-carregado, custom-deep-inspection. Você também pode clonar qualquer um dos perfis somente leitura ou criar seu próprio perfil de inspeção personalizado.

**Avisos de Certificados**

Quando você usa inspeção profunda SSL usando o certificado CA FortiGate, seu navegador exibe um aviso de certificado toda vez que você se conecta a um site HTTPS. Isso ocorre porque o Fortigate está gerando um certificado que parece ser do site correto, mas é assinado pela CA FortiGate, que não é uma CA em que o navegador confia por padrão. Isso faz parecer que o FortiGate está realizando um ataque de homem no meio.

Por exemplo, um usuário de rede se conecta a <https://facebook.com>. O tráfego do servidor web do Facebook usa o certificado real do Facebook, assinado por uma conhecida CA. O Fortigate intercepta esse tráfego e o descriptografa. Então, quando é considerado seguro, o Fortigate repassa o tráfego para o usuário final. O tráfego agora usa um certificado com o nome <https://facebook.com>, mas o certificado é assinado pela Fortigate CA.

Erros de certificado também pode aparecer quando você usa a inspeção de certificados SSL, por que o FortiGate usa seu certificado Ca par acriptografar a mensagem de substituição que aparece quando você tenta navegar para um site bloqueado via HTTPS.

**Evitando Avisos de Certificados**

Para evitar avisos de certificado, faça um dos seguintes procedimentos:

- Baixe o certificado Fortinet_CA_SSL e instale-o em todas as estações de trabalho como uma autoridade root confiável.
- Use um certificado SSL emitido por uma CA e garanta que o certificado esteja instalado nos navegadores necessários.
