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


# 1. Amazon Actions

- `AmazonEC2ReadOnlyAccess` Acesso a todos os recursos ec2, porém apenas para leitura 

- `AmazonEC2FullAccess` Acesso completo a todos os recursos ec2

# 2. AWS Actions

## 2.1 Consultar sobre informações

`ec2:DescribeInstances` Quais máquinas eu tenho e suas informações

`ec2:DescribeImages` Consulta as AMIs dipo

`ec2:DescribeInstanceTypes` Consulta os tipos de EC2 e suas características: vCPU, RAM, rede, etc.

`ec2:DescribeSecurityGroups` Consulta informações dos Security Groups e suas regras. 

`ec2:DescribeVolumes` Consulta os volumes EBS, ou seja, os discos associados às EC2.

## 2.2 Controle do EC2

`ec2:RunInstances` Cria uma nova EC2.

`ec2:StartInstances` Inicia uma EC2 que está parada.

`ec2:StopInstances` Para uma EC2 em execução.

`ec2:RebootInstances` Reinicia uma EC2, como reiniciar um computador.

`ec2:TerminateInstances` Encerra uma EC2, removendo a instância.

## 2.3 Segurança / acesso
`ec2:CreateSecurityGroup` Cria um novo Security Group.

`ec2:DeleteSecurityGroup` Exclui um Security Group.

`ec2:AuthorizeSecurityGroupIngress` Adiciona uma regra de entrada no Security Group.

`ec2:RevokeSecurityGroupIngress`  Remove uma regra de entrada do Security Group.

`ec2:DescribeSecurityGroups` Consulta Security Groups e suas configurações.