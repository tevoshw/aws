# Policies

Policy é um documento (JSON) que define quais actions são permitidas ou 
negadas, em quais recursos, sob quais condições.

Resumindo: **policy = conjunto de actions em serviços**, com um efeito 
(Allow/Deny) associado.

## Estrutura básica

    {
      "Effect": "Allow",
      "Action": "ec2:StartInstances",
      "Resource": "*"
    }

- **Effect** — permite (`Allow`) ou nega (`Deny`) a action.
- **Action** — a operação específica (ex: `ec2:StartInstances`).
- **Resource** — em qual recurso a action se aplica (ex: uma EC2 específica, ou `*` para todos).
- **Condition** *(opcional)* — restrições adicionais (ex: só permitir de um IP específico).

# 1. AWS Policys EC2

- `AmazonEC2ReadOnlyAccess` Acesso a todos os recursos ec2, porém apenas para leitura 

- `AmazonEC2FullAccess` Acesso completo a todos os recursos ec2