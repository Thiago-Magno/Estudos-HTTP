# Entendendo o que é HTTP

O que acontece é uma troca de mensagens entre o browser e o servidor, o browser faz um pedido e o servidor responde

## Mensagem :speech_balloon: 

![Exemplo1](./Imagens%20aulas/caminho1.png)

### Pedido :incoming_envelope:
    No pedido é preciso definir o tipo de pedido, alem falar qual a ação que queremos fazer no servidor.
    Todo pedido tem um cabeçalho e um corpo(mas são opcionais).

#### GET
    Pegar algum recuros de dentro do servidor

#### Post
    Postar/criar um recurso no servidor

### Resposta 	:e-mail:

![Exemplo2](./Imagens%20aulas/caminho2.png) 

#### Status code
    É forma em qual se encontra o pedido, o estado em qual ele esta, ele foi concluido?
    esta em processo?
    ou ocorreu algum erro?
      
    * 200: concluido
    * 301: redireciodo, como por exemplo foi redirecionado a um novo URL
    * 404: pagina/arquivo não encontrado
    * 500: erro interno de servidor


​     
#### Request message
![Exemplo de Resqueste](./Imagens%20aulas/request.png)
    Onde é dito qual o método(no caso o GET), qual recuros(no caso o index.html) e a versão do HTTP(versão 1.1 no exemplo); Cabeçalho User-Agent: mozilla/4.0 broser 
#### Response message
![Exemplo de Response](./Imagens%20aulas/response.png)
    Vesão do HTTP 200 ok(Indica que deu tudo com o pedido),
    o tipo de server(Express no caso do exemplo) e o topo de conteudo(: text/html) 
### Resquest/Response

#### Headers
    São campos informativos.

#### Body
    Serve como um tipo de conteudo, pode ser um HTML ou um JSON.

## Visualizando com DevTools
Abre com F12, na aba Network podemos observar as atividade que ocorrem em uma pagina no navegador

### curl
    é o nosso client que vai fazer conversa entre ele e o servidor

## Cliente :mag:
    O cliente é o User Agent normalmente o browser, pode também ser o cURL
    É sempre ele que começa a comunicação com o server, a não ser que sejá programa para o server começar a interação.

### Ações do cliente
    As ações do cliente são as ações que o cliente consegue fazer na comunicação como os abaixo(request):


## Servidor :globe_with_meridians:
    É uma maquina ao redor do mundo esperando para mandar a resposta.
    Sempre esta responsavel por mandar a resposta.

## Proxier
    São representantes entre o cliente e o servidor, eles nos ajudam a fazer a comunicação, com o servidor
### Funções

#### Cache
    guarda uma informação muito requisitada para ter um acesso mais rapido caso ela seja requisitada novamente

#### Filtro
    Permite fazer um controle de site, entre outras coisa

#### Load balancing(Distribuição de carga)
    Por exemplo no caso de estarmos fazendo um upload de um arquivo muito grande,
    o proxy balanceia isso dividindo em varios outros proxies para dividir o "peso"

#### Autenticação
    Autenticação para se comunicar com a internet

#### Autorização
    Autorização para se comunicar com a internet

## URI
    Sigla para: Uniform Resource Identifier

#### Conceito
    É um forma de encontrar os recursos pedidos, e para fazer isso ele usa o nome do recurso eou a localização

### Resource
    É o alvo do pedido HTTP, esse recurso pode ser qualquer coisa/entidade identificavel.
    Se podemos identificar, nomear, endereçar ou manipular estamos falando de um recurso .

## Locator

#### URL
    URL(Uniform Resource Locator), o URL é composto por componentes opcionais que são
    componentes que afetam a area do local(site) o que é e onde é encontrado(ex: seção contato de um site/um video no yt.)
    e obrigatório que o local em si(site).
    Toda URL é uma URI mas nem toda URI é uma URL.

