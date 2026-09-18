# Movieflix

API REST desenvolvida como parte do desafio **Movieflix**, proposto no curso [Java Spring Expert](https://devsuperior.club/courses/6) da [DevSuperior](https://devsuperior.com.br), no módulo *Casos de uso, signup, finalização*.

O projeto simula uma plataforma de streaming de filmes, permitindo que visitantes e membros listem filmes e gêneros, e que membros publiquem avaliações sobre os filmes assistidos.

## 🎯 Objetivo do desafio

Implementar as funcionalidades necessárias para atender aos seguintes casos de uso:

- **Listar filmes**: listagem paginada de filmes (ordenada alfabeticamente por título), com filtro opcional por gênero, além da listagem de todos os gêneros disponíveis.
- **Visualizar detalhes do filme**: exibição dos dados completos de um filme específico.
- **Avaliar filme**: usuários com perfil MEMBER podem publicar uma avaliação de texto para um filme.

## 🛠️ Tecnologias utilizadas

- Java 25
- Spring Boot
- Spring Security + OAuth2 Authorization Server (grant type `password` customizado)
- Spring Data JPA / Hibernate
- Bean Validation
- H2 Database (ambiente de testes)
- JUnit 5 + MockMvc (testes de integração)
- Maven

## 🔐 Controle de acesso

A API possui dois perfis de usuário:

| Perfil    | Permissões                                  |
|-----------|----------------------------------------------|
| VISITOR   | Listar gêneros, listar filmes, ver detalhes  |
| MEMBER    | Todas as permissões de VISITOR + publicar avaliações |

A autenticação é feita via OAuth2 (grant type `password`), retornando um token JWT que deve ser enviado no header `Authorization: Bearer {token}` em todas as requisições.

## 📌 Endpoints

| Método | Endpoint              | Acesso           | Descrição                                      |
|--------|------------------------|------------------|-------------------------------------------------|
| GET    | `/genres`              | VISITOR, MEMBER  | Lista todos os gêneros                          |
| GET    | `/movies`              | VISITOR, MEMBER  | Lista paginada de filmes, ordenada por título    |
| GET    | `/movies?genreId={id}` | VISITOR, MEMBER  | Lista paginada de filmes filtrada por gênero     |
| GET    | `/movies/{id}`         | VISITOR, MEMBER  | Detalhes de um filme específico                 |
| POST   | `/reviews`             | MEMBER           | Publica uma avaliação para um filme             |

## ✅ Testes

O projeto conta com testes de integração cobrindo os principais cenários de cada caso de uso: autenticação, autorização por perfil, validação de dados e regras de negócio.

## 👤 Autor

Desenvolvido por **Breno Oliveira de Souza** durante os estudos do curso Java Spring Expert da DevSuperior.
