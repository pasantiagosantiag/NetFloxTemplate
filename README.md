# Práctica CSS. Módulo LMSGI



## Introducción

En esta práctica se va a desarrollar un sitio web con la finalidad de aprender las características de CSS. Se trata de diseñar un sitio "resposie"  adaptable a distintos tamaños de pantalla.

## Objetivos

1. Definir reglas CSS, usando los diferentes tipos de selectores, para aplicarlos a las diferentes etiquetas del HTML.
2. Usar en las reglas CSS variables y funciones.
3. Comprender, aplicar y modificar el modelo de cajas.
4. Utilizar unidades de medida, tanto absolutas como relativas.
5. Usar transformaciones, transiciones y animaciones.
6. Establecer diferentes diseños para diferentes tamaños de pantalla.
7. Seleccionar y utilizar los diferentes contenedores que proporciona CSS.

## Preparando el entorno

- **La práctica se realiza por parejas**
- Se da libertad para seleccionar el IDE.
- Se ha de crear un repositorio en GitHub y añadir como colaboradores a: Compañero/a, rgmf (Román Martínez) y pasantiagosantig (Pedro Antonio)
- La entrega se realizará para LMSGI en Aules y para ED en el propio GitHub en la fecha indicada en el Aules del módulo.
  
## Enunciado

Nos han pedido crear un pequeño sitio web  para una empresa que pretende ofrecer vídeo bajo demanda, al estilo de Netflix, Amazon Prime o HBO Max. El sitio debe tener un diseño **adaptable** a distintos tamaños de pantalla y proporcionar una experiencia de usuario agradable.

Posee una página principal (index.html), una página de detalles de cada película y una página para la configuración de la cuenta.

## Estructura de directorios

Tal y como se vio en el tema anterior, la carpeta del sitio ha de tener al menos:

- Carpeta css. Contiene los archivos css.
- Carpeta img. Contiene las imágenes del sitio.
- Carpeta js. Contiene los archivos js.
- Fichero index.html.
- Fichero detalle.html.
- Fichero configuracion.html.

## Estructura de la web.

El sitio web se debe ver correctamente en 4 tipos de dispositivos:

 - Compactos, con un ancho de pantalla  máximo de 480px. (móviles)
 - Normal, con un ancho de pantalla con un máximo de 768px. (tablets verticales)
 - Mediano, con un ancho de pantalla de hasta 1024px. (tablets en horizontal)
 - Grande, con un ancho de pantalla mayor de  1024px. (monitor)

Todas las páginas poseen  la misma estructura que dependerá del tipo de dispositivo. 

### Grande 

La página tendra un margen tanto a la izquierda como a la derecha.

En la parte superior se tiene dos barras de navegación:

 - Opciones: situada a la izquerda con las diferentes secciones del sitio:

    - Home
    - Favoritos
    - Novedades
    - Próximos estrenos
   
 - Configuración: situada a la derecha con opciones de configuración:

    - Perfil
    - Buscar  
    - Cerrar sesión

Al pasar el ratón sobre una opción de navegación, se debe cambiar el color de fondo de la opción.
Las barras de navegación se crean usando listas, en el siguiente enlace se puede ver un ejemplo de cómo se crea una lista:
[ W3Schools lista](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_lists_menu). Las opciones de navegación contienen 
además del texto iconos. 
Existen multitud de librerías de iconos, una de ellas es [Boostrap Icons](https://icons.getbootstrap.com/). 
Para incluir esta librería en el sitio, se debe agregar la siguiente etiqueta en el encabezado del sitio:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">

```
    
Por último, en la parte inferior se encuentra el pie de página.	En esta sección se encuentra la información de contacto, el copyright y la lista de redes sociales.
Un ejemplo básico:

```	html

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Grid Layout</title>
    <link rel="stylesheet" href="./css/estructura.css">
   
</head>
<body>
    <div class="grid-container">
        <nav id="barra1">
           barra 1
        </nav>
        <nav id="barra2">
            barra 2
       </nav>
        <main class="main-content">Contenido Principal</main>
       
        <footer class="footer">Pie de Página</footer>
    </div>
</body>
</html>

```
Y el CSS correspondiente:

```css

/* Se aplica a todos los elementos  */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
html{
    /* para ver el diseño de la web, útli para depurar*/
    background-color: red;
}
/* Contenedor principal
ahora se aplica a todos los dispostivos, aunque corresponde al tamaño grande de la pantalla */
.grid-container {
    display: grid;
    grid-template-areas:
        "barra1 barra2"
        "main-content main-content"
        "footer footer";
    grid-template-rows: 10vh 1fr auto; /* Altura: encabezado, contenido flexible, pie */
    grid-template-columns: 5fr 1fr;/*250px 1fr; /* Ancho: barra lateral fija, contenido flexible */
    min-height: 100vh;
    margin-left: 2vh;
    margin-right: 2vh ;
}

/* Estilo para las áreas */
#barra1 {
    grid-area: barra1;
    background-color: #4CAF50;
    color: white;
    text-align: left;
}
#barra2 {
    grid-area: barra2;
    background-color: #f4f4f4;
   
}
.main-content {
    grid-area: main-content;
    background-color: #fff;
    padding: 20px;
}
.footer {
    grid-area: footer;
    background-color: #333;
    color: white;
    text-align: center;
    padding: 10px;
}

