FROM centos:7

# Instalar dependências necessárias
RUN yum install -y wget gcc openssl-devel cairo cairo-devel cairomm-devel python36 python36-devel libxslt-devel libffi-devel gcc-c++ kernel-devel

# Instalar pip3
RUN yum install -y https://download-ib01.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-14.noarch.rpm
RUN yum install -y python36-pip

# Add a step to upgrade pip
RUN pip3 install --upgrade pip

# Copiar e instalar dependências do requirements.txt
COPY requirements.txt /srv/
RUN pip3 install -r /srv/requirements.txt

# Limpeza das ferramentas de compilação
RUN yum remove gcc kernel-devel gcc-c++ -y
RUN yum clean all
RUN rm -rf /var/cache/yum

# Copiar o aplicativo
COPY app.py /srv/

# Definir o comando padrão
CMD ["python3.6", "/srv/app.py"]
