# 1. O que é o AWS CLI
 
Ferramenta instalada no computador que traduz comandos de texto em chamadas de API pra AWS. Fluxo:
 
```
Você (terminal) → AWS CLI → usa credenciais salvas (~/.aws/) → API da AWS → IAM verifica permissão → libera/nega → resposta formatada
```

# 2. Comandos Gerais

A estrutura básica é

```python 
aws <serviço> <ação> [opções]
```


## Info sobre o CLI

```python

aws --version # Verifica se está instalado e qual sua versão

aws --help # Ajuda em alguns comandos

```

## Configurações do CLI

```python

# ACESS KEY
aws configure ## Se conectar em conta aws via acess key (default)

aws configure --profile <user> ## Se conectar em uma conta não default via acess key


# SSO
aws configure sso ## Se conectar em conta aws via sso (default)

aws configure sso --profile <user> ## Se conectar em conta não default via sso


# Info sobre as configurações
aws configure list ## Ver as configurações atuais

aws configure get <info> ## Verifica uma configuração 

aws configure set <info> ## Define uma nova configuração



# Extra 

## Para se fazer comandos em usuarios diferentes utilizados o --profile <user> na frente deles
aws <comand> --profile <user> 
aws ec2 describe-instances --profile tevoshw 

## Para se fazer comandos em regiões diferentes utilizamos o --region
aws <command> --region <region> 
aws ec2 describe-instances --region sa-east-1



## Para se definir o output da API no terminal usamos o --output, caso não, o default que definimos no configure será o utilizado

aws <comando> --output <type>
aws ec2 describe-instances --output table

## Listar usuarios
aws configure list-profiles
aws configure list --profile <user> ## Ver configurações de um user especifico


```
