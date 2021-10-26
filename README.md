![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![](https://socialify.git.ci/rafaelgeronimo/trybe-project-cookmaster/image?description=1&descriptionEditable=%5BTrybe%20Project%5D%20Cookmaster&font=Bitter&language=1&owner=1&pattern=Brick%20Wall&theme=Light)

## 📗 Sobre

Projeto desenvolvido no módulo de Desenvolvimento Back-end da Trybe, no bloco de Autenticação e Upload de Arquivos, onde estudamos JWT (Json Web Token), Upload de arquivos com `multer` e testamos APIs com Testes de Integração.

Foi desenvolvido um app utilizando a arquitetura **MSC**, onde é possível fazer o cadastro e login de pessoas usuárias, onde apenas essas pessoas poderão acessar, modificar e deletar as receitas que foram cadastradas.

# Habilidades desenvolvidas

Com o desenvolvimento deste projeto, foram colocadas em prática as seguintes habilidades:

- Entender o que há por dentro de um token de autenticação;
- Gerar tokens a partir de informações como login e senha;
- Autenticar rotas do Express, usando o token JWT;
- Fazer upload de arquivos em APIs REST;
- Salvar arquivos no servidor através de uma API REST;
- Consultar arquivos do servidor através de uma api REST.
- Realizar testes de integração

## 🚀 Demo
API URL: https://rafaelgeronimo-cookmaster.herokuapp.com/

Utilize o Insomnia, Postman ou outro de sua preferência para realizar as requisições na rotas pelos métodos disponíveis.

Métodos e rotas:

|Método|Rota|Descrição|
|---|---|---|
|`POST`|`/users`|Endpoint para cadastro de usuários|
|`POST`|`/login`|Endpoint para login de usuário cadastrado|
|`POST`|`/recipes`|Realiza o cadastro de uma nova receita|
|`GET`|`/recipes`|Retorna todas as receitas cadastradas|
|`GET`|`/recipes/:id`|Retorna dados de receita específica pelo seu ID|
|`PUT`|`recipes/:id`|Permite editar uma receita já cadastrada|
|`DELETE`|`recipes/:id`|Endpoint para excluir receita específica pelo seu ID|
|`PUT`|`recipes/:id/image`|Endpoint para adicionar uma imagem a uma receita|
|`GET`|`recipes/:id/*.jpeg`|Permite acessar a imagem de uma receita|

## 🛠 Instalação
- Realize o clone do projeto com o comando:
```sh
git clone git@github.com:rafaelgeronimo/trybe-project-cookmaster.git
```
- Instale o projeto com `npm` ou `yarn`:
```sh
cd trybe-project-cookmaster

## npm
npm install

## yarn
yarn install
```
- Configure as variáveis de ambiente:
  - Para que essa api funcione corretamente no seu ambiente local, será necessário criar o arquivo `.env` na raíz do projeto, contendo os dados de acesso ao banco de dados `MongoDB`.
  - Também é possível escolher a porta em que a aplicação irá rodar. Se não for configurada, o padrão será a porta 3000.
```
MONGO_DB_URL=mongodb://localhost:27017/Cookmaster
PORT=3000
```
- Após a instalação das dependências e configuração das variáveis de ambiente, é possível executar com o comando para iniciar a API:
```sh
## npm
npm start

## yarn
yarn start
```

### Requisitos do projeto
#### Requisitos obrigatórios
<details>
  <summary>
    1 - Crie um endpoint para o cadastro de usuários
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/users</kbd>).
    </li>
    <li>
      No banco um usuário precisa ter os campos Email, Senha, Nome e Role.
    </li>
    <li>
      Para criar um usuário através da API, todos os campos são obrigatórios, com exceção do Role.
    </li>
    <li>
      O campo Email deve ser único.
    </li>
    <li>
      Usuários criados através desse endpoint devem ter seu campo Role com o atributo _user_, ou seja, devem ser usuários comuns, e não admins.
    </li>
    <li>
      O body da requisição deve conter o seguinte formato:
      <pre>
        {
          "name": "string",
          "email": "string",
          "password": "string"
        }
      </pre>
    </li>
    <li>
      Não use <kbd>bcrypt</kbd> ou outra biblioteca para encriptar a senha, para que o avaliador funcione corretamente.
    </li>
  </ul>
</details>
<details>
  <summary>
    2 - Crie um endpoint para o login de usuários
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/login</kbd>).
    </li>
    <li>
      A rota deve receber os campos Email e Senha e esses campos devem ser validados no banco de dados.
    </li>
    <li>
      Na configuração do <kbd>JWT</kbd> **não use variáveis de ambientes** para não ter conflito com o avaliador.
    </li>
    <li>
      Um token <kbd>JWT</kbd> deve ser gerado e retornado caso haja sucesso no login. No seu payload deve estar presente o id, email e role do usuário.
    </li>
    <li>
      O body da requisição deve conter o seguinte formato:
      <pre>
        {
          "email": "string",
          "password": "string"
        }
      </pre>
    </li>
  </ul>
