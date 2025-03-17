# API de Usuário com Node.js e MySQL

Este repositório contém um projeto de API REST para gerenciamento completo de usuários, desenvolvido com Node.js e MySQL. A API permite criar, listar, atualizar e deletar usuários armazenados em um banco de dados.

## Requisitos
Certifique-se de ter instalado em sua máquina:
- [Node.js](https://nodejs.org/)
- [MySQL](https://www.mysql.com/)

## Configuração do Ambiente
1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```
2. Instale as dependências:
   ```bash
   npm install
   ```
3. Configure as variáveis de ambiente:
   Crie um arquivo `.env` na raiz do projeto e adicione as seguintes configurações:
   ```env
   DB_HOST=localhost
   DB_USER=root
   DB_PASSWORD=sua_senha
   DB_NAME=usersdb
   PORT=3000
   ```
   Substitua `sua_senha` pela senha do seu MySQL.

## Inicialização do Banco de Dados
O projeto automaticamente criará o banco de dados e a tabela necessária na primeira execução.

## Executando a API
Para iniciar o servidor, execute:
```bash
node index.js
```

O servidor rodará na porta definida no `.env` (padrão: 3000).

## Rotas da API

### Criar usuário
- **POST** `/users`
- **Corpo da requisição (JSON):**
  ```json
  {
    "name": "Nome do Usuário",
    "email": "email@example.com"
  }
  ```
- **Resposta de Sucesso:**
  ```json
  {
    "message": "Usuário criado com sucesso",
    "id": 1
  }
  ```

### Listar todos os usuários
- **GET** `/users`
- **Resposta de Sucesso:**
  ```json
  [
    {
      "id": 1,
      "name": "Nome do Usuário",
      "email": "email@example.com"
    }
  ]
  ```

### Atualizar usuário
- **PUT** `/users/:id`
- **Corpo da requisição (JSON):**
  ```json
  {
    "name": "Novo Nome",
    "email": "novoemail@example.com"
  }
  ```
- **Resposta de Sucesso:**
  ```json
  {
    "message": "Usuário atualizado com sucesso"
  }
  ```
- **Erro (Usuário não encontrado):**
  ```json
  {
    "message": "Usuário não encontrado"
  }
  ```

### Deletar usuário
- **DELETE** `/users/:id`
- **Resposta de Sucesso:**
  ```json
  {
    "message": "Usuário deletado com sucesso"
  }
  ```
- **Erro (Usuário não encontrado):**
  ```json
  {
    "message": "Usuário não encontrado"
  }
  ```

## Uso com Docker
Para executar o MySQL em um contêiner Docker:
```bash
docker run -d -p 3306:3306 --name meu-mysql -e MYSQL_ROOT_PASSWORD=sua_senha mysql:latest
```
Acesse o MySQL dentro do contêiner com:
```bash
docker exec -it meu-mysql mysql -u root -p
```

## Testando a API
Utilize ferramentas como [Postman](https://www.postman.com/) ou [Insomnia](https://insomnia.rest/) para testar todas as operações CRUD:
1. **Criar Usuário:** POST para `/users` com corpo JSON.
2. **Listar Usuários:** GET para `/users`.
3. **Atualizar Usuário:** PUT para `/users/1` (substitua 1 pelo ID desejado).
4. **Deletar Usuário:** DELETE para `/users/1` (substitua 1 pelo ID desejado).
