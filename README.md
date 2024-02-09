# bix-api-gateway

Este repositório contém as configurações e recursos relacionados ao Kong, com o Konga sendo utilizado como interface de gerenciamento.

## Descrição

O Kong é um API Gateway escalável e de código aberto, projetado para gerenciar o tráfego de API de forma eficiente e segura. 
O Konga é uma interface de gerenciamento para o Kong, que simplifica a configuração e o gerenciamento do Kong.

## Funcionamento

O API gateway irá agrupar todos os microsserviços, fazer autenticação, roteamento, e poderá, futuramente lidar com algumas políticas e mecanismos adicionais, como retentativas, circuit breaker e ACL.
O lado do cliente *jamais* saberá o que acontece por trás do endpoint, e não fará ideia de quantos microsserviços tem.

## Requisitos

- Docker

## Execução

Para subir os containers do docker-compose, você deverá utilizar o seguinte comando:
```bash 
docker-compose up -d
```
#### Kong

No diretório `/docker-kong`, você deverá subir os containers do arquivo `docker-compose.yml` para iniciar o Kong e todos os serviços associados. 



#### Microsserviços
Suba os containers do arquivo do docker no diretório raiz utilizando o comando indicado acima.

## Contribuição e Integração com os microsserviços

#### Sugestão A: 

Buildar e fornecer a imagem através do Docker Hub e incluir no docker-compose.yml do diretório raiz.

##### Prós: 
Fica mais fácil de dar manutenção e configurar, pois não exige que os serviços fiquem no mesmo diretório (uma pasta /services?)

##### Contras: 
Trabalho extra para buildar e publicar a imagem; Talvez precise entender um pouco de Dockerfile.

#### Sugestão B:

Colocar os serviços em um subdiretório (/services?) e criar um volume no docker-compose.

##### Prós: 
Não exige experiência com docker.

##### Contras: 
Eventualmente será necessário atualizar todos os repositórios manualmente. Além disso, é necessário que a estrutura de pastas seja mantida para que o volume funcione.

## Observações

Os subdiretórios deste repositório foram criados apenas para exemplificar um cenário. Caso os projetos sejam clonados nos diretórios, adicioná-los no .gitignore antes.