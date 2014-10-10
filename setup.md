
# How to replicate this website on a fresh DigitalOcean droplet

## About the Wordpress Application on DO

- https://www.digitalocean.com/community/tutorials/one-click-install-wordpress-on-ubuntu-14-04-with-digitalocean


## 1. Remove default Wordpress

```
cd /var
mv www www-DO
```

## 2. Install git

```
apt-get install git
```

## 3. Clone the repo and change the group ownership, and create a link

```
cd /var
git clone https://github.com/mnmo/infocards.git
chown www-data:www-data -R infocards
ln -s /var/infocards/wordpress /var/www
```

## 4. Config the wordpress using a web-browser

- navigate to your machine's IP url
- use the credentials for the admin on the http auth dialog
  - ```cat /root/WORDPRESS```
- use the database name, user and password from the default DO wp-config.php
  - ```cat /var/www-DO/wp-config.php |grep DB_```

### 4.1 Infocards site config

#### 4.1.1 Content import

- Ferramentas > Importar > Wordpress
- choose the .xml exported file from the production website
- check the option "Baixar e importar arquivos anexos"

#### 4.1.2 Configuration

- Configurações > Geral
  - title = "Infocards"
  - description = "Serviços e Processamento"
- Configurações > Leitura
  - "A página inicial mostra" = "Uma página estática (selecionar abaixo)"
    - Home
- Configurações > Links Permanentes
  - "Estrutura Personalizada" = /%postname%

#### 4.1.3 Plugins

- Enable:
  - Gecka Submenu
  - Ninja Forms

- SMTP
  - install this plugin so we don't have to configure sendmail, postfix and waste time
  - https://wp-ecommerce.net/easy-wordpress-smtp-send-emails-from-your-wordpress-site-using-a-smtp-server-2197

#### 4.1.4 Theme

- Aparência > Temas
  - select Infocards, and click "Ativar"
- Aparência > Menus > Editar Menus
  - "Selecionar um menu para editar: sitemap, "Selecionar"
  - check "	Automatically populate with child pages" on the menus 2 to 4
- Aparência > Menus > Gerenciar Posições
  - Menu Principal = header, "Salvar Alterações"

#### 4.1.5 Contact Form

- Formulários > Importar / Exportar
  - use the file "contact-form-export/contato" from the git repository
    - "Importar Formulário"
- Formulários > Todos os Formulários
  - note down the form id
- /wp-admin/theme-editor.php?file=footer.php&theme=infocards
  - replace the id in the line: ``` ninja_forms_display_form( 3 ); ```
