# 1. O que é

IAM (Identity and Access Management) é o serviço da AWS responsável por controlar quem pode fazer o quê em quais recursos.

Ele controla principalmente:

Quem → usuários, grupos, roles
O quê pode fazer → ações como ec2:StartInstances
Em quê → recursos, como uma determinada EC2
Em quais condições → condições adicionais através de Condition

# 2. Estrutua do IAM

## 1. Users
são as identidades individuais dentro da AWS. Cada usuário representa uma pessoa ou identidade que pode acessar e utilizar recursos da AWS. Um usuário pode possuir suas próprias credenciais e receber permissões através de policies.

## 2. Grupos
são grupos usados para reunir vários usuários. Em vez de configurar as mesmas permissões individualmente para cada usuário, você pode colocar os usuários em um grupo e associar uma policy ao grupo. Assim, todos os usuários daquele grupo recebem aquelas permissões.

## 3. Actions
são ações individuais que uma identidade pode executar em um serviço da AWS. Cada serviço possui suas próprias actions. Por exemplo, no EC2 existem ec2:StartInstances, ec2:StopInstances e ec2:DescribeInstances. Uma Action representa o que pode ser feito.

## 4. Policys
São documentos que definem as permissões dentro da AWS. Elas determinam quais Actions podem ou não ser executadas e podem especificar outras informações, como sobre quais recursos a ação pode ser realizada e em quais condições. Uma policy pode conter várias Actions.

Em vez de ficar dando permissões individualmente:

Tevo
├── ec2:StartInstances
├── ec2:StopInstances
├── ec2:DescribeInstances
└── ec2:DescribeVolumes

Você cria uma Policy contendo essas permissões:

EC2Policy
├── ec2:StartInstances
├── ec2:StopInstances
├── ec2:DescribeInstances
└── ec2:DescribeVolumes

E depois permite para vários usuarios/grupos

Developers
├── Tevo
├── João
├── Maria
└── Carlos
       ↓
   EC2Policy
       ↓
   várias Actions


# 3. Comandos

```python

aws iam create-user # Cria um usuário IAM
aws iam delete-user # Exclui um usuário IAM
aws iam get-user # Obtém informações de um usuário IAM
aws iam list-users # Lista os usuários IAM

aws iam create-policy # Cria uma policy IAM
aws iam get-policy # Obtém informações de uma policy IAM
aws iam list-policies # Lista as policies IAM
aws iam attach-user-policy # Anexa uma policy a um usuáio
aws iam detach-user-policy # Remove uma policy de um usuário

aws iam create-access-key # Cria uma Access Key para um usuário
aws iam list-access-keys # Lista as Access Keys de um usuário
aws iam delete-access-key # Exclui uma Access Key


```