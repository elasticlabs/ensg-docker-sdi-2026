# Copier la conf
cp compose/.env.example compose/.env

# Démarrer le coeur
docker compose --env-file compose/.env -f compose/docker-compose.yml --profile core up -d

# + Catalogage
docker compose --env-file compose/.env -f compose/docker-compose.yml --profile core --profile catalog up -d

# + Extras
docker compose --env-file compose/.env -f compose/docker-compose.yml --profile core --profile extras up -d

# Logs
docker compose -f compose/docker-compose.yml logs -f --tail=200

# Stop / reset total
docker compose -f compose/docker-compose.yml down -v
