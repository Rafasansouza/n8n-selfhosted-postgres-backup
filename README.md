
# n8n Self-Hosted com PostgreSQL e Backup Automático

Este repositório contém um ambiente completo para rodar o [n8n](https://n8n.io/) auto-hospedado utilizando Docker. A stack inclui:

- Banco de dados PostgreSQL persistente
- Interface do n8n acessível localmente
- Backup automático diário do banco de dados (`pg_dump`)

Ideal para automações profissionais em empresas ou uso pessoal avançado.

---

## 🚀 Instalação

### Pré-requisitos

- [Docker](https://www.docker.com/products/docker-desktop) instalado
- [Docker Compose](https://docs.docker.com/compose/install/) instalado

### Passo a passo

1. Clone este repositório:

```bash
git clone https://github.com/seu-usuario/n8n-selfhosted-postgres-backup.git
cd n8n-selfhosted-postgres-backup
```

2. Suba os containers com Docker Compose:

```bash
docker-compose up -d
```

3. Acesse o n8n em seu navegador:

```
http://localhost:5678
```

4. Faça login com:

```
Usuário: admin
Senha: admin123
```

> ⚠️ Altere as credenciais no `docker-compose.yml` para uso em produção.

---

## 💾 Backups

Os backups automáticos são realizados diariamente e salvos no diretório local:

```
./backups/n8n_backup_YYYY-MM-DD.sql
```

- Formato: `.sql` (compatível com `pg_restore`)
- Frequência: 1 vez a cada 24h
- Volume persistente: `./backups`

---

## 📁 Estrutura do Projeto

```
n8n-selfhosted-postgres-backup/
├── docker-compose.yml
├── n8n_data/           # Dados do n8n (workflows, credenciais, etc.)
├── postgres_data/      # Dados do PostgreSQL
└── backups/            # Backups diários do banco
```

---

## 🔐 Segurança e Produção

- Use senhas fortes para `POSTGRES_PASSWORD` e `N8N_BASIC_AUTH_PASSWORD`
- Considere usar NGINX como proxy reverso com HTTPS (Let's Encrypt)
- Configure backup remoto (ex: Google Drive, OneDrive, FTP)
- Faça snapshots regulares dos volumes

---

## 🧠 Recursos úteis

- Documentação oficial do n8n: https://docs.n8n.io
- Lista de integrações: https://n8n.io/integrations
- Comunidade: https://community.n8n.io

---