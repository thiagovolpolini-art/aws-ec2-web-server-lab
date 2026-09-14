# ☁️ Laboratório de Servidor Web AWS EC2

Projeto desenvolvido durante um laboratório prático de **Amazon Web Services (AWS)** com o objetivo de criar, configurar e disponibilizar um servidor web utilizando uma instância **Amazon EC2**.

Durante o laboratório, configurei a infraestrutura de rede, instalei o servidor Apache e publiquei uma página HTML acessível através da internet.

---

## 🎯 Objetivo

Criar uma instância EC2 utilizando **Amazon Linux 2023** e configurá-la para funcionar como um servidor web.

O projeto envolveu desde a criação da infraestrutura de rede até a publicação e validação de uma página HTML.

---

## 🛠️ Tecnologias e serviços utilizados

- Amazon Web Services (AWS)
- Amazon EC2
- Amazon VPC
- Amazon EBS
- Amazon Linux 2023
- Security Groups
- EC2 Instance Connect
- Apache HTTP Server (`httpd`)
- Linux
- SSH
- HTML

---

## 🏗️ Arquitetura

A infraestrutura utilizada no laboratório foi composta por:

**Internet → Security Group → Sub-rede pública → EC2 → Apache → Página HTML**

A instância EC2 foi criada dentro de uma **VPC**, utilizando uma **sub-rede pública** e endereço IPv4 público para permitir acesso ao servidor pela internet.

---

## ⚙️ Configuração da EC2

A instância foi configurada com:

- **AMI:** Amazon Linux 2023
- **Tipo de instância:** `t3.micro`
- **Armazenamento:** Amazon EBS SSD `gp2`
- **IPv4 público:** habilitado
- **Servidor web:** Apache HTTP Server (`httpd`)

O Security Group foi configurado para permitir:

| Serviço | Porta | Finalidade |
|---|---:|---|
| SSH | 22 | Acesso remoto à instância |
| HTTP | 80 | Acesso ao servidor web |

---

## 🌐 Configuração de rede

Durante o laboratório, foram configurados:

- VPC
- Sub-rede pública
- IPv4 público
- Security Group
- Regras de entrada para SSH e HTTP

Essa etapa permitiu que a instância EC2 pudesse ser administrada remotamente e que a página hospedada fosse acessada através da internet.

---

## 💻 Instalação do Apache

A instalação e inicialização do Apache foram automatizadas utilizando **User Data** na criação da instância.

```bash
#!/bin/bash
yum install -y httpd
systemctl start httpd
systemctl enable httpd
chmod 777 /var/www/html
```

O Apache foi configurado para iniciar automaticamente junto com a instância.

---

## 📄 Publicação da página

A instância foi acessada utilizando **EC2 Instance Connect**.

O arquivo HTML foi criado e posteriormente copiado para o diretório utilizado pelo Apache:

```bash
nano projects.html
cp projects.html /var/www/html/
ls /var/www/html/
```

Após a publicação, o arquivo `projects.html` ficou disponível através do servidor web.

---

## 📸 Evidências

### Página publicada

A página HTML foi acessada através do navegador utilizando o servidor web hospedado na EC2.

![Página web funcionando](imagens/pagina-web.png)

### Configuração pelo terminal

Utilização do terminal da instância para criação e publicação do arquivo HTML.

![Terminal EC2](imagens/terminal-ec2.png)

### Apache em execução

O log do sistema da instância confirmou a configuração do serviço `httpd`.

![Log do HTTPD](imagens/log-httpd.png)

---

## 🧠 O que aprendi

Este laboratório permitiu colocar em prática conceitos importantes de computação em nuvem e infraestrutura AWS, principalmente:

- Criação e configuração de instâncias EC2
- Diferença entre endereços IP privados e públicos
- Funcionamento de VPCs e sub-redes
- Configuração de Security Groups
- Acesso remoto utilizando SSH/EC2 Instance Connect
- Utilização de comandos Linux
- Instalação e gerenciamento de serviços com `systemctl`
- Hospedagem de uma página utilizando Apache
- Utilização de User Data para automatizar configurações

Um dos principais aprendizados foi entender como **EC2, VPC, sub-rede, Security Groups e endereços IP trabalham em conjunto para disponibilizar um serviço na internet**.

---

## 👨‍💻 Autor

**Thiago Volpolini**

Estudante de Análise e Desenvolvimento de Sistemas, desenvolvendo conhecimentos em **Cloud Computing, AWS, Dados e Desenvolvimento**.
