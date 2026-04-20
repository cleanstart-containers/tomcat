## Container Documentation for Tomcat Documentation

The CleanStart Tomcat image provides a production-ready, security-hardened container optimized for enterprise environments. Built on a minimal base OS with comprehensive security hardening, this image delivers reliable application execution with advanced security features.

📌 **Base Foundation**: Security-hardened, minimal base OS designed for enterprise containerized environments.

**Image Path**: `ghcr.io/cleanstart-containers/tomcat`

**Registry**: `cleanstart Registry`

## Key Features
Core capabilities and strengths of this container

- Production-ready container deployment
- Enterprise-grade security hardening
- Comprehensive monitoring and logging
- Multi-architecture support

## Common Use Cases
Typical scenarios where this container excels

- Production application deployment
- Microservices architecture implementation
- Development and testing environments
- Enterprise workload containerization

## Pull Latest Image
Download the container image from the registry

```bash
docker pull ghcr.io/cleanstart-containers/tomcat:latest
```
```bash
docker pull ghcr.io/cleanstart-containers/tomcat:latest-dev
```


## Basic Run
Run the container with basic configuration

```bash
docker run -it --name tomcat ghcr.io/cleanstart-containers/tomcat:latest
```

## Production Deployment
Deploy with production security settings

```bash
docker run -d --name tomcat-prod \
  --security-opt=no-new-privileges \
  --restart unless-stopped \
  ghcr.io/cleanstart-containers/tomcat:latest
```

Volume Mount Mount local directory for persistent data

```bash
docker run -v /app:/app ghcr.io/cleanstart-containers/tomcat:latest
```

Port Forwarding Run with custom port mappings

```bash
docker run -p 8080:8080 ghcr.io/cleanstart-containers/tomcat:latest
```

## Environment Variables
Configuration options available through environment variables

| Variable | Default | Description |
|----------|---------|-------------|
| PATH | /usr/local/sbin:/... | System PATH configuration |

## Security Best Practices
Recommended security configurations and practices

- Use specific image tags for production (avoid latest)
- Configure resource limits: memory and CPU constraints
- Enable read-only root filesystem when possible
- Run containers with non-root user (--user 1000:1000)
- Use --security-opt=no-new-privileges flag
- Regularly update container images for security patches
- Implement proper network segmentation
- Monitor container metrics for anomalies

## Kubernetes Security Context
Recommended security context for Kubernetes deployments

```yaml
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  runAsGroup: 1000
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
  capabilities:
    drop:
      - ALL
```

## Documentation Resources
Essential links and resources for further information
 
**CleanStart Images**: https://images.cleanstart.com/
 
**Community Images**:
**Docker Hub**: https://hub.docker.com/u/cleanstart<br>
**GitHub**: https://github.com/cleanstart-containers<br>
**AWS ECR Public Gallery**: https://gallery.ecr.aws/cleanstart/
 
**Presence on Social Media**:
**Community**: https://www.linkedin.com/groups/18324021/<br>
**YouTube**: https://www.youtube.com/@CleanStartOfficial<br>
 
**Contribute to Container Use Cases**: https://github.com/cleanstart-dev/cleanstart-use-cases/
