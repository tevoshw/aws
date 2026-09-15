# Actions, o que são

Actions são as operações específicas que podem ser permitidas ou negadas 
numa policy — basicamente "o que pode ser feito" em um serviço.

Formato: `servico:Acao`

## Exemplo prático

Se o usuário roda no terminal:

    aws ec2 describe-instances

Por baixo, isso corresponde à action `ec2:DescribeInstances`.

- **Se a policy do usuário permite** essa action → o comando funciona e 
  retorna a lista de instâncias EC2.
- **Se não permite** → a AWS recusa e retorna erro de acesso negado 
  (`UnauthorizedOperation` / `AccessDenied`), mesmo que o comando esteja 
  digitado corretamente.

Ou seja: a action não é sobre o comando em si (sintaxe), é sobre a 
**permissão** de executar aquela

# 1. AWS Actions

## 1.1 Consultar Informações

`iam:GetUser` Consulta dados de um usuário.

`iam:ListUsers` Lista todos os usuários.

`iam:GetRole` Consulta dados de uma role.

`iam:ListRoles` Lista todas as roles.

`iam:GetPolicy` Consulta dados de uma policy.

`iam:ListPolicies` Lista todas as policies.

`iam:ListAttachedUserPolicies` Lista policies anexadas a um usuário.

## 1.2 Controle de grupo/usuarios/roles

`iam:CreateUser` Cria um novo usuário.

`iam:DeleteUser` Exclui um usuário.

`iam:CreateRole` Cria uma nova role.

`iam:DeleteRole` Exclui uma role.

`iam:CreateGroup` Cria um novo grupo.

`iam:AddUserToGroup` Adiciona usuário a um grupo


## 1.3 Permissões / policies

`iam:AttachUserPolicy` Anexa uma policy a um usuário.

`iam:DetachUserPolicy` Remove uma policy de um usuário.

`iam:AttachRolePolicy` Anexa uma policy a uma role.

`iam:PutUserPolicy` Cria/atualiza uma policy inline no usuário.

`iam:CreatePolicy` Cria uma nova policy.

`iam:DeletePolicy` Exclui uma policy.

## 1.4 Credenciais

`iam:CreateAccessKey` Cria uma access key para um usuário.

`iam:DeleteAccessKey` Exclui uma access key.

`iam:UpdateAccessKey` Ativa/desativa uma access key.

`iam:ChangePassword` Altera a senha do usuário.

## 1.5 Assumir role

`sts:AssumeRole` Permite assumir uma role (troca temporária de permissões).