```
### Normal

Basada en la grande, pero la barra de navegación de opciones se encuentra en la parte inferior del sitio, y se reduce a Home y Favoritos.
En la parte superior aparece la barra de navegación dos, sin el texto, solo los iconos.

### Mediano

Igual que la grande, pero con las siguientes características:
 - No tiene margen a la izquierda ni a la derecha.
 - La barra de navegación de opciones se encuentra en la parte izquerda del sitio, sin texto.
 - No aparece la barra de navegación de configuración.


### Compacto

Solo aparece una barra de navegación inferior con las opciones de buscar y cerrar sesión, sin texto y el contenido principal.

## Contenido 

Se encuentra dentro de la etiqueta de tipo main, el contenido será diferente dependiendo de si es la principal, detalles o perfíl.

### Página principal

En la página principal han de aparecer, 3 grupos:

- Estrenos.
- Series.
- Películas.

Cada grupo posee una serie de tarjetas con las películas, en la tarjeta aparece:

- La imagen
- El título
- La duración y el año
- La puntuación (con iconos de 0 a 5)

Los requisitos de las tarjetas son:

- Las tarjetas han de tener una sombra de caja, al pasar sobre ellas la sombra ha de cambiar (borde, efecto sombreado...). Recordar el generador de sombras [ MDN Sombras](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_backgrounds_and_borders/Box-shadow_generator)
- Al pasar el ratón sobre la imagen se ha de hacer una transformación, mostrando la sinopsis de la misma.
- La imagen de la tarjeta que se encuentra en la primera posición de la sección ha de hacer una animación, la segunda otra animación, la tercera otra, la cuarta la misma que la primera, la quinta la misma que la segunda, etc.

Se pueden tomar como referencia los siguientes ejemplos:

- [W3Schools tarjetas](https://www.w3schools.com/howto/howto_css_cards.asp)

- [W3Schools tarjetas con animaciones](https://www.w3schools.com/howto/howto_css_flip_card.asp)

- [W3Schools ejemplo tarjeta perfíl](https://www.w3schools.com/howto/howto_css_profile_card.asp)

- [W3Schools ejemplo tarjeta producto](https://www.w3schools.com/howto/howto_css_product_card.asp)

Para que las imágenes se vean todas del mismo tamaño, consultar el siguiente enlace [ W3Schools propiedad object-fit](https://www.w3schools.com/css/css3_object-fit.asp)


### Página detalle

En la página detalle de cada película se encuentra la información de la película, en la parte superior se encuentra el título de la película, la imagen (con una barra simulando los botones de reproducción y pausa en la parte inferior), la duración, la puntuación y la sinopsis, y en la parte
derecha los comentarios, si el número de comentario excede el espacio, ha de ser "scrollable". Los comentarios han de estar numerados de forma automática, usando contadores CSS.

- Si el tamaño es grande  o mediano se muestra en el lateral los comentarios.

- Si la sección es normal no debe aparecer los comentarios.

- Si es compacto solo aparece el título la imagen de la película, y los botones de reproducción.

### Página de perfil

Tienen un formulario con los datos del usuario y con el CSS modificado. Los datos del formulario son:

- Nombre
- Email
- Dirección
- Teléfono
- Contraseña
- Confirmar contraseña

Además de los botones de enviar y cancelar.

## Variables y colores

A lo largo de la práctica se han definido diferentes colores que ayudan al desarrollo (ver áreas, bordes, ajustes...) y otros que forman parte del diseño.
Si en el futuro se cambia la gama de colores, puede ser tedioso realizar este cambio.
Se pide definir la gama de colores en variables y modificar el código.
Existen diferentes páginas que ayudan a definir la gama de colores:

- [Coolors](https://coolors.co/540d6e-f8c7cc-81a684-57886c-ffc857)
- [Colorhunt.co](https://colorhunt.co)

Definir variables para los colores de la web, por ejemplo:

- Principal.
- Secundario.
- Complemento 1
- Complemento 2

Crear variables en un fichero con el valor de los colores seleccionados, y sustituir en el resto del CSS por las variables.

## Evaluación

1. Definir la estructura de forma correcta, usando el modelo de cajas, grif y flex, en las 3 página. **3 puntos**
2. Hacer que el diseño sea "resposive" con los tamaños indicados **2,5 puntos**
3. Implementar las transiciones **1 punto**
4. Crear el formulario con un aspecto similar al del resto de la web **1 punto**
5. Establecer los colores con variables **1 punto**
6. Definir  un contador de comentarios **0,25 puntos**
7. Estructura el css en diferentes ficheros **0,25 puntos**
8. Documentar el código **0,25 puntos**
9.  Usar iconos **0,25 puntos**
10. Aplicar las unidades de medida y funciones de forma correcta **0,5 puntos**

Extra: Realizar el formulario con Boostrap ** (0,75 punto) **, insertar un Carosul de imágenes como cabecera **1,25 puntos**
