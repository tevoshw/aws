# 1. O que é AWS

AWS (Amazon Web Services) é a plataforma de cloud computing da Amazon, que disponibiliza infraestrutura e serviços sob demanda, com cobrança baseada 
em uso (pay-as-you-go).

Alguns serviços principais:

- **EC2** — servidores virtuais (máquinas na nuvem)
- **S3** — armazenamento de arquivos/objetos
- **RDS** — bancos de dados relacionais gerenciados (Postgres, MySQL, etc.)
- **Lambda** — execução de código sem gerenciar servidor (serverless)
- **IAM** — gerenciamento de usuários, permissões e acesso


# 2. AWS via CLI

A AWS possui um site (Console) para criar e utilizar seus produtos. Porém, 
em empresas grandes, gerenciar tudo manualmente pelo site não escala bem é lento, repetitivo e propenso a erro humano.

Pra resolver isso, a AWS disponibiliza uma **CLI** (Command Line Interface), 
que permite acessar os mesmos recursos via terminal útil pra automação, 
scripts e integração com CI/CD.

Por isso trataremos AWS como o Git, assim como o Git precisa do software `git` instalado pra usar seus comandos (`git commit`, `git push`...), a AWS precisa do **AWS CLI** instalado pra usar seus comandos (`aws s3`, `aws ec2`...).

Sem o CLI instalado, os comandos `aws` simplesmente não existem no seu 
terminal — é o programa que interpreta e executa essas instruções.