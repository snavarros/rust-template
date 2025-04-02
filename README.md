



# 😺 GITHUB ACTIONS

Se ha creado github action, en donde cada pull o push en [MAIN], le da formato al codigo, se analiza con clippy y se realizan los test respectivos.

# 🐳 DOCKER 

Se han creado 3 entornos ["dev", "test", "prod"], 

## 🆙 Montar Servicios

docker-compose -f docker-compose.dev.yml up -d
docker-compose -f docker-compose.prod.yml up -d
docker-compose -f docker-compose.test.yml up -d


## Reconstruir la imagen y reiniciar los contenedores

docker-compose -f docker-compose.dev.yml up --build

docker-compose -f docker-compose.prod.yml build --no-cache


# 🤖 CHATGPT 

https://chatgpt.com/share/67ed1c56-1a5c-8013-ba03-338398a0f0a8