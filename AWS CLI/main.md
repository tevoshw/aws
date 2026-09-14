# 1. O que é o AWS CLI
 
Ferramenta instalada no computador que traduz comandos de texto via CLI em chamadas de API pra AWS. Fluxo:
 
```
1. Você (terminal) → 
2. AWS CLI → 
3. Usa credenciais salvas (~/.aws/) → 
4. API da AWS → 
5. IAM verifica permissão → 
6. Libera/nega → 
7. resposta formatada
```

# 2. Comandos Gerais

A estrutura básica é

`aws <serviço> <ação>` Como por exemplo `aws ec2 describe-instances`


1. `aws --version` Verifica se está o software cli do aws está instalado e qual sua versão

2. `aws --help` Retrata os comandos, para quando esquecer


## 3. Acesso ao AWS CLI (login)

### ACESS KEY

1. `aws configure` Se conectar em conta aws via acess key (default)

2. `aws configure --profile <user>` Se conectar em uma conta não default via acess key 


### SSO
1. `aws configure sso` Se conectar em conta aws via sso (default)

2. `aws configure sso --profile <user>` Se conectar em conta não default via sso


# 4. Informações/Atualizar sobre as configurações

1. `aws configure list` Ver as configurações atuais

2. `aws configure get <info>` Verifica uma configuração específica

3. `aws configure set <info>` Define uma nova configuração específica



# 5. Extras


## 5.1 Profiles 
**1. Para se fazer comandos em usuarios diferentes utilizados o --profile <user> na frente deles**

`aws <comand> --profile <user>` 

       Exemplo: aws ec2 describe-instances --profile tevoshw

---

**2. Para listar os usuários existentas naquela máquina**

`aws configure list-profiles`  

---     

**3. Para listar um usuario especifico**

`aws configure list --profile <user>` 

## 5.2 Regions
Para se fazer comandos em regiões diferentes utilizamos o --region

1. `aws <command> --region <region>` 

        aws ec2 describe-instances --region sa-east-1

## 5.3 Outputs
Para se definir o output da API no terminal usamos o --output, caso não, o default que definimos no configure será o utilizado

1. `aws <comando> --output <type>` 

        aws ec2 describe-instances --output table
