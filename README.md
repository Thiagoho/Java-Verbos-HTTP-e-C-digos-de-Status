# Desafio Java — Verbos HTTP e Status Codes

## Objetivo
Este projeto foi desenvolvido como parte do desafio para praticar APIs REST, verbos HTTP, tratamento correto de status codes e estruturação de respostas de erro no padrão JSON.<br>
Objetivo principal é demonstrar, na prática, como funciona a comunicação cliente-servidor usando boas práticas definidas na RFC 9110 (HTTP Semantics).

## Entender o uso correto dos verbos HTTP:
GET, POST, PUT, PATCH e DELETE<br>
Aprender a retornar status codes adequados em cada situação:<br>
200, 201, 204, 400, 404, 409, 500<br>
Criar endpoints REST bem definidos<br>
Implementar tratamento global de erros<br>
Enviar erros padronizados em formato JSON<br>
Criar um pequeno frontend em HTML + JS que consome a API e mostra mensagens de erro na tela

## Recurso Utilizado na API
O recurso escolhido foi Produto, contendo:<br>
id — identificador único<br>
nome — nome do produto<br>
preco — preço atual<br>
estoque — quantidade disponível

## Arquitetura do Projeto
src/main/java/com/desafiohttp/<br>
 ├── controller/        → Endpoints da API<br>
 ├── service/           → Regras de negócio<br>
 ├── repository/        → Acesso ao banco de dados<br>
 ├── model/             → Entidades (Produto)<br>
 ├── exception/         → Erros personalizados e handler<br>
 └── DesafioHttpApplication.java

## Tecnologias
Java 17<br>
Spring Boot<br>
Spring Web<br>
Spring Data JPA<br>
H2 Database<br>
Lombok<br>
Swagger<br>

## Endpoints e Funcionamento
GET /produtos — Listar todos<br>
Retorna todos os produtos cadastrados.<br>
Status:<br>
200 OK
## GET /produtos/{id} — Buscar por ID<br>
Status:<br>
200 OK → quando o produto existe<br>
404 Not Found → quando não existe
## POST /produtos — Criar novo produto<br>
Envia nome, preço e estoque.<br>
Status possíveis:<br>
201 Created → criado com sucesso<br>
00 Bad Request → dados inválidos<br>
409 Conflict → nome já existente<br>
## PATCH /produtos/{id} — Atualização parcial<br>
Permite alterar apenas um campo específico.<br>
Status:<br>
200 OK<br>
400 Bad Request → JSON inválido<br>
404 Not Found
## DELETE /produtos/{id} — Remover produto<br>
Status:<br>
204 No Content → removido<br>
404 Not Found → ID não encontrado<br>
## Tratamento Global de Erros<br>
O projeto utiliza @ControllerAdvice para interceptar erros da aplicação.<br>
Todos os erros seguem um padrão JSON, contendo:<br>
código HTTP<br>
mensagem<br>
timestamp
##	Frontend (HTML + JavaScript)
O projeto inclui uma página simples que consome a API usando fetch().<br>
Essa tela exibe:<br>
 Mensagens de sucesso<br>
Mensagens de erro vindas da API<br>
Respostas 400, 404, 409 formatadas na interface<br>
Exemplos de mensagens exibidas:<br>
"Erro 404: Produto não encontrado"<br>
"Erro 409: Já existe um produto com esse nome"<br>
"Erro 400: Dados inválidos"<br>
"Produto criado com sucesso!"
##	Decisões Técnicas
Separação clara entre camadas (controller, service, repository).<br>
Uso de exceptions personalizadas para:<br>
recurso não encontrado<br>
conflito de dados<br>
Padrão de tratamento de erros centralizado<br>
HTML + JS puro para exibir mensagens da API<br>
Código limpo e comentado, seguindo boas práticas REST

##	Resultado Final<br>
Este projeto demonstra:<br>
Como funciona cada verbo HTTP<br>
Como retornar o status correto<br>
Como padronizar respostas de erro<br>
Como separar bem a arquitetura<br>
Como exibir mensagens no frontend<br>
Como construir uma API Java simples, limpa e profissional<br>
