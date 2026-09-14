
# Amazon

AmazonEC2ReadOnlyAccess: Acesso a todos os recursos ec2, porém apenas para leitura 
AmazonEC2FullAccess: Acesso completo a todos os recursos ec2

# Policys

## Consult
ec2:DescribeInstances # Quais máquinas eu tenho e suas informações
ec2:DescribeImages # Consulta as AMIs dipo
ec2:DescribeInstanceTypes # Consulta os tipos de EC2 e suas características: vCPU, RAM, rede, etc.
ec2:DescribeSecurityGroups # Consulta informações dos Security Groups e suas regras. 
ec2:DescribeVolumes # Consulta os volumes EBS, ou seja, os discos associados às EC2.

## Control EC2

ec2:RunInstances # Cria uma nova EC2.
ec2:StartInstances # Inicia uma EC2 que está parada.
ec2:StopInstances # Para uma EC2 em execução.
ec2:RebootInstances # Reinicia uma EC2, como reiniciar um computador.
ec2:TerminateInstances #  Encerra uma EC2, removendo a instância.

## Segurança / acesso
ec2:CreateSecurityGroup # Cria um novo Security Group.
ec2:DeleteSecurityGroup # Exclui um Security Group.
ec2:AuthorizeSecurityGroupIngress # Adiciona uma regra de entrada no Security Group.
ec2:RevokeSecurityGroupIngress #  Remove uma regra de entrada do Security Group.
ec2:DescribeSecurityGroups # Consulta Security Groups e suas configurações.