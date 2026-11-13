# Node-RED API

API REST em Spring Boot para receber e consultar dados de sensores. O projeto usa PostgreSQL para persistência e pode servir como back-end de um fluxo Node-RED ou de uma aplicação de monitoramento.

## Tecnologias

- Java 17
- Spring Boot 3.4
- Spring Web
- Spring Data JPA
- PostgreSQL
- Maven Wrapper
- Docker

## Configuração

A aplicação lê a conexão com o banco pela variável `DATABASE_URL`. Use uma URL JDBC:

```bash
export DATABASE_URL='jdbc:postgresql://localhost:5432/nodered'
```

A porta pode ser alterada com `PORT`; o padrão é `8080`.

## Como executar

```bash
./mvnw spring-boot:run
```

No Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

## Endpoints

Base: `http://localhost:8080/api/dados`

| Método | Rota | Ação |
| --- | --- | --- |
| `POST` | `/api/dados` | Salva um dado recebido |
| `GET` | `/api/dados` | Lista todos os dados |

Exemplo:

```bash
curl -X POST http://localhost:8080/api/dados \
  -H "Content-Type: application/json" \
  -d '{"sensor":"temperatura","valor":25.4}'
```

Consulte `src/main/java/com/sensor/nodered_api/model/Dado.java` para conferir os campos aceitos pelo modelo.
