# Lesson 07: Control Web Access Using Web Filtering

Após concluir esta lição, você será capaz de alcançar estes objetivos:

- Entenda por que você deve usar filtragem web
- Descreva as categorias do FortiGuard
- Configure o filtro web do FortiGate

**Uso do Filtragem Web**

Então, por que organizações, e pessoas em geral, usam filtragem web? O filtragem web ajuda a controlar, ou rastrear, os sites que as pessoas visitam. Existem mutios motivos pelos quais administradores de rede aplicariam filtragem web:

- Limitar o acesso a sites que distraem, como redes sociais, para manter seus funcionários focados no trabalho e manter a produtividade
- Para evitar congestionamento de rede, garantindo que os usuários não usem largura de banda valiosa para fins não comerciais, como straming de vídeo.
- Diminuir a exposição a ameaças baseadas na web limitando o acesso a sites potencialmente prejudiciais
- Para limitar a responsabilidade, caso os funcionários tentem baixar material inadequado ou ofensivo
- Para evitar que usuários visualizem material inadequado

## **Filtros de Categoria FortiGuard**

- **Web Filter 1:** Para filtragem web, o FortiGate pode usar filtros de categoria FortiGuard para controlar o acesso à web. As categorias FortiGuard são derivadas do serviço de filtragem web FortiGuard.
- **Web Filter 2:** O serviço inclui o Bando de Dados de Categorias de URL FortiGuard, que classifica bilhões de páginas da Web em uma ampla variedade de categorias de classificação.
- **Web Filter 3:** Cada categoria contém sites ou páginas web que foram atribuidos com base no conteúdo dominante. Essas categorias podem, por sua vez, ser bloqueadas ou permitidas de acordo com seu conteúdo. O bando de dados categoriza o conteúdo da web com base na sua adequação para visualização para três grandes grupos de consumidores: empresas, escolas e residências e famílias. Por exemplo, o Twitter é categorizado como parte da categoria interesse Geral - Pessoal. Enquanto o Dropbox é categorizado como parte da categoria consumindo largura de banda.
- **Web Filter 4:**- Note que as categorias podem ser ainda divididas em subcategorias. A categoria interesse Geral - Pessoal inclui subcategorias como Redes Sociais, notícias e Mídia.  Enquanto a categoria de consumo de Largura de Banda inclui subcategorias como Compartilhamento e Armazenamento de ARquivos, telefonia pela internet e streaming de mídia e download.

**Aplicação de Filtros de Categoria FortiGuard**

O Fortigate trabalha com as categorias do FortiGuard para determinar como os sites são filtrados. Em vez de bloquear ou permitir sites individualmente, o filtro por categorias do FortiGuard analisa a categoria com a qual o site foi avaliado. O fortigate bloqueia ou permite o acesso a sites, com base nas ações definidas para aquela categoria, não na URL.

**Aplicando ações de Categoria FortiGuard**

O FortiGate permite ou bloqueia conexões com sites com base nas ações configuradas para a categoria de filtro web do Fortiguard no FortiGate. as seguinte ações de categoria de filtro web do FortiGuard estão disponíveis.


**Configure um Filtro Web para uma Categoria FortiGuard**

Para melhorar a segurança da rede, você pode configurar o FortiGate para filtragem web com base nas categorias do FortiGuard. Expanda cada tarefa para identificar o processo recomendado.

- **TASK 1 -** Certifique-se de que o fortigate possui uma licença válida de assinatura de segurança do FortiGuard
- **TASK 1 -** Identifique como o serviço FortiGuard Categoriza o site específico que você está tentando bloquear ou permitir
- **TASK 1 -** Configure um perfil de filtragem web para usar filtros baseados em categorias do FortiGuard
- **TASK 1 -** Aplique o perfil de segurança do filtro web a uma política de firewall para começar a inspecionar o tráfego web. Nesse ponto, se quiser gerar logs, ative o loggin na política do firewall.
- **TASK 1 -** Teste o perfil de segurança do filtro web configurado para os filtros baseados em categorias do FortiGuard especificados.



