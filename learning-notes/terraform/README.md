# Terraform - Getting Started

> _Infrastructure as Code_:
> Provisioning Infrastructure through **software** to achieve **consistent** and **predictable** deployments

- Defined in code (`json`, `yaml`, `tf`)
- Code is stored in source control and versioned
- Declarative and Imperative approaches 

> _Imperative_:
> Telling exact steps in code to do a thing, in procedural nature.

If we were to describe how to make taco in imperative way:
```
get shell
get beans
get cheese
get lettuce
get salsa

put beans in shell
put cheese on beans
put lettuce on cheese
put salsa on lettuce
```
>_Declarative_:
> By ordering predefined items via common abstractions

If we were to order taco in declarative way:
```tf
#Make me a taco

food taco "bean-taco" {
    ingredients = [
        "beans", "cheese", "lettuce", "salsa"
    ]
}
```

- We are asking for a type food of subtype taco w/ name "bean-taco"
- Terraform is an example of declarative language

>_Idempotency_:
>Each time you do something result should be the same

- Terraform is idempotent if you haven't changed your code and apply again to the same environment nothing will change since defined code matches the reality of the infrastructure that exists

>_Push or Pull_:
> Whether if target environment pulls the configuration or configuration pushed to target environment

- Terraform is has a push type model

Benefits:

- Automated deployment
- Repeatable process
- Consistent environments
- Reusable components
- Documented Architecture

# Deploying Terraform Configuration

## What is Terraform
Tool to automate deployment and Infra. management, it is an open source project managed by hashicorp.

- Vendor agnostic - meaning works with different Cloud providers.

_**Core components:**_

-  Executable, single binary file to run Terraform.
-  Configuration files, with `.tf`
-  Provider plugins allow Terraform to talk with AWS/Azure etc.. at [registry.terraform.io](registry.terraform.io)
-  State data, maintained the current information about environment.

> When an update is issued State data is compared with updated version and plans, executes, updates state data.

## Installing Terraform

- [terraform.io/downloads.html](terraform.io/downloads.html) is place to download information.
- `terraform -h` - gives help

## Object Types

- `Providers` - provider wants to know what AWS region and account we will be using.
- `Resources` - things we want to create in target environment, each resource is associated with a provider and will require additional info for configuration.
- `Data sources` - way to query information from a provider, asking for information to use in configuration, Associated with `Provider`.

_Terraform uses block syntax_
```tf
block_type "label" "name_label" {
    key = "value
    nested_block {
        key = "value"
    }
}
```

_Example creating an EC2 instance in AWS_
```tf
resource "aws_instance" "web_server" {
    name = "web-server"
    ebs_volume {
        size = 40
    }
}
```

- we may refer to an object using the syntax `<resource_type>.<name_label>.<attribute>`, for above example `aws_instance.web_server.name`

- To start let's look at the `main.tf` file at [https://github.com/ned1313/Getting-Started-Terraform/blob/main/base_web_app/main.tf](https://github.com/ned1313/Getting-Started-Terraform/blob/main/base_web_app/main.tf)
  
```tf
##################################################################################
# PROVIDERS
##################################################################################

provider "aws" {
  access_key = "ACCESS_KEY"
  secret_key = "SECRET_KEY"
  region     = "us-east-1"
}

```
> We are telling to provider what AWS account we would like to use, and way of accesing it as well as region.

---

```tf
##################################################################################
# DATA
##################################################################################

data "aws_ssm_parameter" "ami" {
  name = "/aws/service/ami-amazon-linux-latest/amzn2-ami-hvm-x86_64-gp2"
}
```
> We are specifying our `Data source`,  `"aws_ssm_parameter"` stands for service manager with given name `"ami"`, key `name` is path to Amazon Linux to AMI ID for the current region.
---
```tf
##################################################################################
# RESOURCES
##################################################################################

# NETWORKING #
resource "aws_vpc" "vpc" {
  cidr_block           = "10.0.0.0/16"
  enable_dns_hostnames = true

}

resource "aws_internet_gateway" "igw" {
  vpc_id = aws_vpc.vpc.id

}

resource "aws_subnet" "subnet1" {
  cidr_block              = "10.0.0.0/24"
  vpc_id                  = aws_vpc.vpc.id
  map_public_ip_on_launch = true
}
```

> - We are starting resources section with networking.
> - Creating a `"aws_vpc"` service with name `"vpc"`
> - Then creating an `"aws_internet_gateway"` with name `"igw"` this uses `aws_vpc.vpc.id`
> - Then creating a subnet.

```tf
# ROUTING #
resource "aws_route_table" "rtb" {
  vpc_id = aws_vpc.vpc.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.igw.id
  }
}

resource "aws_route_table_association" "rta-subnet1" {
  subnet_id      = aws_subnet.subnet1.id
  route_table_id = aws_route_table.rtb.id
}
```

> This allows inbound and outbound traffic to go through the Gateway.
> then are able to associate route table with subnet.

```tf
# SECURITY GROUPS #
# Nginx security group 
resource "aws_security_group" "nginx-sg" {
  name   = "nginx_sg"
  vpc_id = aws_vpc.vpc.id

  # HTTP access from anywhere
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  # outbound internet access
  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

```tf
# INSTANCES #
resource "aws_instance" "nginx1" {
  ami                    = nonsensitive(data.aws_ssm_parameter.ami.value)
  instance_type          = "t2.micro"
  subnet_id              = aws_subnet.subnet1.id
  vpc_security_group_ids = [aws_security_group.nginx-sg.id]

  user_data = <<EOF
#! /bin/bash
sudo amazon-linux-extras install -y nginx1
sudo service nginx start
sudo rm /usr/share/nginx/html/index.html
echo '<html><head><title>Taco Team Server</title></head><body style=\"background-color:#1F778D\"><p style=\"text-align: center;\"><span style=\"color:#FFFFFF;\"><span style=\"font-size:28px;\">You did it! Have a &#127790;</span></span></p></body></html>' | sudo tee /usr/share/nginx/html/index.html
EOF

}
```
> An EC2 instance running nginx with html page specified

## Workflow
- `$> terraform init` looks for configuration files in current directory, examines if there is a need for any provider plugins. If needed those plugins will be fetched from registries and state data will be outputed to the current dir or to the specified API state data back end.

- `$> terraform plan` Terraform will look at the current configuration and the state data contents, determine differences and make a plan to update our target env. to match the desired plan. Will print and usefull to look at

- `$> terraform apply` **WILL RUN THE PLAN** be careful with this one. Applies the plan and changes the state data.

- `$> terraform destroy` **WILL DESTROY EVERYTHING IN TARGET ENV** be careful with this one. *Here there be dragons* 

## Variables

