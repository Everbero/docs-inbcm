# Passo a passo para instalar o LAMP + Wordpress debian/ubuntu
Este tutuorial explica como instalar o Wordpress em sua máquina local

## Passo 1 - Instalar o apache

```
$ sudo apt install apache2  -y
```

## Passo 2 - Instalar o php (7.4+ funciona)
```
$ sudo apt install php
```
## Passo 2.1 - Instalar os pacotes do php que o wordpress usa
```
sudo apt install libapache2-mod-php php-pear php-cgi php-common php-mbstring php-zip php-net-socket  php-gd php-xml-util php-mysql php-bcmath unzip wget git -y
```

## Passo 3 - Instalar o banco de dados, neste caso MariaDb
```
$ sudo apt install mariadb-server mariadb-client -y
```

## Passo 3.1 - Configurar o banco de dados
Neste passo pode responder sim em tudo, mas recomendo não mudar o tipo de autenticação/senha quando solicitado

```
$ sudo mysql_secure_installation
```

## Passo 4 - Criar um banco para o wordpress
acessar o shell do mysql

```
$ sudo mysql -u root -p
```

Rodar os comandos a seguir, substituia {senha} pela sua senha, coloque ; no final de cada comando:
```
CREATE DATABASE wordpressdb;
GRANT ALL PRIVILEGES ON wordpressdb.* to root@localhost identified by '{senha}';
FLUSH PRIVILEGES;
QUIT;
```
## Passo 5 - Configurando o virtualhost para a instalação
Navegue para a pasta de virtualhosts para melhor visualiação
```
$ cd /etc/apache2/sites-available/
```
Faça uma cópia do default para facilitar o trabalho, renomeando para o novo host
```
$ sudo cp 000-default.conf wordpress.conf
```
Edite a configuração
```
$ sudo nano wordpress.conf
```
Configure assim:  
ServerName nomedosite.dominio (no meu caso wordpress.xyz)  
DocumentRoot /var/www/wordpress  

Habilite o site
```
$ sudo a2ensite wordpress.conf
```

## Passo 6 - configurar o arquivo de hosts
{ip} - {nome do host}
por ex:
127.0.0.1 - wordpress.local

## Passo 7 - Habilitar a reescrita de URLs nas configurações do apache
Isso vai permitir ter links amigáveis no wordpress: ex: site.com.br/link-amigavel

Adicionando:
```
<Directory /var/www/wordpress>
        Options Indexes FollowSymLinks
        AllowOverride All 
        Require all granted
</Directory>
```
ao arquivo /etc/apache2/apache2.conf

```
$ sudo nano /etc/apache2/apache2.conf
```

habilite mod_rewrite para permitir a reescrita de urls

```
$ sudo a2enmod rewrite
```

## Passo 8 - Baixar o wordpress
ir para a pasta destino
```
$ cd /var/www/wordpress/
```
Baixar a versão mais recente do wp
```
$ sudo wget https://wordpress.org/latest.zip
```
descompactar (instale $ sudo apt install zip unzip caso não exista o pacote)
```
$ sudo unzip latest.zip
```

Desta forma o unzip já cria a pasta wordpress que estava compactada :)

## Passo 9 - Mudar o proprietário dos arquivos
```
$ sudo chown -R www-data:www-data /var/www/wordpress
```
## Passo 10 - Reiniciar o apache
```
$ sudo service apache2 restart
```
ou
```
$ sudo systemctl restart apache2
```
## Passo 11 - Acesse o endereço do site no navegador e siga o passo a passo da instalação
No meu caso http://wordpress.local

### Outras dicas
Ao acessar o wordpress visite Configurações > links permanetes e mude a estrutura para 'nome do post'  
Não consegue gravar arquivos ou instalar plugins? Certifique-se de ter executado o passo 9.  