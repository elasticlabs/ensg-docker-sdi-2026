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


# URLs à afficher aux stagiaires (après boot)

GeoServer : http://localhost/geoserver/ (via Nginx) ou http://localhost:8082/geoserver/
Jupyter : http://localhost/jupyter/ ou http://localhost:8888/ (token)
pgAdmin : http://localhost:5050/
GeoNetwork : http://localhost:8080/geonetwork/ (si activé)
MinIO : http://localhost:9001/ (si activé)
