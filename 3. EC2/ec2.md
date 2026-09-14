# 1. O que é
EC2 (Elastic Compute Cloud) é o serviço da AWS que permite criar máquinas virtuais (servidores) na nuvem.

Máquinas virtuais são basicamente computadores

> Para entender melhore sobre máquinas/computadores olhe: https://github.com/tevoshw/exploring-servers

# 2. Estrutura

Uma EC2 possui principalmente 7 estruturas:

## 1. AMI 
.
## 2. Instance type  
.
## 3. Storage (EBS) 
.
## 4. Security Group 
.
## 5. Key pair 
.
## 6. VPC/Subnet 
.
## 7. Public IP
.

# 3. Comandos
Todos os comandos a seguir é supondo que temos a permissão do IAM para tal

**TODOS OS COMANDOS SEMPRE UTILIZARÃO `aws ec2 <comando>`**

1. `describe-instances` Mostra as máquinas e seus tipos 

## 3.1 Funcionamento de instâncias

2. `run-instances` Inicia uma nova instancia

3. `start-instances` Inicia uma instancia parada

4. `stop-instances` Para uma instancia em execução

5. `reboot-instances` Reinicia uma instancia

6. `terminate-instances` Deleta uma instancia

## 3.2 Informação sobre as instâncias

1. `describe-images ` Consulta as AMIs diponiveis

2. `describe-instance-types` Consulta os tipos de EC2 e suas características: vCPU, RAM, rede, etc.

3. `describe-security-groups` Consultainformações dos Security Groups e suas regras. 

4. `describe-volumes ` Consulta os volumes EBS, ou seja, os discos associados às EC2.


