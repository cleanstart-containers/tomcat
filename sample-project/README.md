# Tomcat Sample Project

A single-node Tomcat setup using `cleanstart/tomcat:latest-dev`.

**Requirements: Docker and Docker Compose.**

---

## Project Structure

```
tomcat-sample/
├── docker-compose.yml
├── webapps/
│   └── index.html      # Sample app deployed at /sample
└── README.md
```

The `webapps/` folder is mounted into the container at `/usr/local/tomcat/webapps/sample`. Anything placed here is served by Tomcat at `http://localhost:8080/sample`.

---

## Start the Server

```bash
docker compose up -d tomcat
```

Open in browser: **http://localhost:8080/sample**

---

## Common Commands

### Server Management

```bash
# View logs
docker logs tomcat-server

# Follow logs
docker logs -f tomcat-server

# Restart
docker restart tomcat-server

# Stop
docker stop tomcat-server

# Start
docker start tomcat-server

# Remove
docker rm -f tomcat-server
```

### Tomcat Admin

```bash
# Open a shell inside the container
docker exec -it tomcat-server /bin/bash

# Check Tomcat version
docker exec -it tomcat-server /usr/local/tomcat/bin/version.sh

# List deployed webapps
docker exec -it tomcat-server ls /usr/local/tomcat/webapps/

# Tail catalina log
docker exec -it tomcat-server tail -f /usr/local/tomcat/logs/catalina.out

# Check Tomcat process
docker exec -it tomcat-server ps aux | grep tomcat
```

### Deploy a WAR File

To deploy a WAR, copy it into the `webapps/` folder — Tomcat auto-deploys it:

```bash
# Copy a WAR into the mounted webapps folder
cp myapp.war ./webapps/myapp.war
```

It will be available at **http://localhost:8080/sample/myapp** within seconds. No restart needed.

---

## Configuration

Settings are passed as environment variables in `docker-compose.yml`:

| Variable | Default | Description |
|---|---|---|
| `JAVA_OPTS` | `-Xms256m -Xmx512m` | JVM memory settings |
| `CATALINA_OPTS` | `-Dfile.encoding=UTF-8` | Tomcat-specific JVM options |

To change a setting, edit `docker-compose.yml` and restart:

```bash
docker compose up -d tomcat
```