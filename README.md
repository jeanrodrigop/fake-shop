# Projeto Fake Shop
## Objetivo
O objetivo do projeto é ser um pequeno e-commerce para ser usado como prova de conceito para o processo de deploy de uma aplicação em ambiente Kubernetes com pipeline CI/CD e monitoramento.

## Tecnologias relacionadas
- Python
- Flask
- Postgresql


Variável de Ambiente
DB_HOST => Host do banco de dados PostgreSQL.

DB_USER => Nome do usuário do banco de dados PostgreSQL.

DB_PASSWORD => Senha do usuário do banco de dados PostgreSQL.

DB_NAME => Nome do banco de dados PostgreSQL.

DB_PORT => Porta de conexão com o banco de dados PostgreSQL.

#

Projeto adaptado para rodar no ambiente local

```bash
# Criar cluster k3d
k3d cluster create cluster-aula-2 --servers 3 --agents 3 \
-p "8181:30000@loadbalancer" \
-p "8182:30001@loadbalancer" \
-p "8183:30002@loadbalancer"

# Subir a aplicação e o prometheus com grafana
kubectl apply -f k8s/deployment.yaml
kubectl apply -f prometheus/deployment.yaml

# Obter senha do grafana
kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
