# deploy-EC2-Terraform

## Pré-requisitos

- Conta AWS
- AWS CLI
- VSCode

## Instalar o Terraform

```
https://developer.hashicorp.com/terraform/install
```

1. Depois de baixar o arquivo compactado, extraia-o e crie um pasta no __disco C__ chamada __terraform__ e vamos colocar o arquivo executável __terraform.exe.__ dentro dela.

```
md terraform-aws-example
```
```
cd .\terraform-aws-example\
```

## Configurar o PATH para o Terraform

1. Clique no menu iniciar no __Windows__, e pesquise por: __exibir configurações avançadas do sistema__

2. Em seguida, A tela __Propriedades do sistema será exibida__, clique em __Variáveis de Ambiente__.

3. Na tela de variáveis de Ambiente, clique em __Path__ –> __Editar__.

4. Selecione a opção __Novo__, insira o caminho __C:\terraform__ e depois clicar em __OK__.

- Clique em Ok até fechar todas as telas das variáveis de ambiente.

## Validar se as configurações foram feitas de forma correta

1. Vamos verificar a versão do __Terraform__ instalada. Abra o terminal no Windows e digite o comando:

```
terraform -version
```

- Em seguida crie o arquivo de configuração do __Terraform__, usando o comando code __main.tf__, para abrir o __VSCode__

- Dentro do arquivo __main.tf__ no vscode, adicione a seguinte configuração para criar uma instância __ec2__ e salve o arquivo.

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16"
    }
  }

  required_version = ">= 1.2.0"
}

provider "aws" {
  region  = "us-west-2"
}

resource "aws_instance" "compass_terraform" {
  ami           = "ami-830c94e3"
  instance_type = "t2.micro"

  tags = {
    Name = "ExampleInstance"
  }
}
```

## De volta ao Terminal

- Ao criar uma nova configuração, você precisa inicializar o diretório com terraform init.

- Aplique a configuração agora com o __terraform apply__.

## AGORA NO AWS CONSOLE

1.Verifique o console da AWS para confirmar a criação da instância EC2.

- Em Serviços procure por __EC2__, e veja as __Instances__ que estão rodando:

## No terminal
E depois use o comando __terraform destroy__ para encerrar a __ec2 instance__

## No Console AWS
Verifique se a instancia foi encerrada corretamente no console
