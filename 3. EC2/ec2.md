# 1. O que é
EC2 (Elastic Compute Cloud) é o serviço da AWS que permite criar máquinas virtuais (servidores) na nuvem.

Máquinas virtuais são basicamente computadores

> Para entender melhore sobre máquinas/computadores olhe: https://github.com/tevoshw/exploring-servers

# 2. Estrutura

Uma EC2 possui principalmente 7 estruturas:

## 1. AMI
Molde/template usado pra criar a instância. Define sistema operacional, 
configurações iniciais e softwares pré-instalados.

## 2. Instance type
Define o hardware: CPU, RAM, rede e (se aplicável) GPU. 
Formato: `família.tamanho` (ex: `t3.medium`, `p3.2xlarge`).

## 3. Storage (EBS)
Disco/volume anexado à instância. É onde fica o sistema operacional 
(vindo da AMI) e os dados. Pode ter snapshots (backups).

## 4. Security Group
Firewall virtual da instância. Controla tráfego de entrada e saída 
(portas, protocolos, origem/destino permitida).

## 5. Key pair
Par de chaves (pública/privada) usado pra autenticação via SSH. 
Substitui usuário/senha no acesso direto à instância.

## 6. VPC/Subnet
Rede isolada (VPC) onde a instância mora, e o pedaço específico dela 
(subnet) que define se tem ou não rota pra internet (pública/privada).

## 7. Public IP
Endereço que torna a instância acessível pela internet. Só existe se a 
subnet for pública e a opção estiver ativada (dinâmico ou Elastic IP fixo).

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


