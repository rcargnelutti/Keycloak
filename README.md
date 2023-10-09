# Keycloak

Keycloak é uma solução de gerenciamento de acesso e identidade de código aberto que fornece serviços robustos de autenticação e autorização.

## Dockerfile

Dockerfile personalizado que forneçe uma configuração personalizada e perfeita para o Keycloak.
Este Dockerfile constrói uma imagem Keycloak baseada na imagem “quay.io/keycloak/keycloak”. Ele configura o banco de dados Postgres, especifica os recursos desejados do Keycloak e executa o comando “kc.sh build” necessário para garantir uma configuração adequada do Keycloak.

## Keycloak e Postgre com Docker compose

1. Clonar o repositório  
```git clone https://github.com/rcargnelutti/Keycloak.git```

2. Compilar imagem (Dockerfile)  
```docker compose build --no-cache keycloak```  

3. Executar as imagens (docker-compose.yml)  
```docker compose up -d```

4. Listar os containers em execução    
```docker compose ps```

5. Checar os logs do container keycloak  
```docker compose logs -f keycloak```

6. Acessar endeeço no navegador web  
```http://localhost:8180/```

7. Desabilitar SSl  
Acessar o container  
```docker exec -it [id ou nome do container] bash```  
Entrar no diretório  
```cd /opt/keycloak-22.0.3/bin```  
Executar comandos  
```./kcadm.sh config credentials --server http://localhost:8080 --realm master --user admin```  
```./kcadm.sh update realms/master -s sslRequired=NONE```  

Esta solução garante um ambiente Keycloak atualizado e fornece instruções claras para integração do Keycloak com Postgres ou outros bancos de dados.

Com essas etapas, os usuários podem implantar e gerenciar com êxito o Keycloak no Docker, aproveitando seus poderosos recursos de gerenciamento de identidade e acesso.

## Referência
[Run Keycloak locally with Docker compose](https://medium.com/@ozbillwang/run-keycloak-locally-with-docker-compose-db9a9f2fb437)
