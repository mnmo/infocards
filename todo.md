# Geral











# Notas para ambiente de dev

## Desabilitar FTP para atualização/escrita das coisas

- Lembrar de colocar isto no wp-config.php:
```
define('FS_METHOD', 'direct');
```

## Plugins usados

* submenu plugin
  * http://wordpress.org/extend/plugins/gecka-submenu/
* change post order
  * http://wordpress.org/extend/plugins/hofire-post-order-plugins-for-wordpress/
  * http://www.hofire.com/wordpress-plugins/hofire-post-order-plugins-wordpress/
* paginas iniciais feitas para funcionar com o plugin page_generator
  * https://github.com/fczuardi/page_generator
* cache plugin
  * http://wordpress.org/extend/plugins/quick-cache/
  * http://www.primothemes.com/post/product/quick-cache-plugin-for-wordpress/

# Configuracoes necessarias

* permalink deve ser modificado para /%postname%
* desabilitar comentarios
