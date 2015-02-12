# Migración de Wordpress
¿Cómo migrar una web Wordpress al servidor de producción?

1) Bajar todo el FTP a una carpeta temporal, que esté fuera de la parte de producción.
2) Subir al nuevo FTP, todo, menos wp-config.php (configuración BD), y .htaccess (rutas del permalink)
	2.1) Una vez subido, modificar estos ficheros.
3) Base datos, exportar del mysql orignal desde phpmyadmin: Exportar (Rápido)
	3.1) Vamos al SQL que se ha generado y modificamos las URL de script * Importante, al reemplazar no poner las barras finales:
		3.1.1) Ejemplo: http://miweb.preprod.com reemplazar con http://miweb.produccion.com/xproject
	3.2) Grabar los cambios, y hacer un zip
	3.3) Ir al phpmyadmin de producción, y hacer importar seleccionando el .zip (no hay que modificar ninguna opción)
		3.3.1) Esto puede fallar, porque le falte un USE database, o DROP o algo de eso.
4) Volviendo al punto 2.1, modificamos el wp-config.php
	4.1) Hay que cambiar: bd: DB_NAME, DB_USER, DB_PASSWORD, DB_HOST, no hay que cambiar nada más, a no ser que tengamos DEBUG igual a true, que entonces se pone a FALSE.
	4.2) .htaccess, cambiar RewriteBase+RewriteRule a la carpeta donde esté a partir del dominio, si está en una URL directa sin carpeta se deja la barra (siempre acaba en "/").

5) IMPORTANTE: Una vez subidos todos los ficheros, poner 777 a través del Filezilla a la carpeta uploads (Marcar: Incluir subdirectorios), sino, no irá los uploads.

# Dentro del Admin (una vez revisado que todo funciona)

1) Ir a WPML > Localización de temas y plugins y desactivar la opción Traducir utilizando archivos .mo > Carga el archivo .mo, IMPORTANTE, guardar y volver a ponerlo como estaba (esto es un bug de WPML).
2) Los plugins que utilizan pantallas propias que no son de WORDPRESS, por ejemplo, el Cookie Law Info, aplicar todos los cambios de nuevo. También pasa con los Themes que se compran en envato.
3) Activar Analytics con el código bueno, si no está activo + Intentar a no ser que el proyecto lo necesite activar el "Hide comments" para evitar el Spam.
4) Si se pierden los rewrites (permalink) Ir a por ejemplo /aviso-legal o /contact a) Verificar .htaccess (dentro del generado en Settings > Permalinks ) b) Ir a Settings > Permalinks y Save Changes
5) Importante, avisar de cuando está colgado que cambien el usuario y password.


