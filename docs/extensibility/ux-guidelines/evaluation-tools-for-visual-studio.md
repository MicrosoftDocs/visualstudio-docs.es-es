---
title: "Herramientas de evaluaci&#243;n de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# Herramientas de evaluaci&#243;n de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Lista de comprobación de artesanía para Visual Studio  
 Utilice esta lista de comprobación para evaluar la calidad de la experiencia de usuario de visual y la interacción.  
  
### Información general  
  
-   Compruebe que todos los comandos dan como resultado los comentarios que se indica a los usuarios que se han efectuado sus comandos.  
  
-   Compruebe que todos los elementos de interfaz de usuario y los controles están visibles en todos los temas y en modo de contraste alto.  
  
-   Compruebe que siempre se diferencian selección inactiva y activa, tanto en modo de contraste alto y estándar.  
  
-   Compruebe que foco siempre está visible y aparente.  
  
### Rendimiento  
  
-   Compruebe que algún tipo de "ocupado" indicador se muestra si un comando tiene más de un segundo en completarse.  
  
-   Compruebe que si un comando tarda más de 10 segundos en completarse, una barra de progreso explícita, ya sea determinada \(preferido\) o indeterminado, se muestra.  
  
### Texto de la interfaz de usuario  
  
-   Compruebe que todas las etiquetas de título o frase y que ningún texto es totalmente en minúsculas.  
  
    ||Corregir|Incorrecto|  
    |-|--------------|----------------|  
    |**Texto de comando \(todos\)**|Oración:<br /><br /> **Nombre de directorio:**|Nombre de directorio:|  
    |**Texto del botón \(cliente\)**|Título:<br /><br /> **\[Establecer como predeterminado\]**|VALOR PREDETERMINADO DE SET AS|  
    |**Texto del botón \(en línea\)**|Oración:<br /><br /> **\[Establecer como predeterminado\]**||  
  
-   Compruebe que todas las etiquetas, excepto los encabezados de grupo y los botones, terminan con un signo de dos puntos y preceden el control con el que están emparejadas.  
  
-   Compruebe que los botones, comandos y vínculos de comando que inicia la interfaz de usuario para capturar la entrada del usuario finalización en los puntos suspensivos **\[...\]**.  
  
     Ejemplos:  
  
    -   Un **\[avanzadas...\]** botón en un cuadro de diálogo.  
  
    -   Las opciones de comando en el menú Herramientas \(**Herramientas \> opciones**\) no se debe obtener puntos suspensivos, como iniciar el cuadro de diálogo es la intención del comando.  
  
-   Compruebe que la interfaz de usuario no contiene ningún abreviaturas, excepto los términos estándar del sector. Por ejemplo, HTML ni TCP\/IP necesario deletreado, aunque deben OOM \(memoria insuficiente\) y PII \(información de identificación personal\).  
  
### Acceso mediante el teclado  
  
-   Compruebe que hay una manera de realizar cada tarea con el teclado. Generalmente, esto se logra a través del acceso de teclado para cada control, pero algunas áreas altamente visual, es aceptable una solución como ir a vista de código.  
  
-   Compruebe que puede cambiar a través de controles en un orden lógico \(de izquierda a derecha y de arriba a abajo\). Aunque esto es una práctica recomendada para la mayoría de los controles, no todos los controles requieren este enfoque. Por ejemplo, compruebe que los controles están en un grupo con una sola tabulación de botón de radio.  
  
-   Compruebe que todos los controles tengan etiquetas y que cada etiqueta tiene una tecla de acceso \(excepciones incluyen algunos controles no etiquetados que podrían seguir un control con la etiqueta en la ficha\).  
  
-   Compruebe que no hay ningún conflicto de tecla de acceso.  
  
### Fuentes  
  
-   Compruebe que todas las fuentes \(cara, tamaño, color\) se utilizan de forma coherente y mantienen la jerarquía.  
  
-   Compruebe que todos los elementos de interfaz de usuario usa el servicio de fuente del entorno. \(Consulte [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)\)  
  
     Para comprobar si se está utilizando el servicio, vaya a **Herramientas \> Opciones \> fuentes y colores**. En la lista desplegable Configuración, Elegir fuente del entorno y cambie la fuente a algo asimilar diferente \(como Harrington o cómic SAN\) y establezca el tamaño en 12 pt. A continuación, haga clic en Aceptar. Es posible que deba reiniciar el IDE, pero la mayoría de la interfaz de usuario cambiará inmediatamente. Las áreas que no refleje el cambio de fuente, incluso en el reinicio no están utilizando la fuente del entorno.  
  
