# DevOps Pipeline Demo

[![CI](https://github.com/d3Par1/devops-lab1/actions/workflows/main.yml/badge.svg)](https://github.com/d3Par1/devops-lab1/actions/workflows/main.yml)

Лабораторна робота № 1 з дисципліни «Технології DevOps».
Виконав: Степаненко Назар Юрійович, ТВ-43, № 14 у списку групи.

| Завдання | Що в репозиторії |
|---|---|
| 1. Git: конфлікт злиття | `info.txt`, гілка `feature/user-data`, коміт злиття `5ef0f65` |
| 2. Docker | `Dockerfile`, `index.html`, `.dockerignore` |
| 3. Terraform | `terraform/main.tf`, `terraform/.terraform.lock.hcl` |
| 4. GitHub Actions | `.github/workflows/main.yml` |

## Запуск

```bash
# Завдання 2: образ і контейнер, сторінка на http://localhost:8080
docker build -t my-app:latest .
docker run -d --name devops-web -p 8080:80 my-app:latest

# Завдання 3: файл devops_iac_output.txt через Terraform
cd terraform
terraform init
terraform plan
terraform apply
terraform destroy
```

Конвеєр CI запускається на кожен push у `main`: спершу `Test/Lint` (hadolint для Dockerfile),
потім `Build/Package` (`docker build -t my-app:latest .` і перевірка сторінки в контейнері).
