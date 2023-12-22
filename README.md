# Репризиторій AWS_Kubernetes-
# Інфраструктура AWS з використанням Terraform

Цей репозиторій містить код Terraform для створення AWS Virtual Private Cloud (VPC) та Amazon Elastic Kubernetes Service (EKS).

## Передумови

Перш ніж розпочати, переконайтеся, що у вас є наступне:
- Облікові дані облікового запису AWS (ключ доступу та секретний ключ) з відповідними дозволами.
- Встановлений Terraform на вашому комп'ютері. [Посібник з встановлення Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli)

## Налаштування

### Налаштування провайдера AWS

У файлі `main.tf` ви знайдете блок конфігурації провайдера для AWS:

```hcl
provider "aws" {
  region     = "eu-north-1"
  access_key = "access_key_IAM"
  secret_key = "secret_key_IAM"
}
```

### Налаштування провайдера AWS

У файлі `main.tf` ви знайдете блок конфігурації провайдера для AWS. Замініть `"ваш_ключ_доступу_IAM"` та `"ваш_секретний_ключ_IAM"` на ваші облікові дані IAM AWS.

### Конфігурація змінних

Для налаштування ресурсів відредагуйте змінні у файлі `variables.tf` згідно ваших потреб. Деякі ключові змінні включають:
- `locals.name`: Назва ваших ресурсів (за замовчуванням: "kubik").
- `locals.vpc_cidr`: CIDR-блок для VPC.
- `locals.azs`: Зони доступності для використання.
- `local.public_subnets`, `local.private_subnets`, `local.intra_subnets`: Налаштування підмереж.

### Модулі

У цьому репозиторії використовуються такі модулі Terraform:
- `terraform-aws-modules/vpc/aws`: Створює VPC, підмережі та необхідні мережеві компоненти.
- `terraform-aws-modules/eks/aws`: Налаштовує кластер Amazon EKS з керованими групами вузлів.

## Використання

1. Ініціалізуйте Terraform:

```bash
terraform init
```

2. Застосуйте зміни для створення інфраструктури:

```bash
terraform init
```

3. Застосуйте зміни для створення інфраструктури:

```bash
terraform apply
```

## Очищення

Для знищення створених ресурсів Terraform використовуйте:

```bash
terraform destroy
```

 - Увага: Будьте обережні при виконанні terraform destroy, оскільки це остаточно видалить створену інфраструктуру.