-   Compruebe que las fuentes que están derivado del servicio \(por ejemplo, texto en negrita o ampliado\) conservan su tamaño y el formato en relación con el texto "normal", cuando se cambia el tamaño de fuente del entorno.  
  
-   Compruebe que no hay ningún error de recorte debido a las fuentes ampliadas. Fuentes que recortan probablemente son el resultado de los controles de alto fijo o contenedores de alto fijo.  
  
### Cuadros de diálogo  
  
-   Compruebe que el título del cuadro de diálogo es el mismo que el comando que se inició.  
  
-   Compruebe que todos los controles estándares sean coherentes con el sistema operativo: color de fondo es estándar y no los controles deben tener un estilo de plantilla re especial que hace que se muestren diferentes de los controles estándares.  
  
-   Compruebe que los márgenes dentro del formulario deben ser de 12 píxeles y deben aparecer coherente y uniforme.  
  
-   Compruebe que los cuadros de diálogo aparecen centrados dentro del shell IDE o la ventana que se generó.  
  
-   Cuando es útil, puede cambiar el tamaño los cuadros de diálogo. Para cuadros de diálogo que se puede cambiar el tamaño, compruebe que al cambiar el tamaño, los controles adecuados deben cambiar de tamaño mientras que otras partes del cuadro de diálogo permanezcan constantes.  
  
-   Compruebe que los diálogos redimensionables conservan cualquier tamaño ajustado por el usuario \(tamaño, ubicación, expansión de controles de cuadro de diálogo etc.\).  
  
-   Compruebe que no hay ningún icono en la barra de título.  
  
-   Compruebe que no hay ningún botón de minimizar y maximizar en la barra de título.  
  
#### Botones de operación del cuadro de diálogo \(sólo cliente de VS\)  
  
-   Compruebe que los botones están en este orden: **Aceptar**, **Cancelar**, **aplicar**.  
  
-   Compruebe que **Aceptar** y **Cancelar** botones son el tamaño estándar: 23 x 75 píxeles.  
  
-   Compruebe que **Aceptar** y **Cancelar** botones son del mismo tamaño, independientemente de la longitud de la cadena.  
  
-   Si la etiqueta de un botón de la operación requiere el botón sea más ancha que estándar, compruebe que el correspondiente **Cancelar** botón es del mismo tamaño.  
  
-   Compruebe que hay un relleno de 6 píxeles entre los botones y controles asociados.  
  
-   Compruebe que la **Aceptar** y **Cancelar** botones no tienen teclas de acceso definida por una letra subrayada.  
  
-   Compruebe que un botón \(normalmente **Aceptar**\) tiene el foco de forma predeterminada.  
  
-   Compruebe que **Esc** cancela el cuadro de diálogo  
  
-   Compruebe que **ENTRAR** ejecuta el botón predeterminado si el foco no está en un control que procesa ENTRAR.  
  
-   Compruebe que la **Aceptar** y **Cancelar** botones se colocan en la esquina inferior derecha del cuadro de diálogo. En raras excepciones, es aceptable se apilan verticalmente en la esquina superior derecha.  
  
-   Compruebe que la configuración vertical se usa sólo si otros botones que se encuentran en una alineación horizontal en el cuadro de diálogo.  
  
### Estándares de control  
  
#### General  
  
-   Compruebe que, cuando sea posible, hay buenos valores predeterminados para acelerar la interacción del usuario y dirigir a los usuarios hacia un resultado seguro o comunes.  
  
-   Compruebe que los controles estándar comportan de la misma manera para que los usuarios sepan lo que ocurrirá según la experiencia anterior.  
  
#### Controles de etiqueta  
  
-   Compruebe que cada control tiene una etiqueta y que cada etiqueta visualmente se empareja con su control \(generalmente dentro de un intervalo de 4 a 6 píxeles\) y está más cerca de su control correspondiente que a otros controles.  
  
-   Compruebe que las etiquetas se colocan vaciar izquierda con el control si situado por encima del borde izquierdo y se centra horizontalmente, para que la línea de base de la etiqueta se alinea con la línea base del texto de entrada si situado a la izquierda.  
  
-   Compruebe que si se colocan varias etiquetas apiladas y controles de entrada a la izquierda de un control, las etiquetas de alineación están a la izquierda y misma distancia desde el borde del cuadro de diálogo, nunca vaciar derecha y la misma distancia desde los controles. Pares deben distribuirse uniformemente a menos que necesita espacio adicional para indicar la agrupación.  
  
#### Controles de entrada \(cuadros de texto y cuadros combinados\)  
  
