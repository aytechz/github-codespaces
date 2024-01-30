Create a repo in Github Codespaces.
Install requirements
Run Docker containers
  pgAdmin
  postgress
Install Jupyter notebooks
>>> pip install jupyter

Install Terraform for Linux:
Check https://developer.hashicorp.com/terraform/install for installation.

`docker network create pg-network`
`docker volume create --name dtc_postgres_volume_local -d local`

Run Postgres (change the path)

```bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v dtc_postgres_volume_local:/var/lib/postgresql/data \
  -p 5432:5432 \
  --network=pg-network \
  --name pg-database \
  postgres:13
```

Run pgAdmin

```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -p 8080:80 \
  --network=pg-network \
  --name pgadmin-2 \
  dpage/pgadmin4
```
