# 1. O que é
EC2 (Elastic Compute Cloud) é o serviço da AWS que permite criar máquinas virtuais (servidores) na nuvem.

Máquinas virtuais são basicamente computadores

> Para entender melhore sobre máquinas/computadores olhe: https://github.com/tevoshw/exploring-servers

# 2. Estrutura

Uma EC2 possui principalmente 7 estruturas:

## 1. AMI 
## 2. Instance type  
## 3. Storage (EBS) 
## 4. Security Group 
## 5. Key pair 
## 6. VPC/Subnet 
## 7. Public IP


# 3. Comandos
Todos os comandos a seguir é supondo que temos a permissão do IAM para tal

**TODOS OS COMANDOS SEMPRE UTILIZARÃO `aws ec2 <comando>`**

`describe-instances` Mostra as máquinas e seus tipos 

`run-instances` Inicia uma nova instancia

`start-instances` Inicia uma instancia parada

`stop-instances` Para uma instancia em execução

`reboot-instances` Reinicia uma instancia

`erminate-instances` Deleta uma instancia


`describe-images ` Consulta as AMIs diponiveis

`describe-instance-types` Consulta os tipos de EC2 e suas características: vCPU, RAM, rede, etc.

`describe-security-groups` Consultainformações dos Security Groups e suas regras. 

`describe-volumes ` Consulta os volumes EBS, ou seja, os discos associados às EC2.


