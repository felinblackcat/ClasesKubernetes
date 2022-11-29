# Second Class Kubernetes
## Objetive: 
Deploy django app using kubernetes withouth volumen clain

## Steps:
- Make docker file with django dependences. (Multistep)
- Pull image to docker hub
- Prepare Ecosystem (namespace, resourcequotas)
- Prepare environment variables and secrets (create config maps and secrets)
- Prepare deployment (create deployment to app and database/s)
- Prepare expose (create service)

## Conclusions

## Next Step
- Volumes Theory (PersistenVolumen, after use it with persistentvolumeclaim)
- Use volumes with django app
- CI/CD 
- Understand metrics
- Whats grafana and ...
- Autoscaling app using data analitycs
- Examples: Deployment jenkis, deployment cluster db (postgres, mysql, mongodb)
