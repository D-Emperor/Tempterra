provider "aws" {
  profile    = "terraiam" #IAM user name
  access_key = "<access_key>"
  secret_key = "<secret_key>"
  region     = "ap-south-1"
}

resource "aws_instance" "linux_instance1" {
  ami = "ami-0f9d9a251c1a44858"
  tags = {
    Name = "Linux-Demo-instance"
  }
  instance_type   = "t2.micro"
  key_name        = "MumbaiKey"
  security_groups = ["${aws_security_group.allow_ssh.name}"]
}

resource "aws_security_group" "allow_ssh" {
  name        = "allow_ssh"
  description = "allow ssh traffic"
  ingress {
    from_port   = 22 # by default, windows server listens to TCP port 3389 for RDP
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
