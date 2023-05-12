# terraform-install
this is terraform install
terraform windows download 64 bit
and extract file
folder create and paste
cmd open
terraform -v
sysdm.cp
advanced click
environment variable click
path select and edit click
c:/terraform paste
ok and ok 
terraform -v (13.5)

terraform linux install
wget https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip
unzip terraform_0.11.13_linux_amd64.zip
ls
sudo mkdir terraform
sudo mv terraform terraform/
ls
cd terraform
environment path set cheyala
cd
ls -a
sudo vi .bashrc
path : /home/ec2-user terraform"
save
terraform -v
13.5




create aws using vpc terraform script

first user create 
IAM click
user click and add user click
nmae: user1
program matic  access select
next permissions click
attach exiecting policy directly select
admistrative full access select 
next tags click
create user
simple download

create aws provider using terraform search
docs overview hashigrop click

go to visual studio

provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}



provider "aws" {
  region     = "ap-south-1"
  access_key = "dygyrfhjhhgf"
  secret_key = "sgdghgjhjty"
}

resource "aws_vpc" "vpc" {
  cidr_block       = "192.168.0.0/16"
  instance_tenancy = "default"

  tags = {
    Name = "demo-vpc"
  }
}

resource "aws_subnet" "pub" {
  vpc_id     = aws_vpc.vpc.id
  cidr_block = "192.168.1.0/24"

  tags = {
    Name = "public"
  }
}
create aws subnet using terraform


resource "aws_subnet" "pri" {
  vpc_id     = aws_vpc.vpc.id
  cidr_block = "192.168.3.0/24"

  tags = {
    Name = "private"
  }
}
create aws internet gateway using terraform
resource "aws_internet_gateway" "igw" {
  vpc_id = aws_vpc.vpc.id

  tags = {
    Name = "igw"
  }
}


resource "aws_eip" "ip" {
  instance = aws_instance.web.id
  vpc      = true
}

create aws nat gateway using terraform

resource "aws_nat_gateway" "ngw" {
  allocation_id = aws_eip.nat.id
  subnet_id     = aws_subnet.pri.id

  tags = {
    Name = "NGW NAT"
  }
}

route table
create aws route table using terraform














resource "aws_security_group" "sg" {
  name        = "first-SG"
  description = "Allow TLS inbound traffic"
  vpc_id      = aws_vpc.main.id

  ingress {
    description      = "TLS from VPC"
    from_port        = 22
    to_port          = 22
    protocol         = "tcp"
    cidr_blocks      = [aws_vpc.vpc.cidr_block]
    ipv6_cidr_blocks = [aws_vpc.main.ipv6_cidr_block]
  }

  egress {
    from_port        = 0
    to_port          = 0
    protocol         = "-1"
    cidr_blocks      = ["0.0.0.0/0"]
    ipv6_cidr_blocks = ["::/0"]
  }

  tags = {
    Name = "SG"
  }
}


resource "aws_route_table_association" "as_1" {
  subnet_id      = aws_subnet.pub.id
  route_table_id = aws_route_table.rt1.id
}


resource "aws_route_table_association" "as_2" {
  subnet_id      = aws_subnet.pri.id
  route_table_id = aws_route_table.rt2.id
}

cdrive folder path copy open to power shell

terraform init(total vpc provider)
terraform validate(the configuration valid)
floder create aws all plugins information
terraform plan(11 to add resources)
terraform apply (create a vpc)
go to aws account vpc create :demo-vpc
subnet public
private
all resources created
(actions click and dns hostnames dns enable and support)



















