# 1. O que é
EC2 (Elastic Compute Cloud) é o serviço da AWS que permite criar máquinas virtuais (servidores) na nuvem.

Máquinas virtuais são basicamente computadores

> Para entender melhore sobre máquinas/computadores olhe: https://github.com/tevoshw/exploring-servers

# 2. Estrutura

Uma EC2 possui principalmente

1. AMI → imagem/base do sistema operacional
2. Instance type → CPU, RAM etc.
3. Storage (EBS) → disco
4. Security Group → firewall
5. Key pair → autenticação SSH
6. VPC/Subnet → rede
7. Public IP → endereço público, quando configurado


# Comandos
Todos os comandos a seguir é supondo que temos a permissão do IAM

```python

aws ec2 describe-instances # Mostra as máquinas e seus tipos 
aws ec2 run-instances # Inicia uma nova instancia
aws ec2 start-instances # Inicia uma instancia parada
aws ec2 stop-instances # Para uma instancia em execução
aws ec2 reboot-instances # Reinicia uma instancia
aws ec2 terminate-instances # Deleta uma instancia

aws ec2 describe-images  # Consulta as AMIs dipo
aws ec2 describe-instance-types # Consulta os tipos de EC2 e suas características: vCPU, RAM, rede, etc.
aws ec2 describe-security-groups # Consulta informações dos Security Groups e suas regras. 
aws ec2 describe-volumes  # Consulta os volumes EBS, ou seja, os discos associados às EC2.

```