-   Compruebe que cuando se utiliza la fuente del entorno de forma predeterminada, el alto de los cuadros de texto, cuadros combinados y botones son todos los píxeles de 23.  
  
-   Si se utiliza el texto de la sugerencia, compruebe que el color esté establecido en `Environment.ControlEditHintText` con el servicio de color.  
  
-   Si el campo es un campo obligatorio que debe identificarse como tal, compruebe:  
  
    -   que el fondo se establece en `Environment.ControlEditRequiredBackground` y en primer plano `Environment.ControlEditRequiredHintText`  
  
    -   que hay texto de sugerencia en el control que aparece como **"\<" requiere \>**  
  
#### Controles de botón  
  
-   Compruebe que los botones sean un tamaño mínimo de 23 x 75 píxeles, a menos que satisfaga la longitud del texto.  
  
-   Compruebe que los botones quedan y márgenes de 3 a 5 píxeles, así como relleno para el contenido de la derecha.  
  
-   Es aceptable usar un botón pequeño cuadrado con solo puntos suspensivos **\[...\]** en ella en lugar de un **\[Examinar...\]** botón \(o una funcionalidad similar\). Si utiliza esta opción, compruebe que el botón es 23 x 23 de tamaño.  
  
-   Si hay más de un **\[Examinar...\]** botón en un cuadro de diálogo, a continuación, compruebe que la versión abreviada \(solo puntos suspensivos **\[...\]**\) se utiliza para todos.  
  
-   Compruebe que puntos suspensivos **\[...\]** botones no tienen una tecla de acceso. Cuando el foco está en el control de entrada junto a ella, una pestaña debe mover el foco en el botón de puntos suspensivos.  
  
-   Compruebe que los botones, comandos y vínculos de comando que inicia la interfaz de usuario secundaria que captura la entrada de usuario más deben finalizar en los puntos suspensivos **\[...\]**.  
  
#### Hipervínculos  
  
-   Compruebe que un control hyperlink nunca parpadea rojo cuando está activo. Esto es un indicador de que el servicio de color no se va a utilizar  
  
-   Compruebe que los colores de VS utilizados son:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Compruebe que los hipervínculos aparecen azules con ningún subrayado, a menos que se incrustan en un párrafo.  
  
#### Casillas de verificación  
  
-   Si una casilla de verificación tiene texto de varias líneas, compruebe que la casilla se alinea con la primera línea de texto, no centrado verticalmente en todas las líneas.  
  
-   Compruebe que casillas siempre indican una elección binaria y no el usuario navegue por o abrir nuevas ventanas o páginas.  
  
-   Si una casilla de verificación, se presenta una opción de un control de entrada, compruebe que está colocado vaciar izquierda y muy estrechamente en ese control para indicar a su relación.  
  
-   Compruebe que la casilla de verificación es **nunca** utiliza como un medio para habilitar todo el contenido de un cuadro de diálogo o una página.  
  
#### Cuadros de grupo  
  
-   Compruebe que un cuadro de diálogo no contiene un cuadro de grupo único dentro de él que contiene todo el contenido del cuadro de diálogo.  
  
-   Compruebe que hay al menos dos controles dentro de cada cuadro de grupo.  
  
-   Casi nunca debería haber más de dos cuadros de grupo en un cuadro de diálogo.  
  
-   Compruebe que no hay ningún cuadro de grupo anidado.  
  
### Iconos  
  
-   Compruebe que los iconos aparecen correctamente invertidos en el tema oscuro.  
  
-   Compruebe que todos los iconos se basan en conceptos básicos.  
  
-   Compruebe que cada icono es distinto, fácil de reconocer y no contiene más de dos conceptos \(sin el modificador de estado, lenguaje\).  
  
-   Compruebe que el icono base aparece centrado en el espacio.  
  
-   Compruebe que todos los iconos aparecen legibles en el modo de contraste alto.  
  
-   Compruebe que cualquier color utilizado se alinea con los estándares de uso de color.  
  
-   Compruebe que no hay ninguna \(bordes\) halos alrededor de iconos. \(Si está presente, el halo debe coincidir con el color de fondo de la interfaz de usuario adyacente\).  
  
### Interfaz de usuario táctil  
  
-   Compruebe que los controles interactivos son suficientemente grandes para ser fácilmente touchable: mínimo **píxeles de 23 x 23** de tamaño  
  
-   Compruebe que los controles más usados son al menos **40 por 40 píxeles** de tamaño.  
  
-   Compruebe que los controles interactivos se tienen al menos **5 píxeles de espaciado** entre ellos