</details>
<details>
  <summary>
    3 - Crie um endpoint para o cadastro de receitas
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes</kbd>).
    </li>
    <li>
      A receita só pode ser criada caso o usuário esteja logado e o token <kbd>JWT</kbd> validado.
    </li>
    <li>
      No banco, a receita deve ter os campos Nome, Ingredientes, Modo de preparo, URL da imagem e Id do Autor.
    </li>
    <li>
      Nome, ingredientes e modo de preparo devem ser recebidos no corpo da requisição, com o seguinte formato:
      <pre>
        {
          "name": "string",
          "ingredients": "string",
          "preparation": "string"
        }
      </pre>
    </li>
    <li>
      O campo dos ingredientes pode ser um campo de texto aberto.
    </li>
    <li>
      O campo ID do autor, deve ser preenchido automaticamente com o ID do usuário logado, que deve ser extraído do token JWT.
    </li>
    <li>
      A URL da imagem será preenchida através de outro endpoint
    </li>
  </ul>
</details>
<details>
  <summary>
    4 - Crie um endpoint para a listagem de receitas
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes</kbd>).
    </li>
    <li>
      A rota pode ser acessada por usuários logados ou não
    </li>
  </ul>
</details>
<details>
  <summary>
    5 - Crie um endpoint para visualizar uma receita específica
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes/:id</kbd>).
    </li>
    <li>
      A rota pode ser acessada por usuários logados ou não
    </li>
  </ul>
</details>
<details>
  <summary>
    6 - Crie uma query em mongo que insira uma pessoa usuária com permissões de admin
  </summary>
  <ul>
    <li>
      Crie um arquivo <kbd>seed.js</kbd> na raiz do projeto com uma query do Mongo DB capaz de inserir um usuário na coleção _users_ com os seguintes valores:
      <pre>
        <kbd>{ name: 'admin', email: 'root@email.com', password: 'admin', role: 'admin' }</kbd>
      </pre>
      <strong>Obs.:</strong> Esse usuário tem o poder de criar, deletar, atualizar ou remover qualquer receita, independente de quem a cadastrou. Isso será solicitado ao longo dos próximos requisitos.
    </li>
  </ul>
</details>
<details>
  <summary>
    7 - Crie um endpoint para a edição de uma receita
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes/:id</kbd>).
    </li>
    <li>
      A receita só pode ser atualizada caso o usuário esteja logado e o token <kbd>JWT</kbd> validado.
    </li>
    <li>
      A receita só pode ser atualizada caso pertença ao usuário logado, ou caso esse usuário seja um admin.
    </li>
    <li>
      O corpo da requisição deve receber o seguinte formato:
      <pre>
        {
          "name": "string",
          "ingredients": "string",
          "preparation": "string"
        }
      </pre>
    </li>
  </ul>
</details>
<details>
  <summary>
    8 - Crie um endpoint para a exclusão de uma receita
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes/:id</kbd>).
    </li>
    <li>
      A receita só pode ser excluída caso o usuário esteja logado e o token <kbd>JWT</kbd> validado.
    </li>
    <li>
      A receita só pode ser excluída caso pertença ao usuário logado, ou caso o usuário logado seja um admin.
    </li>
  </ul>
