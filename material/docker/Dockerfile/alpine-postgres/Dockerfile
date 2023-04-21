# Instala Alpine com Postgres
FROM postgres:alpine

# Define as variáveis de ambiente
ENV POSTGRES_USER postgres
ENV POSTGRES_PASSWORD postgres
ENV POSTGRES_DB where2go

# Instala dependências e atualiza o sistema
RUN apk update && apk upgrade
RUN apk add --no-cache tzdata

# Adiciona um novo usuário e concede permissões limitadas
RUN echo "CREATE USER admin_w2g WITH PASSWORD 'where2go';" > /docker-entrypoint-initdb.d/init-user.sql
RUN echo "GRANT CONNECT ON DATABASE where2go TO admin_w2g;" >> /docker-entrypoint-initdb.d/init-user.sql
RUN echo "GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO admin_w2g;" >> /docker-entrypoint-initdb.d/init-user.sql

# Cria um diretório padrão
RUN mkdir /app

# Expõe a porta padrão do PostgreSQL
EXPOSE 5432

# Inicializa o PostgreSQL
CMD ["postgres", "-c", "config_file=/etc/postgresql/postgresql.conf"]