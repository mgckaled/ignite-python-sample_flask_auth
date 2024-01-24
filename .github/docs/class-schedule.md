# Roteiro das aulas

> [voltar](../../README.md) para a página anterior

## Sumário

- [Roteiro das aulas](#roteiro-das-aulas)
  - [Sumário](#sumário)
  - [Roteiro](#roteiro)
    - [1. Primeiros Passos](#1-primeiros-passos)
      - [Introdução](#introdução)
      - [Apresentação do Projeto](#apresentação-do-projeto)
      - [Instalando dependências e criando repositório no Github](#instalando-dependências-e-criando-repositório-no-github)
    - [2. Banco de Dados e SQLAlchemy](#2-banco-de-dados-e-sqlalchemy)
      - [Conceito de banco de dados e utilização do SQLAlchemy - parte 1](#conceito-de-banco-de-dados-e-utilização-do-sqlalchemy---parte-1)
      - [Conceito de banco de dados e utilização do SQLAlchemy - parte 2](#conceito-de-banco-de-dados-e-utilização-do-sqlalchemy---parte-2)
      - [Modelando o Usuário](#modelando-o-usuário)
      - [Criando o banco de dados e organizando componentes](#criando-o-banco-de-dados-e-organizando-componentes)
    - [3. Autenticação e Flask-Login](#3-autenticação-e-flask-login)
      - [Autenticação com Flask - login - parte 1](#autenticação-com-flask---login---parte-1)
      - [Autenticação com Flask - login - parte 2](#autenticação-com-flask---login---parte-2)
      - [Criando usuário e realizando autenticação](#criando-usuário-e-realizando-autenticação)
      - [Criando Views de Logout e Cadastro de Usuário - parte 1](#criando-views-de-logout-e-cadastro-de-usuário---parte-1)
      - [Criando Views de Logout e Cadastro de Usuário - parte 2](#criando-views-de-logout-e-cadastro-de-usuário---parte-2)
      - [Rotas de Read e Update do Usuario](#rotas-de-read-e-update-do-usuario)
      - [Rotas de Delete de Usuário](#rotas-de-delete-de-usuário)
    - [4. Finalizando o Projeto](#4-finalizando-o-projeto)
      - [Atualizando repositório do Github](#atualizando-repositório-do-github)
      - [Utilizando o banco de dados MySQL](#utilizando-o-banco-de-dados-mysql)
      - [Gerenciamento de Perfil](#gerenciamento-de-perfil)
      - [Criptografia de senhas](#criptografia-de-senhas)
      - [Finalização](#finalização)

## Roteiro

### 1. Primeiros Passos

#### Introdução

Nesta aula do módulo 4, vamos aprender sobre autenticação em APIs e integração com bancos de dados. Desenvolveremos um projeto completo de autenticação para APIs, incluindo login, logout, cadastro, deleção, atualização e leitura de usuários. Também entenderemos a importância de um banco de dados para persistir os dados da nossa aplicação. A autenticação é fundamental em muitos sistemas, independentemente do objetivo. Estou animado para continuar com vocês neste módulo. Nos vemos na próxima aula!

#### Apresentação do Projeto

Nesta aula, vamos construir um projeto de autenticação em uma API usando Flask. Vamos integrar um banco de dados para armazenar os usuários e teremos um sistema de gerenciamento de perfis para controlar o acesso aos endpoints da API. Teremos rotas de login, logout, cadastro de usuários, recuperação de informações, alteração de senha e exclusão de usuários. Durante o módulo, vamos aprender a construir e implementar essa API. Estou animado para ter você comigo. Até a próxima aula!

#### Instalando dependências e criando repositório no Github

Nesta aula, vamos começar o desenvolvimento do projeto focado em banco de dados e autenticação. Começaremos criando um repositório no GitHub e clonando-o para o nosso computador. Em seguida, abriremos a pasta do repositório no Visual Studio e criaremos um arquivo chamado `requirements.txt` para listar as dependências do projeto, como Flask, Flask-SQLAlchemy, Flask-Login e Werkzeug. Faremos o commit dessas alterações e discutiremos a importância de fazer commits pequenos e bem separados. Por fim, faremos a instalação das dependências usando o comando `pip3 install -r requirements.txt`. Na próxima aula, continuaremos o desenvolvimento da API.

> [retornar](#roteiro-das-aulas) para o topo da página

### 2. Banco de Dados e SQLAlchemy

#### Conceito de banco de dados e utilização do SQLAlchemy - parte 1

Nesta aula, vamos abordar o tema de banco de dados. O objetivo do projeto deste módulo é criar um sistema de autenticação vinculado a um banco de dados. Vamos aprender a cadastrar usuários, gerenciá-los e realizar login e logout. Antes de começar, é importante entender o papel do banco de dados na persistência de informações. Em projetos anteriores, armazenamos dados em estruturas de dados do Python, como listas e dicionários. No entanto, esses dados eram perdidos quando reiniciávamos o programa. Isso ocorre porque esses dados são armazenados na memória RAM, que é volátil e não persiste os dados. Para resolver esse problema, utilizamos um banco de dados, que é uma ferramenta para persistir informações. Existem diferentes tipos de bancos de dados, como MySQL, PostgreSQL e MongoDB. Neste projeto, vamos utilizar o SQLite, que é um banco de dados relacional de código aberto. O SQLite é uma ótima opção para projetos de desenvolvimento, pois é leve e fácil de usar. No entanto, não é tão adequado para aplicações em produção, devido às limitações de gerenciamento de requisições concorrentes. Vamos utilizar o Flask SQL Alchemy, que é uma extensão do Flask que suporta o SQL Alchemy. O SQL Alchemy é um ORM (Object Relational Mapper), que nos permite abstrair as funções do banco de dados e facilita a troca de banco de dados no futuro. Recomendo que você consulte a documentação do SQL Alchemy para obter mais informações sobre como utilizá-lo.

#### Conceito de banco de dados e utilização do SQLAlchemy - parte 2

Nesta aula, começamos criando uma aplicação Flask chamada `app.py`. Em seguida, criamos uma rota simples chamada `\hello-world` para testar se a aplicação está funcionando corretamente. Depois disso, importamos a classe SQL Alchemy do Flask SQL Alchemy para estabelecer a conexão com o banco de dados. Configuramos a chave secreta e a URL do banco de dados. Por fim, discutimos que na próxima aula iremos mapear os usuários e criar as tabelas correspondentes no banco de dados.

#### Modelando o Usuário

Nesta aula, continuamos o desenvolvimento da nossa aplicação de autenticação conectada ao banco de dados. Criamos uma pasta chamada `models` para organizar melhor nossos componentes. Dentro dessa pasta, criamos o arquivo `user.py` para definir o modelo do usuário. Importamos o DB do nosso app e criamos a classe User, que herda da classe `db.Model`. Definimos as colunas do modelo, como o identificador (chave primária), o nome de usuário e a senha. Explicamos a importância da chave primária e como definir a propriedade `nullable` para permitir ou não valores nulos nas colunas. Também mencionamos outros tipos de dados que podem ser usados, como texto, data e hora, float e booleano. Encerramos a aula explicando que o mapeamento de modelos é fundamental para persistir informações no banco de dados e que continuaremos a adicionar mais informações e aprender mais sobre modelagem com Flask na próxima aula.

#### Criando o banco de dados e organizando componentes

Nesta aula, continuamos a modelagem do usuário e aprendemos sobre o conceito de autenticação usando o FlaskLogin. Importamos a classe `UserMixin` do FlaskLogin, que já possui métodos prontos para autenticação. Utilizamos herança múltipla para herdar tanto do model quanto do UserMixin, evitando a necessidade de criar esses métodos manualmente. Em seguida, utilizamos o `flash shell` para criar o banco de dados manualmente, utilizando o método `createAll` do DB. Também explicamos a importância da sessão do banco de dados e como usar o método commit para executar os comandos no banco. Por fim, resolvemos problemas de importação circular movendo o SQLAlchemy para um arquivo separado chamado `database.py`.

> [retornar](#roteiro-das-aulas) para o topo da página

### 3. Autenticação e Flask-Login

#### Autenticação com Flask - login - parte 1

Nesta aula, vamos começar a trabalhar com autenticação utilizando a biblioteca Flask Login. Essa biblioteca nos permite gerenciar a sessão do usuário, fornecendo funcionalidades como login, logout e proteção de rotas para usuários autenticados. No entanto, é importante ressaltar que o Flask Login não lida com o registro de usuários, recuperação de contas ou armazenamento seguro de senhas. Para utilizar o Flask Login, precisamos importá-lo, criar uma instância do LoginManager e definir uma rota para realizar o login. Na rota de login, vamos receber os dados do usuário através de uma requisição POST e verificar se as credenciais são válidas. Caso sejam inválidas, retornaremos uma mensagem de erro.

#### Autenticação com Flask - login - parte 2

Nesta aula, vamos utilizar o Postman para testar a autenticação em uma API. Vamos criar uma coleção no Postman chamada "API de autenticação" e adicionar uma nova requisição HTTP para o login. Vamos configurar o ambiente com a base URL e adicionar as variáveis de username e password no corpo da requisição. Em seguida, vamos implementar a lógica de autenticação no código, verificando se o usuário está cadastrado e se a senha está correta. Se tudo estiver correto, retornaremos uma mensagem de autenticação realizada com sucesso. Caso contrário, retornaremos uma mensagem de credenciais inválidas. Na próxima aula, continuaremos a implementação da autenticação na nossa API.

#### Criando usuário e realizando autenticação

Nesta aula, continuamos a construir a rota de login. Após verificar o usuário e a senha, realizamos a autenticação usando o método `login_user` do Flask-Login. Também utilizamos o `current_user` para recuperar informações do usuário autenticado. Para que tudo funcione corretamente, é necessário configurar o `login_manager` com a rota de login e implementar a função `user_loader` para carregar o usuário a partir do ID. Além disso, mostramos como cadastrar um usuário no banco de dados usando o SQLAlchemy. Por fim, explicamos como o cookie de sessão é utilizado para controlar a autenticação. Na próxima aula, abordaremos as views de logout e continuaremos com o CRUD do sistema.

#### Criando Views de Logout e Cadastro de Usuário - parte 1

Nesta aula, continuamos a construção do sistema de autenticação, focando agora na parte do logout. Criamos uma rota chamada `/logout` que permite que o usuário se desautentique do sistema. Utilizamos o método GET para fazer a desautenticação e importamos a função `logout_user` do FlaskLogin para realizar essa ação. Protegemos a rota utilizando o decorator `login_required`, que impede que usuários não autenticados acessem essa rota. Testamos a funcionalidade no Postman e verificamos que o logout foi realizado com sucesso. O logout limpa a sessão do usuário e impede o acesso a rotas protegidas.

#### Criando Views de Logout e Cadastro de Usuário - parte 2

Nesta aula, abordamos a implementação do cadastro de usuários em um sistema de autenticação. Explicamos que existem duas abordagens possíveis: um cadastro interno, onde apenas usuários autenticados podem cadastrar novos usuários, e um cadastro aberto, onde qualquer pessoa pode se registrar com um nível de acesso mais baixo. Optamos por abordar o cadastro aberto. Demonstramos como criar a rota de cadastro de usuário, utilizando o método POST, e como receber as informações do usuário no corpo da requisição.

Em seguida, mostramos como validar e processar essas informações, adicionando o novo usuário ao banco de dados. Também explicamos como retornar respostas adequadas para diferentes cenários, como dados inválidos ou sucesso no cadastro. Utilizamos códigos de status HTTP, como 400 para Bad Request e 200 para OK, para indicar o resultado da requisição.

Por fim, mostramos como proteger rotas específicas com autenticação, utilizando o conceito de Login Required. Demonstrei que, ao tentar acessar uma rota protegida sem estar autenticado, o sistema redireciona automaticamente para a rota de login.

Encerramos a aula com a demonstração de como o cadastro de usuários e a autenticação funcionam em conjunto, permitindo que usuários cadastrados acessem rotas protegidas. Explicamos que é possível proteger qualquer rota do sistema, exceto a rota de login.

#### Rotas de Read e Update do Usuario

Nesta aula, continuamos o desenvolvimento da nossa API. Já construímos as rotas de autenticação, login, logout e cadastro de usuários. Agora vamos criar uma rota para recuperar informações do usuário. Essa rota permitirá que usuários autenticados vejam os detalhes dos usuários cadastrados. Recomendo criptografar senhas para proteger a informação. Em seguida, vamos criar as rotas de atualização e exclusão de usuários. É importante lembrar que a atualização do username pode causar problemas na autenticação, então é recomendado atualizar apenas a senha. Por fim, vamos testar todas as rotas no Postman.

#### Rotas de Delete de Usuário

Nesta aula, aprendemos como excluir um usuário do banco de dados. Utilizamos o método `delete` em vez do `add` para remover o usuário. Em seguida, realizamos o commit para confirmar a exclusão. No entanto, é importante verificar se o usuário que está logado está tentando excluir a si mesmo, pois isso causaria um conflito no sistema de autenticação. Testamos a exclusão e verificamos se funcionou corretamente. Também discutimos a importância de garantir que pelo menos um usuário permaneça no sistema para evitar a perda de acesso completo à API.

> [retornar](#roteiro-das-aulas) para o topo da página

### 4. Finalizando o Projeto

#### Atualizando repositório do Github

Nesta aula, vamos subir nosso código para o GitHub e atualizar nosso repositório. Antes disso, vamos deletar a rota `/hello-world` que não é mais necessária. No terminal, estou dentro da pasta do projeto e entro no repositório do GitHub. Verifico os arquivos alterados, incluindo o app com a implementação do sistema de autenticação e o CRUD de usuários. Também temos a pasta models, onde mapeamos o modelo de usuário, e o arquivo `database.py`, responsável por instanciar o SQL Alchemy. Atualizo tudo com "git add .", faço o commit com uma mensagem explicando as alterações e faço o push para o repositório. Agora, o código está atualizado e disponível para todos que seguem o projeto. Na próxima aula, continuaremos o desenvolvimento.

#### Utilizando o banco de dados MySQL

Nesta aula, continuamos falando sobre bancos de dados. Explicamos que nossa aplicação utiliza o SQLite, que é um banco de dados adequado para desenvolvimento, mas não recomendado para aplicações com muitas requisições simultâneas. Apresentamos o MySQL como uma opção mais completa e amplamente utilizada no mercado. Mostramos como instalar as dependências necessárias e como configurar o MySQL utilizando o Docker. Também demonstramos como conectar a aplicação ao banco de dados e realizar operações como criar tabelas e inserir dados. Por fim, mencionamos a extensão MySQL disponível no Visual Studio para gerenciar o banco de dados.

#### Gerenciamento de Perfil

Nesta aula, introduzimos o conceito de perfis para o gerenciamento do sistema de autenticação. Implementamos o conceito de papel, onde definimos perfis de administrador e usuário. O perfil de usuário permite gerenciar apenas as informações do próprio usuário, enquanto o perfil de administrador pode alterar informações de todos os usuários. Criamos uma coluna chamada `role` no modelo de usuário e adicionamos um valor padrão. Utilizamos essa informação para comparar durante as requisições e permitir ou negar acesso a determinadas ações. Também implementamos verificações para garantir que apenas administradores possam realizar certas operações.

#### Criptografia de senhas

Nesta aula, aprendemos como proteger as senhas dos usuários armazenadas em um banco de dados. Utilizamos a biblioteca Bcrypt do Python para criptografar as senhas. Primeiro, fizemos a instalação da biblioteca através do comando `pip3 install bcrypt`. Em seguida, vimos como utilizar a função `hashpw` para criar um hash criptografado a partir de uma senha. Também aprendemos a utilizar a função checkpw para verificar se uma senha corresponde a um hash armazenado no banco de dados. Implementamos essas funcionalidades em nosso código e testamos o sistema. Agora, as senhas dos usuários estão criptografadas e protegidas contra acesso não autorizado.

#### Finalização

Nesta aula, finalizamos o gerenciamento de perfil e agora vamos atualizar nosso GitHub. Para fazer isso, usamos o comando `git status` para ver os arquivos modificados. Em seguida, adicionamos esses arquivos e fazemos um commit com a mensagem "Implementando User Roles". Depois, fazemos um push para a branch principal e nosso projeto é atualizado. Durante este módulo, aprendemos sobre conexão com banco de dados, diferentes tipos de bancos, rotas de autenticação, CRUD de usuários e gerenciamento de perfil. Espero que você tenha gostado e absorvido conhecimento. Nos vemos nos próximos módulos!

> [retornar](#roteiro-das-aulas) para o topo da página
>
> [voltar](../../README.md) para a página anterior
