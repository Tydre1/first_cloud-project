# Implementando o Projeto Hands-on - Parte 1 com Cloud AWS e GCP

Publicação da parte 1 no LinkedIn - [Imersão Cloud](https://www.linkedin.com/posts/andr%C3%A9-barbosa229_cloudcomputing-aws-gcp-activity-7097391099354202113-WJLP?utm_source=share&utm_medium=member_desktop)

Olá, pessoal! Nesta parte do projeto, vamos mergulhar na implementação prática do Hands-on, utilizando as nuvens Amazon Web Services (AWS) e Google Cloud Platform (GCP). Vamos dar uma olhada nos passos que segui para fazer isso acontecer:

## Amazon Web Services (AWS)

1. Comecei acessando a console da AWS e digitei "IAM" na barra de pesquisa para encontrar o serviço de Gerenciamento de Identidade e Acesso (IAM).
2. Cliquei em "Users" e selecionei "Add users" para criar um novo usuário.
3. Defini o nome do usuário como **terraform-pt-1** e configurei como um usuário programático.
4. Na etapa de permissões, cliquei em "Attach existing policies directly".
5. Pesquisei por **AmazonS3FullAccess** e selecionei essa política, dando ao usuário acesso total ao Amazon S3.
6. Finalizei a criação do usuário.

## Google Cloud Platform (GCP)

1. Baixei o arquivo **Mission1.zip** do projeto hands-on a partir deste [link](https://tcb-public-events.s3.amazonaws.com/icp/mission1.zip).
2. Acessei a console da GCP e abri o Cloud Shell.
3. Fiz o upload dos arquivos **accessKeys.csv** e **mission1.zip** para o Cloud Shell.
4. Verifiquei se os arquivos foram carregados com sucesso usando o comando `ls -la`.
5. Executei alguns comandos para preparar os arquivos e conceder permissões.

```shell
mkdir mission1_pt
mv mission1.zip mission1_pt
cd mission1_pt
unzip mission1.zip
mv ~/accessKeys.csv mission1/pt
cd mission1/pt
chmod +x *.sh
```

6. Configurei as credenciais da AWS e defini o projeto GCP:

```shell
./aws_set_credentials.sh accessKeys.csv
gcloud config set project <your-project-id>
```

7. Autorizei a integração e configurei o projeto no Google Cloud Shell.

```shell
./gcp_set_project.sh
```

8. Habilitei as APIs do Kubernetes, Container Registry e Cloud SQL:

```shell
gcloud services enable containerregistry.googleapis.com
gcloud services enable container.googleapis.com
gcloud services enable sqladmin.googleapis.com
```

9. Antes de usar o Terraform, abri o Google Cloud Editor para atualizar o arquivo **tcb_aws_storage.tf**, substituindo o nome do bucket para um exclusivo.

10. Finalmente, estava pronto para provisionar os recursos da infraestrutura:

```shell
cd ~/mission1_pt/mission1/pt/terraform/

terraform init
terraform plan
terraform apply
# Confirme com 'yes'
```

Depois de um tempinho, os recursos estarão prontos. E lembrem-se, o Cloud SQL pode levar um tempinho para ser criado.

Com isso, encerro a parte 1 do Projeto Hands-on. Implementei recursos em várias nuvens usando o Terraform. Estamos no caminho certo! 🚀🎉

---
