
- Python 3.9 or higher
- Docker  

### Local setup

After cloning the repo:

1. Setup env

```bash
# Python virtual env
python3 -m venv venv (Linux)
pytho -m venv venv (Windows)
source venv/bin/activate
```

```bash
# Env variables
# Copy example file, change values if needed
cp .env.example .env (Linux)
copy .env.example .env  (Windows)
```

2. Build and run the docker container
```
docker-compose build
docker-compose up -d
```

3. Prepare the database 

run `docker ps` and get the CONTAINER ID of the postgres:image
copy the container id of the pg container `e180ffc7d5d6`

```
CONTAINER ID   IMAGE                COMMAND                  CREATED       STATUS       PORTS                    NAMES
9432a9884aad   sheepfish_vpn   "python app/manage.p…"   7 hours ago   Up 7 hours   0.0.0.0:8000->8000/tcp   sheepfish_vpn-web-1
e180ffc7d5d6   postgres:latest      "docker-entrypoint.s…"   7 hours ago   Up 7 hours   0.0.0.0:5432->5432/tcp   sheepfish_vpn-db-1
```

Then run this command to write db_sheepfish_vpn_backup.sql onto sheepfish_vpn db

```
cat db_sheepfish_vpn_backup.sql | docker exec -i CONTAINER ID psql --user admin sheepfish_vpn
```
4. Check if the installation succeeds by opening the [http://localhost:8000/vpnsite]()
```
please coordinate the vpn host at urls.py with host changes changes
```
user credentials: username=User, password=userpassword
admin credentials: username=Admin, password=adminpassword