##### Obrigatórios:
    * Dominio: É como se fosse o nome do site;
    * Protocolo: é um protocolo para o recurso que. esta sendo buscado(ex: http:// e https://)

##### Opcionais: (opcianal quer dizer que é não obrigatorio ou não precisa ser colocado)
    * Subdominio: é o que vem antes do dominio as vezes necessario para encontra a pagina web;
    * Path: É o caminho para encontra um recurso especifico do dominio (ex: https://app.rocketseat.com.br/node/guia-estelar-de-http,
    me leva ao guia estelar de http da rocketseat), se não houver um caminho normalmente o usuario é encaminhado para o dominio;
    
    * Parametro: É usado para encontra um recurso no BD, por exemplo um video no yt precisa de um parametro para ser encontrado;
    * Porta: Algum local dentro do servidor que esta disponivel para chegar a um endereço, as vezes essa porta pode estar fechada impossibilitando a chegada;
    * Âncora: Algum lugar dentro do documento, esta procurando algo dentro do documento.
### Name

#### URN
        Uniform resource name, pode se usar para encontra um recurso por nome, mas no desevolvimento web é mais favoravel e mais utilizado o URL.

## HTTP Messages
    Tipos de HTTP:
    * HTTP/1.1: é uma das formas da mensagem HTTP escrito em uma mais legivel e textual;
    * HTTP/2: uma versão mais moderna e binaria do HTTP, mas funciona da mesma maneira do HTTP/1.1.

### Mensagens
    Temos dois tipos de mensagens HTTP o request(pedido) e o response(resposta ao pedido).

#### Request
    * É o pedido em um http/https;
    * Para ver a saida de dados use o comando no curl:
        -v https//:google.com.br 
    
    * ">" é onde indica a saida dos dados de uma mensagem;   
    * O tipo de mensagem tem como padrão o tipo Request, caso não tenha sido
    especificado na mensagem o tipo da mesagem vai acabar sendo request;  

#### Response
    * Exibe a resposta do server:
        -i https//:google.com.br
    * contem a versão do protocolo, status code, headers e status message que é o corpo da mensagem;
    * Exibe tudo menos o status message/corpo da mensagem:
        -I https//:google.com.br

## Iniciando o JSON
    Para iniciar o json server nos precisamos utilizar o comando: 
    json-server --watch db.json
    
    Isso assumindo que o arquivo json já foi criado e salvo previamente. Caso não tenha sido criado utilizar o comando:
    vim db.json
    
    Esse comando vai permitir tanto que seja criado o arquivo db.json quanto edita-lo
    diretamente do terminal colocando as configurações iniciais do json.


## Métodos HTTP

### Methods
    Os metodos HTTP são a indicação de uma ação por parte do cliente;
    Adendo:
    - Cada metodo possui sua propria semantica;
      
    A imagem abaixo mostra quais são os metodo e se são seguro(se mudam algo no servidor) e
    idempotentes(quando o metodo é executado a resposta é sempre a mesma)
![Exemplo idempotencia](Imagens%20aulas/Idempotence.png)

#### OPTIONS
    Caracteristicas:
    É usado para verificar a disponibilidade dos metodos da requisição,
    é seguro já que não faz mudanças no servidor, não tem cache porque pode
    haver mudanças nos estados dos metodos, não tem body. 
    
Comando no teminal:

    curl -X http://localhost:3000/posts -i

#### GET
    Serve para pegar os recursos, caracteristicas:
    * Seguro: sim;
    * Idempotente: sim;
    * Body: sim
    - Request: não;
    - Response: sim;
    * Cache: sim;
    * Uso em forms HTML: sim. Dependendo do pedido é melhor não usar,
    mas se for o caso de uma simple pesquisa na maior parte dos caso o uso de form html é o ideal.
    
Comando no teminal:

    curl -v http://localhost:3000/posts

#### HEAD
    Parecido com o GET, mas recebemos apenas o cabeçalho ao inves do body
    Caracteristicas:
    * Seguro: sim;
    * Idempotente: sim;
    * Body: não;
    * Uso em form HTML: não;
    * cache: sim.

Comando utlizado:

    Comando no teminal: curl -I http://localhost:3000/posts

#### POST
    Publica/inclui algum recurso em algum lugar
    Caracteristicas:
    * Seguro: Não;
    * Idempotente: Não
    * Body: Sim, depende de como foi configurada a app;
    * Uso em form HTML: Sim;
    * Cache: Sim;

Comando utilizado:

     curl -d ' "Nota: apos o -d é colocado as infomações que serão inseridas no json" { "id": 2, "title": "json-server-2", "author": "thiago magno" }' -H "Content-type: application/json" -X POST http://localhost:3000/posts


#### PUT
    Usado para criar e atualizar recursos, status code de criação: 200, status code de atualização: 204 ou 200.
    * Seguro: Não;
    * Idempotente: Sim:
    * Body:
    - Request: Sim;
    - Response: Não;
    * Uso em form HTML: Não;
    * Cache: Não;

É o mesmo comando do POST, mas é colocado o PUT no lugar do POST:

    curl -d ' { "id": 2, "title": "json-server-2", "author": "thiago magno" }' -H "Content-type: application/json" -X PUT http://localhost:3000/posts

#### PATCH
    O PATCH serve para fazer uma modificação parcial do recurso, diferente do PUT que faz a modicação do recurso inteiro.
    * Seguro: Não;
    * Idempotente: Não;
    * Body: Sim; 
    * Uso em form HTML: Não;
    * Cache: Não.

Comando utilizado:

    curl -d ' { "author": "thiago magno" }' -H "Content-type: application/json" -X PATCH http://localhost:3000/posts

#### DELETE
    Deleta um recurso.
    * Seguro: Não;
    * Idempotente: Sim;
    * Body:
    - Request: Possivel;
    - Response: Possivel;
    * Uso em form HTML:;
    * Cach:;

 Comando Utilizado:

    curl -X DELETE http://localhost:3000/post/2

    Deleta o post#2

## HEADER
    Normalmente escrito com nome:valor ou property:value.
    A maioria dos clients já possuem headers já pre-definidos.

### General
    Serve tanto para o response tanto para o request, sendo um header geral,
    onde mostra o metodo, status code, remote address serve como um endereço do servidor,
    referrer policy.

### Request
