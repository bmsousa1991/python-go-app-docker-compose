# Aplicação Python/GO em Docker-Compose

## Descrição

Este projeto implementa uma arquitetura de software composta por três principais componentes: Backend (Go - Reader), Frontend e Backend (Python - Writer). A comunicação entre esses componentes é realizada através de Redis.

## Backend (Go - Reader)

- Porta: 8080
- Descrição: Responsável por ler dados e consultar o Redis usando a chave “SHAREDKEY”.
 - Serviços:
   - /data: Retorna dados para o Frontend.
     

## Frontend

- Porta: 5000
- Descrição: Interface do usuário que envia dados para o serviço /write e recebe dados do serviço /data.
 - Serviços:
   - /write: Envia dados para o Backend (Python - Writer).
   - /data: Recebe dados do Backend (Go - Reader).
  
## Backend (Python - Writer)

- Porta: 8081
- Descrição: Responsável por escrever dados recebidos do Frontend no Redis.
 - Serviços:
   - /write: Recebe dados do Frontend e os coloca no Redis usando a chave “SHAREDKEY”.


## Fluxo de Dados

1. O Frontend envia dados para o serviço /write do Backend (Python - Writer).
2. O Backend (Python - Writer) coloca os dados no Redis.
3. O Backend (Go - Reader) consulta o Redis usando a chave “SHAREDKEY” e retorna os dados para o Frontend através do serviço /data.

##Contribuição

Sinta-se à vontade para contribuir com este projeto. Faça um fork, crie uma branch, adicione suas alterações e envie um pull request.
