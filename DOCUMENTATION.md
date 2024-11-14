# Task Manager API

## 1. Introdução
A Task Manager API permite que os usuários gerenciem suas tarefas, criando, lendo, atualizando e excluindo tarefas em uma aplicação web. A API oferece endpoints para que os usuários possam criar novas tarefas, obter uma lista de tarefas, atualizar o status de uma tarefa e excluir tarefas que não são mais necessárias.

Base URL: https://api.taskmanager.com/v1

## 2. Autenticação
Para interagir com a API, o usuário precisa autenticar-se usando um token de autenticação via Bearer Token.

Authorization: Bearer {seu_token_aqui}

## 3. Requisitos
Método de autenticação: Token Bearer
Formato de resposta: JSON
Versão da API: v1

## 4. Endpoints

### 4.1. Criar uma nova tarefa

URL: /tasks
Método HTTP: POST
Descrição: Cria uma nova tarefa na plataforma.

Parâmetros do corpo da requisição:

{
  "title": "Título da Tarefa",
  "description": "Descrição da tarefa",
  "due_date": "2024-11-20T18:00:00Z"
}

{
  "title": "Finalizar o projeto",
  "description": "Revisar o código e preparar a entrega final do projeto.",
  "due_date": "2024-11-20T18:00:00Z"
}

Resposta (sucesso - 201):

{
  "id": 1,
  "title": "Finalizar o projeto",
  "description": "Revisar o código e preparar a entrega final do projeto.",
  "due_date": "2024-11-20T18:00:00Z",
  "status": "pendente"
}

### 4.2. Obter todas as tarefas

URL: /tasks
Método HTTP: GET
Descrição: Retorna uma lista de todas as tarefas no sistema.

Resposta (sucesso - 200):

[
  {
    "id": 1,
    "title": "Finalizar o projeto",
    "description": "Revisar o código e preparar a entrega final do projeto.",
    "due_date": "2024-11-20T18:00:00Z",
    "status": "pendente"
  },
  {
    "id": 2,
    "title": "Reunião com cliente",
    "description": "Discutir requisitos do novo projeto.",
    "due_date": "2024-11-15T10:00:00Z",
    "status": "completo"
  }
]

### 4.3. Atualizar uma tarefa

URL: /tasks/{id}
Método HTTP: PUT
Descrição: Atualiza os detalhes de uma tarefa existente.

Parâmetros do corpo da requisição:

{
  "title": "Novo título da tarefa",
  "description": "Descrição atualizada da tarefa",
  "due_date": "2024-11-25T18:00:00Z",
  "status": "em andamento"
}

{
  "title": "Finalizar o projeto (revisado)",
  "description": "Revisar o código e realizar o deploy para o ambiente de produção.",
  "due_date": "2024-11-25T18:00:00Z",
  "status": "em andamento"
}

Resposta (sucesso - 200):

{
  "id": 1,
  "title": "Finalizar o projeto (revisado)",
  "description": "Revisar o código e realizar o deploy para o ambiente de produção.",
  "due_date": "2024-11-25T18:00:00Z",
  "status": "em andamento"
}

### 4.4. Excluir uma tarefa

URL: /tasks/{id}
Método HTTP: DELETE
Descrição: Exclui uma tarefa do sistema.

Resposta (sucesso - 204):

{}

## 5. Exemplo de Fluxo de Trabalho

Criar uma nova tarefa:
Enviar um POST para /tasks com os dados da tarefa.
Obter a lista de tarefas:
Enviar um GET para /tasks para ver todas as tarefas.
Atualizar o status de uma tarefa:
Enviar um PUT para /tasks/{id} com os novos dados.
Excluir uma tarefa:
Enviar um DELETE para /tasks/{id} para excluir a tarefa.

## 6. Mensagens de Erro

### 6.1. Tarefa não encontrada
Código de erro: 404
Mensagem:

{
  "error": "Tarefa não encontrada."
}
### 6.2. Faltando parâmetro obrigatório
Código de erro: 400
Mensagem:

{
  "error": "O parâmetro 'title' é obrigatório."
}

## 7. FAQ (Perguntas Frequentes)

### 7.1. Como eu crio uma tarefa sem definir a data de vencimento?
A data de vencimento é um parâmetro opcional. Caso você não a forneça, a tarefa será criada sem uma data de vencimento.

### 7.2. Como posso marcar uma tarefa como 'concluída'?
Para marcar uma tarefa como 'concluída', basta enviar uma solicitação PUT para o endpoint /tasks/{id} e atualizar o status para "status": "completo".

## 8. Conclusão
Essa é a documentação básica para a Task Manager API, que oferece uma maneira simples de gerenciar tarefas. Para obter mais informações sobre como usar a API ou se você tiver dúvidas, entre em contato com nossa equipe de suporte.

## 9. Tecnologias usadas
Backend: Node.js (Express)
Banco de dados: MongoDB
Autenticação: JWT (JSON Web Token)
Formatos de resposta: JSON