</details>
<details>
  <summary>
    9 - Crie um endpoint para a adição de uma imagem a uma receita
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/recipes/:id/image/</kbd>).
    </li>
    <li>
      A imagem deve ser lida do campo <kbd>image</kbd>.
    </li>
    <li>
      O endpoint deve aceitar requisições no formato <kbd>multipart/form-data</kbd>.
    </li>
    <li>
      A receita só pode ser atualizada caso o usuário esteja logado e o token <kbd>JWT</kbd> validado.
    </li>
    <li>
      A receita só pode ser atualizada caso pertença ao usuário logado ou caso o usuário logado seja admin.
    </li>
    <li>
      O upload da imagem deverá ser feito utilizando o <kbd>Multer</kbd>.
    </li>
    <li>
      O nome do arquivo deve ser o ID da receita, e sua extensão <kbd>.jpeg</kbd>.
    </li>
    <li>
      A URL completa para acessar a imagem através da API deve ser gravada no banco de dados, junto com os dados da receita.
    </li>
  </ul>
</details>
<details>
  <summary>
    10 - Crie um endpoint para acessar a imagem de uma receita
  </summary>
  <ul>
    <li>
      As imagens devem estar disponíveis através da rota <kbd>/images/<id-da-receita>.jpeg</kbd> na API.
    </li>
  </ul>
</details>
<details>
  <summary>
    11 - Crie testes de integração que cubram no mínimo 30% dos arquivos em <kbd>src</kbd>, com um mínimo de 50 linhas cobertas
  </summary>
  <ul>
    <li>
      Os testes de integração devem ser criados na pasta <kbd>./src/integration-tests</kbd>, essa pasta **não pode ser renomeada ou removida**;
    </li>
    <li>
      O arquivo <kbd>change.me.test.js</kbd> pode ser alterado, renomeado ou removido;
    </li>
    <li>
      Os testes devem ser criados usando o instrumental e boas práticas apresentado nos conteúdos de testes do course;
    </li>
    <li>
      Para rodar os testes, utilize o comando <kbd>npm run dev:test</kbd>;
    </li>
    <li>
      Para visualizar a cobertura, utilize o comando <kbd>npm run dev:test:coverage</kbd>;
    </li>
  </ul>
</details>

#### Requisitos bônus
<details>
  <summary>
    12 - Crie um endpoint para cadastro de pessoas administradoras
  </summary>
  <ul>
    <li>
      A rota deve ser (<kbd>/users/admin</kbd>).
    </li>
    <li>
      Só será possível adicionar um admin caso esta ação esteja sendo feita por outro admin, portanto, deve ser validado se há um admin logado.
    </li>
    <li>
      Por padrão, as requisições pra esse endpoint devem adicionar um usuário com a role _admin_.
    </li>
    <li>
      O corpo da requisição deve ter o seguinte formato:
      <pre>
        {
          "name": "string",
          "email": "string",
          "password": "string"
        }
      </pre>
    </li>
  </ul>
</details>
<details>
  <summary>
    13 - Crie testes de integração que cubram no mínimo 60% dos arquivos em <kbd>src</kbd>, com um mínimo de 100 linhas cobertas
  </summary>
  <ul>
    <li>
      Os testes de integração devem ser criados na pasta <kbd>./src/integration-tests</kbd>, essa pasta **não pode ser renomeada ou removida**;
    </li>
    <li>
      O arquivo <kbd>change.me.test.js</kbd> pode ser alterado, renomeado ou removido;
    </li>
    <li>
      Os testes devem ser criados usando o instrumental e boas práticas apresentado nos conteúdos de testes do course;
    </li>
    <li>
      Para rodar os testes, utilize o comando <kbd>npm run dev:test</kbd>;
    </li>
    <li>
      Para visualizar a cobertura, utilize o comando <kbd>npm run dev:test:coverage</kbd>;
    </li>
  </ul>
</details>
<details>
  <summary>
    14 - Crie testes de integração que cubram no mínimo 90% dos arquivos em <kbd>src</kbd>, com um mínimo de 150 linhas cobertas
  </summary>
  <ul>
    <li>
      Os testes de integração devem ser criados na pasta <kbd>./src/integration-tests</kbd>, essa pasta **não pode ser renomeada ou removida**;
    </li>
    <li>
      O arquivo <kbd>change.me.test.js</kbd> pode ser alterado, renomeado ou removido;
    </li>
    <li>
      Os testes devem ser criados usando o instrumental e boas práticas apresentado nos conteúdos de testes do course;
    </li>
    <li>
      Para rodar os testes, utilize o comando <kbd>npm run dev:test</kbd>;
    </li>
    <li>
      Para visualizar a cobertura, utilize o comando <kbd>npm run dev:test:coverage</kbd>;
    </li>
  </ul>
</details>
