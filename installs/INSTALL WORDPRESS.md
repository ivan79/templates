# Instalación de un Wordpress

0) Conectar a VPN para entrar en el ftp, si es necesario

1) Descargar Wordpress de la web: http://wordpress.org
2) Subir el contenido de la carpeta wordpress al ftp

3) Descargar Pods de la web: https://wordpress.org/plugins/pods/
4) Subir la carpeta pods a la carpeta plugins del ftp

5) Subir los plugins wpml-string-translation y sitepress-multilingual-cms (de pago) a la carpeta plugins del ftp

6) Acceder a /wp-admin/setup-config.php y seguir los pasos (se accede poniendo el dominio directamente)
7) Rellenar los campos de la base de datos con los recibidos por mail. En Table Prefix poner wp_nombredeproyecto_ y acabado en _
Si al hacer submit no tiene acceso de escritura a wp-config.php, renombrar wp-config-sample.php a wp-config.php y pegar lo que sale en el asistente. Subir el fichero y seguir con el asistente
8) Rellenar los datos de wordpress 

9) Loginarse y activar los plugins (pods, wpml-string-translation y sitepress-multilingual-cms)

# Customización del theme

1) Generar el tema base con http://underscores.me/ poniendo el nombre del proyecto

2) Customizar Bootstrap (http://getbootstrap.com/), para adaptar los cortes del proyecto: http://getbootstrap.com/customize/

- En Media Queries Breakpoints http://getbootstrap.com/customize/#media-queries-breakpoints hay que definir los tamaños de cada corte (@screen-xs, @screen-sm, @screen-md, @screen-lg y @screen-xs-max)
- En Grid System http://getbootstrap.com/customize/#grid-system hay que ajustar el grid para quitar el tamaño que deja entre columnas (@grid-gutter-width) a 0.
- En Container Sizes http://getbootstrap.com/customize/#container-sizes hay que cambiar los tamaños con los definidos en el Media Queries Breakpoints (@container-tablet, @container-desktop y @container-large-desktop).

Descargar el fichero y subir la carpeta a que hay en el zip a una carpeta LIBS creada en el tema

> Una vez hecho esto ya se puede vincular con nuestro proyecto Wordpress:
http://www.wpmice.com/integrate-underscores-starter-theme-with-twitter-bootstrap-3/

- Editar el fichero functions.php y añadir a la rutina nombredeproyecto_scripts las dos líneas siguientes (al principio):
    wp_enqueue_style( 'bootstrap', get_template_directory_uri() . '/libs/bootstrap/css/bootstrap.min.css');
    wp_enqueue_script( 'bootstrap-js', get_template_directory_uri() . '/libs/bootstrap/js/bootstrap.min.js', array('jquery'), '', true );

- Comentar las líneas:
	wp_enqueue_script( 'XXXXXX-navigation', get_template_directory_uri() . '/js/navigation.js', array(), '20120206', true );
	wp_enqueue_script( 'XXXXXX-skip-link-focus-fix', get_template_directory_uri() . '/js/skip-link-focus-fix.js', array(), '20130115', true );

Borrar todo el contenido del style.css (menos la cabecera de comentarios)

3) Descargar Font-awesome (http://fortawesome.github.io/Font-Awesome/)
Descomprimir y eliminar las carpetas que no sean CSS y FONTS
Subir la carpeta a LIBS

- Editar el fichero functions.php y añadir a la rutina nombredeproyecto_scripts la línea:
	wp_enqueue_style( 'font-awesome', get_template_directory_uri() . '/libs/font-awesome/css/font-awesome.min.css');

4) Dejar la escructura del header.php (por debajo de div id=page) como sigue:

    <div id="page" class="hfeed site">
		
	<div class="container">
    
   <header id="masthead" class="site-header" role="banner">
    <div class="site-branding">
        <h1 class="site-title"><a href="<?php echo esc_url( home_url( '/' ) ); ?>" rel="home"><?php bloginfo( 'name' ); ?></a></h1>
        <h2 class="site-description"><?php bloginfo( 'description' ); ?></h2>
    </div><!-- .site-branding -->
    <nav class="navbar navbar-default">

            <nav id="site-navigation" class="main-navigation" role="navigation">
                <button class="menu-toggle" aria-controls="menu" aria-expanded="false"><?php _e( 'Primary Menu', 'telfast' ); ?></button>
                <?php wp_nav_menu( array( 'theme_location' => 'primary' ) ); ?>
            </nav><!-- #site-navigation -->

     </nav>
	 </header><!-- #masthead -->     
    
	<div id="content" class="site-content">

5) En footer.php añadir </div> encima del div correspondiente a page