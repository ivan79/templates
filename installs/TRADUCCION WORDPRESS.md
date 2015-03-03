# Traducción de un Wordpress

1) Substituir las cadenas fijas de cada php por llamadas: <?php echo __(“<LITERAL>”, “<NOMBRE_DE_PROYECTO>”); ?> 
PAGES / HEADER / FOOTER

2) Las líneas sustituidas en el paso anterior deben ir copiadas a un fichero TXT poniendo el fichero PHP del que salen 
Ejemplo:
```
#header.php
Idioma 
Contacto
Área clientes
```

AL REEMPLAZAR LAS CADENAS, EN CASO DE NO TENER FICHERO .PO NI .MO, LOS VALORES QUE SE MOSTRARAN SERAN LOS DEL PRIMER PARAMETRO DEL ECHO

3) Descargar Poedit (http://poedit.net/) 

4) Abrir el Poedit y hacer nuevo desde fichero POT

5) Seleccionar el fichero POT que hay en la carpeta languages del tema generado por underscore

6) Configurar para que genere automaticamente el .mo al guardar

7) Nombrar el fichero "es_ES" o el idioma que pertoque

8) Guardar los cambios y se habra generado el fichero .po y .mo

9) Editar el fichero .po con un editor de texto (textmate). Se pueden eliminar todas las entradas (respetar la cabecera)

10) Incluir cada entrada del fichero de texto obtenido en el paso 1 y 2 con el siguiente formato:
```
#header.php
msgid "Idioma"
msgstr "Idioma"
```
11) Guardar el fichero .po

12) Abrir el fichero con Poedit y guardar

13) Subir los ficheros .po y .mo al servidor


