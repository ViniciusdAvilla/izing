# INSTALAR DOCKER E NODE

# NODE
- Download do node WINDOWS         - https://nodejs.org/download/release/v14.21.3/node-v14.21.3-x64.msi
- Download do node para MAC        - https://nodejs.org/download/release/v14.21.3/node-v14.21.3.pkg
- Download do node demais sistemas - https://nodejs.org/download/release/v14.21.3/

# DOCKER
Download do Docker Desktop         - https://www.docker.com/products/docker-desktop/

# SUBIR O BANCO
docker run --name postgresql-local -e POSTGRES_USER=izing -e POSTGRES_PASSWORD=password -p 5432:5432 -v /data:/var/lib/postgresql/datalocalizing --restart=always -d postgres

docker run -e TZ="America/Sao_Paulo" --name redis-izing-local -p 6379:6379 -d --restart=always redis:latest redis-server --appendonly yes --requirepass "password"

docker run -d --name rabbitmq-local -p 5672:5672 -p 15672:15672 --restart=always --hostname rabbitmq -v /data:/var/lib/rabbitmq rabbitmq:3-management-alpine

# BACKEND
npm install --force
npx sequelize db:migrate
npx sequelize db:seed:all
npm start

# FRONTEND
npm install --force
export NODE_OPTIONS=--openssl-legacy-provider
npx quasar build -P -m pwa
npx quasar dev