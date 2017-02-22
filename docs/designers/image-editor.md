---
title: "Editor de im&#225;genes | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.designer.imageeditor"
  - "vs.graphics.imageeditor"
ms.assetid: fc71d502-c548-4863-8afc-12a1d3ec90d4
caps.latest.revision: 45
caps.handback.revision: 45
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Editor de im&#225;genes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este documento se describe cómo ejecutar el editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Imágenes para ver y modificar recursos de textura e imagen.  
  
 Puede utilizar el Editor de imágenes para trabajar con la clases de textura y formatos de imágenes enriquecidos que se utilizan en el desarrollo de aplicaciones de DirectX, lo que incluye compatibilidad con los formatos de archivo de imagen y las codificaciones de color que más se utilizan, características como los canales alfa y la asignación MIP, y muchos de los formatos de texturas muy comprimidos y acelerados por hardware compatibles con DirectX.  
  
## Formatos compatibles  
 El Editor de imágenes admite estos formatos de imagen:  
  
|Nombre de formato|extensión de nombre de archivo|  
|-----------------------|------------------------------------|  
|Formato PNG \(portable network graphics\)|png|  
|JPEG|.jpg, .jpeg, .jpe, .jfif|  
|Superficie de DirectDraw|.dds|  
|formato de intercambio de gráficos|.gif|  
|Mapa de bits|.bmp, .dib|  
|TIFF|.tif, .tiff|  
|TGA \(Targa\)|.tga|  
  
## Introducción  
 En esta sección se describe cómo agregar una imagen al proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y configurarla para requisitos.  
  
#### Para agregar una imagen al proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual del proyecto al que desee agregar la imagen y, a continuación **Add**, **Nuevo elemento**.  
  
2.  En el cuadro de diálogo de **Agregar nuevo elemento** , en **Instalada**, **Gráficos**seleccione y a continuación, seleccione un formato de archivo adecuado para la imagen.  Para obtener información sobre cómo elegir un formato de archivo basado en los requisitos, vea la sección siguiente.  
  
3.  Especifique **Name** de archivo de imagen, y **ubicación** donde desea que se creará.  
  
4.  Elija el botón de **Agregar**.  
  
### Elegir el formato de imagen  
 Dependiendo de cómo piensa utilizar la imagen, ciertos formatos de archivo pueden ser más adecuados que otros.  Por ejemplo, algunos formatos podrían no admitir una característica que se necesidad\- como transparencia ni color específico formato\- o que no proporcione la compresión adecuado para la clase de contenido de la imagen que ha planeado.  
  
 La información siguiente puede ayudarle a elegir un formato de imagen que cubre las necesidades.  
  
 **Imagen de mapa de bits \(.bmp\)**  
 Formato de imagen de mapa de bits.  Un formato de imagen sin comprimir compatible con colores de 24 bits.  El formato de mapa de bits no admite la transparencia.  
  
 **Imagen GIF \(.gif\)**  
 Formato de imagen GIF \(Formato de intercambio de gráficos\).  Formato de imagen LZW comprimido sin pérdidas que admite hasta 256 colores.  Inapropiado para fotografías e imágenes con una cantidad significativa de detalles de color, pero proporciona buenos índices de compresión para las imágenes de color bajo con un alto nivel de coherencia de color.  
  
 **Imagen JPG \(.jpg\)**  
 Formato de imagen JPEG \(grupo conjunto de expertos en fotografía\).  Un formato de imagen explícita muy comprimida que admite colores de 24 bits y es adecuado para la compresión de uso general de imágenes que tienen un alto nivel de coherencia de color.  
  
 **Imagen PNG \(.png\)**  
 Formato de imagen PNG \(Portable Network Graphics\).  Un formato de imagen de comprensión moderada que no es explícito que admite colores de 24 bits y transparencia alfa.  Es adecuado para las imágenes naturales y artificiales, pero no proporciona índices de compresión tan buenos como los formatos explícitos como JPG o GIF.  
  
 **Imagen TIFF \(.tif\)**  
 Formato de imagen TIFF o TIF \(formato de archivo de imagen etiquetado\).  Formato de imagen flexible que admite varios modelos de compresión.  
  
 **Textura de DDS \(.dds\)**  
 El formato de textura DirectDraw Surface \(DDS\).  Un formato de textura explícito muy comprimido compatible con colores de 24 bits y transparencia alfa.  Los índices de compresión pueden ser tan elevados como 8:1.  Está basado en la compresión de texturas S3, que se puede descomprimir en el hardware para gráficos.  
  
 **Imagen TGA \(.tga\)**  
 El formato de imagen TGA \(Truevision Graphics Adapter\) \(también conocido como Targa\).  Un formato de imagen RLE comprimido sin pérdidas que admite imágenes asignadas a colores \(paleta de colores\) o de color de directo de hasta colores de 24 bits y transparencia alfa.  Inapropiado para fotografías e imágenes con una cantidad significativa de detalles de color, pero proporciona buenos índices de compresión en las imágenes que tienen largos intervalos de colores idénticos.  
  
### Configuración de imagen  
 Antes de empezar a trabajar con la imagen que acaba de crear, puede cambiar la configuración predeterminada.  Por ejemplo, puede cambiar sus dimensiones o formato de color que utiliza.  Para obtener información sobre cómo configurar estas y otras propiedades de imágenes, vea [Propiedades de imágenes](#ImageProperties).  
  
> [!NOTE]
>  Antes de guardar el trabajo, asegúrese de establecer la propiedad de **Formato de color** si desea utilizar un formato de color específico.  Si el formato de archivo admite compresión, puede ajustar los valores de compresión al guardar el archivo por primera vez o cuando se elige **Guardar como**.  
  
## Trabajar con el editor de imágenes  
 Esta sección describe cómo utilizar el editor de Imágenes para modificar texturas e imágenes.  
  
### Barras de herramientas del Editor de imágenes  
 Comandos de las barras de herramientas del Diseñador de imágenes que ayudan a trabajar con imágenes.  
  
 Los comandos que afectan al estado del editor de Imágenes se encuentran en la barra de herramientas de **Modo de editor de imágenes** así como comandos avanzado.  La barra de herramientas se encuentra en el borde superior de la superficie de diseño del editor de imágenes.  Las herramientas de dibujo se encuentran en la barra de herramientas de **Editor de imágenes** a lo largo del borde de izquierda de la superficie de diseño del editor de imágenes.  
  
 A continuación, se muestra la barra de herramientas del **Modo editor de imágenes**:  
  
 ![Barra de herramientas modal del Editor de imágenes.](../designers/media/digit-tre-modal-toolbar.png "Digit\-TRE\-Modal\-Toolbar")  
  
 En esta tabla se describen los elementos de la barra de herramientas del **Modo del editor de imágenes**; se muestran en el orden en que aparecen de izquierda a derecha.  
  
|Elemento de la barra de herramientas|Descripción|  
|------------------------------------------|-----------------|  
|**Seleccionar**|Habilita la selección de un área rectangular de una imagen.  Después de seleccionar una región, puede cortarla, moverla, escalarla, girarla, voltearla o eliminarla.  Si hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|  
|**selección irregular**|Habilita la selección de un área irregular de una imagen.  Después de seleccionar una región, puede cortarla, moverla, escalarla, girarla, voltearla o eliminarla.  Si hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|  
|**Selección de varita**|Habilita la selección de una región coloreada de forma similar de una imagen.  La *tolerancia*, es decir, la diferencia máxima entre colores adyacentes para que se consideren similares, se puede configurar para que incluya un intervalo menor o mayor de colores similares.  Después de seleccionar una región, puede cortarla, moverla, escalarla, girarla, voltearla o eliminarla.  Si hay una selección activa, las herramientas de dibujo solo afectan a la región seleccionada.|  
|**Panorámica**|Habilita el movimiento de la imagen en relación con el marco de la ventana.  En el modo **Movimiento panorámico**, seleccione un punto en la imagen y muévalo.<br /><br /> Puede activar temporalmente el modo **Panorámico** si mantiene presionada la tecla Ctrl.|  
|**Zoom**|Habilita la presentación de más o menos detalle de la imagen en relación con el marco de la ventana.  En el modo de **Zoom** , seleccione un punto de la imagen y muévalo a la derecha o hacia abajo para acercar o a la izquierda o hacia arriba para alejar.<br /><br /> Puede acercar o alejar si mantiene presionada la tecla Ctrl mientras utiliza la rueda del mouse o presiona el signo más \(\+\) o el signo menos \(\-\).|  
|**Zoom al tamaño real**|Muestra la imagen con una relación de 1:1 entre los píxeles de la imagen y los píxeles de la pantalla.|  
|**Zoom para ajustar**|Muestra toda la imagen completa del marco de la ventana.|  
|**Ajustar a ancho**|Muestra el ancho total de la imagen en el marco de la ventana.|  
|**Grid**|Habilita o deshabilita la cuadrícula que muestra límites de píxeles.  La cuadrícula puede no aparecer hasta que se haga zoom en la imagen.|  
|**Ver nivel de MIP siguiente**|Eleva el nivel mayor siguiente MIP en una cadena de asignación MIP.  El nivel de MIP de activo se muestra en la superficie de diseño.  Este elemento solo está disponible para las texturas que tienen niveles MIP.|  
|**Ver nivel de MIP anterior**|Eleva el nivel más pequeño siguiente MIP en una cadena de asignación MIP.  El nivel de MIP de activo se muestra en la superficie de diseño.  Este elemento solo está disponible para las texturas que tienen niveles MIP.|  
|**Canal rojo**<br /><br /> **Canal verde**<br /><br /> **Canal azul**<br /><br /> **Canal alfa**|Habilita o deshabilita el canal en color específico. **Note:**  Al habilitar o deshabilitar sistemáticamente los canales de color, puede aislar los problemas relacionados con uno o varios de ellos.  Por ejemplo, podría identificar la transparencia alfa incorrecta.|  
|**Fondo**|Habilita o deshabilita la visualización del segundo plano en las partes transparentes de la imagen.  Puede configurar el modo en que se muestra el fondo eligiendo entre estas opciones:<br /><br /> **Tablero**<br /> Utiliza el color verde junto con el color de fondo especificado para mostrar el fondo como un patrón de tablero.  Puede utilizar esta opción para ayudar a crear partes transparentes de la imagen más evidentes.<br /><br /> Fondo blanco<br /> Utiliza el color blanco para mostrar el fondo.<br /><br /> Fondo negro<br /> Utiliza el color negro para mostrar el fondo.<br /><br /> Animar fondo<br /> Realiza un movimiento panorámico lento sobre el tablero.  Puede utilizar esta opción para ayudar a crear partes transparentes de la imagen más evidentes.|  
|**Propiedades**|Como alternativa abre o cierra la ventana **Propiedades**.|  
|**Avanzado**|Contiene comandos adicionales y opciones.<br /><br /> **Filtros**<br /><br /> Proporciona varios filtros comunes de imagen: **Blanco y negro**, **Desenfoque**, **Iluminar**, **Oscurecer**, **Detección de bordes**, **Relieve**, **Invertir colores**, **Ondas**, **Tono sepia** y **Enfocar**.<br /><br /> **Motores gráficos**<br /><br /> **Presentación con D3D11**<br /> Utiliza Direct3D 11 para presentar la superficie de diseño del Editor de imágenes.<br /><br /> **Representar con D3D11WARP**<br /> Utiliza Windows Advanced Rasterization Platform \(WARP\) de Direct3D 11 para presentar la superficie de diseño del Editor de imágenes.<br /><br /> **Herramientas**<br /><br /> **Voltear horizontalmente**<br /> Transpone la imagen alrededor de su horizontal, o x, eje.<br /><br /> **Voltear verticalmente**<br /> Transpone la imagen alrededor del vertical, o la y, eje.<br /><br /> **Generar Mips**<br /> Genera los niveles de MIP para una imagen.  Si ya existen niveles de MIP, se vuelven a crear a partir del nivel de MIP superior.  Se pierde cualquier cambio realizado en niveles MIP más pequeños.  Para guardar los niveles MIP que ha generado, debe utilizar el formato .dds para guardar la imagen.<br /><br /> **View**<br /><br /> **Velocidad de fotograma**<br /> Cuando está habilitada, muestra la velocidad de fotograma en la esquina superior derecha de la superficie de diseño.  La velocidad de fotograma es el número de marcos dibujados por segundo. **Tip:**  Puede elegir el botón **Avanzadas** para volver a ejecutar el último comando.|  
  
 Esta es la barra de herramientas del **Editor de imágenes**.  
  
 ![Barra de herramientas del Editor de imágenes](../designers/media/digit-tre-toolbar.png "Digit\-TRE\-Toolbar")  
  
 La tabla siguiente describe los elementos de la barra de herramientas del **Editor de imágenes**, que se muestran en el orden en que aparecen de arriba abajo.  
  
|Elemento de la barra de herramientas|Descripción|  
|------------------------------------------|-----------------|  
|**Lápiz**|Utiliza la selección de color activo para dibujar un trazo con alias.  Puede establecer el color y el grosor del trazo en la ventana de **Propiedades** .|  
|**Pincel**|Utiliza la selección de color activo para dibujar un trazo con suavizado.  Puede establecer el color y el grosor del trazo en la ventana de **Propiedades** .|  
|**Aerógrafo**|Utiliza la selección de color activo para dibujar un trazo con suavizado que se combina con la imagen y se satura más en función de tiempo.  Puede establecer el color y el grosor del trazo en la ventana de **Propiedades** .|  
|**Cuentagotas**|Establece la selección de color según el color de píxel seleccionado.|  
|**Fill**|Utiliza la selección de color activo para rellenar un área de la imagen.  La región afectada se define como el píxel donde se aplica el relleno, junto con cada píxel que esté conectado a él por píxeles del mismo color y que sea también del mismo color.  Si el relleno se aplica dentro de un selección activa, la región afectada queda restringida por la selección.<br /><br /> De forma predeterminada, la selección de color activo se mezcla junto con la región afectada de la imagen según su componente alfa.  Para utilizar la selección de color activo para sobrescribir la región afectada, presione y mantenga presionada la tecla Mayús al utilizar la herramienta Rellenar.|  
|**Borrador**|Establece los píxeles totalmente el color transparente si la imagen admite un canal alfa.  Si no, establece los píxeles al color de fondo activo.|  
|**Línea**, **Rectángulo**, **Rectángulo redondeado**, **Elipse**|Dibuja una forma de la imagen.  Puede establecer el color y el grosor del contorno de la ventana de **Propiedades** .<br /><br /> Para dibujar una primitiva con el mismo ancho que alto, presione y mantenga presionada la tecla Mayús mientras dibuja.|  
|**Texto**|Utiliza la selección de color de primer plano para dibujar el texto.  El color de fondo está determinado por la selección de color de fondo.  Para obtener un fondo transparente, el valor alfa de la selección del color de fondo debe ser 0.  Mientras el área de texto está activo, puede establecer si el texto se dibuja con un trazo anti\- con alias, y establecer el texto **Valor**, **font**, **Tamaño**, y estilo**Bold**, **Cursiva**, o **Subrayado**— en la ventana de **Propiedades** .  El contenido y el aspecto del texto se finalizan cuando el área de texto ya no está activa.|  
|**Girar**|Rota la imagen 90 grados en el sentido de las agujas del reloj.|  
|**Trim**|Ajusta la imagen a la selección activa.|  
  
### Trabajar con niveles MIP  
 Algunos formatos de imágenes, como DirectDraw Surface \(.dds\), admiten niveles MIP para el nivel de detalle \(LOD\) del espacio de textura.  Para obtener información sobre cómo se generan y se trabaja con niveles MIP, vea [Cómo: Crear y modificar niveles de MIP](../designers/how-to-create-and-modify-mip-levels.md)  
  
### Trabajar con la transparencia  
 Algunos formatos de imágenes, por ejemplo DirectDraw Surface \(.dds\), admiten la transparencia.  Hay varias formas de transparencia que se pueden utilizar, dependiendo de la herramienta que se esté utilizando.  Para especificar el nivel de transparencia para una selección de color, en la ventana **Propiedades**, establezca el componente **A** \(alfa\) de la selección de color.  Aquí se muestra cómo los diferentes tipos de herramientas controlan cómo se aplica la transparencia:  
  
|Herramienta|Descripción|  
|-----------------|-----------------|  
|**Lápiz**, **Pincel**, **Aerógrafo**, **Línea**, **Rectángulo**, **Rectángulo redondeado**, **Elipse**, **Texto**|Para mezclar la selección de color activa con la imagen, en la ventana **Propiedades**, expanda el grupo de propiedades **Canales** y active la casilla **Dibujar** del canal **Alpha** y, a continuación, dibuje normalmente.<br /><br /> Para dibujar mediante la selección de color activo y dejar el valor alfa de la imagen como está, desactive la casilla **Dibujar** del canal **Alpha**, y después dibuje normalmente.|  
|**Fill**|Para mezclar la selección de color activa así con la imagen, simplemente elija el área que desea rellenar.<br /><br /> Para utilizar la selección de color activo, incluyendo el valor del canal alfa, para sobrescribir la imagen, presione y mantenga presionada la tecla Mayús y elija el área que desea rellenar.|  
  
###  <a name="ImageProperties"></a> Propiedades de imágenes  
 Puede utilizar la ventana de **Propiedades** para especificar varias propiedades de la imagen.  Por ejemplo, puede establecer las propiedades width y height para cambiar el tamaño de la imagen.  
  
 La tabla siguiente describe las propiedades de la imagen.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|Ancho|Ancho de la imagen.|  
|Alto|Alto de la imagen.|  
|Bits por píxel|El número de bits que representan cada píxel.  El valor de esta propiedad depende del valor del **Formato de color** de la imagen.|  
|Selección transparente|**True** para combinar el nivel de selección junto con la imagen principal, según el valor alfa del nivel de selección; si no, **FALSE**.  Este elemento solo está disponible para las imágenes que admiten alfa.|  
|Formato|Formato de color de la imagen.  Diversos formatos de colores se pueden especificar, dependiendo del formato de la imagen.  El formato de color define el número y tipo de los canales de color que se incluyen en la imagen, y también el tamaño y la codificación de diferentes canales.|  
|Nivel MIP|El nivel de MIP activo.  Este elemento solo está disponible para las texturas que tienen niveles MIP.|  
|Recuento de nivel MIP|Número total de elementos MIP en la imagen.  Este elemento solo está disponible para las texturas que tienen niveles MIP.|  
|Número de fotogramas|Número total de marcos en la imagen.  Este elemento solo está disponible para las imágenes que admiten las matrices de textura.|  
|Marco|Marco actual.  Solo el primer marco puede verse; el resto se pierde cuando se guarda la imagen.|  
|Recuento de segmentos de profundidad|Número total de segmentos de profundidad en la imagen.  Este elemento solo está disponible para las imágenes que admiten texturas de volumen.|  
|Segmento de profundidad|El segmento de profundidad actual.  Solo el primer segmento puede verse; el resto se pierde cuando se guarda la imagen.|  
  
> [!NOTE]
>  Dado que la propiedad de **Girar** se aplica a todas las herramientas y regiones seleccionado, siempre aparece en la parte inferior de la ventana de **Propiedades** así como otras propiedades de la herramienta.  **Girar** se muestra siempre porque toda la imagen se selecciona implícitamente cuando no hay otra herramienta de selección o activa.  Para obtener más información sobre la propiedad de **Girar** , vea [Propiedades de la herramienta](#ToolProperties).  
  
#### Cambiar el tamaño de las imágenes  
 Estos son dos maneras de cambiar el tamaño de una imagen.  En ambos casos, el Editor de imágenes usa una interpolación bilineal para volver a muestrear la imagen.  
  
-   En la ventana **Propiedades**, especifique nuevos valores para las propiedades **Ancho** y **Alto**.  
  
-   Seleccione la imagen completa y usan marcadores de borde para cambiar el tamaño de la imagen.  
  
### Trabajar con herramientas  
  
#### Regiones seleccionadas  
 Las selecciones en el Editor de imágenes definen las regiones de la imagen que están activas, es decir, las que se verán afectadas por las herramientas y las transformaciones.  Si hay una selección activa, las áreas de fuera de la región seleccionado no se ven afectadas por la mayoría de las herramientas y las transformaciones.  Si no hay una selección activa, toda la imagen está activa.  
  
 La mayoría de las herramientas**Lápiz**, **Pincel**, **Aerógrafo**, **Relleno**, **Borrador**, y 2d primitivo\- y transformaciones**Girar**, **Ajuste**, **Invertir colores**, **Voltear horizontalmente**, y **Voltear verticalmente**— se restringida o definidas por la selección activa.  Sin embargo, algunas herramientas, **Cuentagotas** y **Texto**, y transformaciones, **Generar Mips**, no se ven afectadas por ninguna selección activa; estas herramientas siempre se comportan como si la imagen en su totalidad es la selección activa.  
  
 Mientras está seleccionando una región, puede presionar y mantener presionada la tecla Mayús para crear una selección proporcional \(cuadrada\); si no lo hace, la selección no tendrá ninguna restricción.  
  
##### Cambiar el tamaño de selecciones  
 Después de seleccionar una región, puede cambiar su tamaño el contenido de su imagen cambiando el tamaño del marcador de selección.  Mientras está cambiando el tamaño del área seleccionada, puede utilizar las teclas modificadoras siguientes para cambiar el comportamiento de la región seleccionado como se cambia el tamaño \(presione y mantenga presionada la tecla mientras se cambia el tamaño\).  
  
 Ctrl  
 Copia el contenido de la región seleccionada antes de que haya cambia de tamaño.  Esto deja de la imagen original intacta cuando se cambia el tamaño de la copia.  
  
 Shift  
 Cambia el tamaño de la región seleccionado en proporción a su tamaño original.  
  
 Alt  
 Cambia el tamaño del área de selección.  Esto deja de imagen sin modificar.  
  
 Éstas son las combinaciones de tecla modificadora válidas:  
  
|Ctrl|Shift|Alt|Descripción|  
|----------|-----------|---------|-----------------|  
||||Cambiar el tamaño del contenido de la región seleccionada.|  
||Shift||Cambiar el tamaño proporcionalmente del contenido de la región seleccionada.|  
|||Alt|Cambia el tamaño de la región seleccionada.  Esto define una nueva área de selección.|  
||Shift|Alt|Cambia el tamaño proporcionalmente del área seleccionada.  Esto define una nueva área de selección.|  
|Ctrl|||Copia y después cambia el tamaño del contenido de la región seleccionada.|  
|Ctrl|Shift||Copias y después cambian el tamaño proporcionalmente del contenido de la región seleccionada.|  
  
####  <a name="ToolProperties"></a> Propiedades de la herramienta  
 Cuando se selecciona una herramienta, puede utilizar la ventana de **Propiedades** para especificar los detalles sobre cómo afecta a la imagen.  Por ejemplo, puede establecer el grosor de la herramienta **Lápiz** o el color de la herramienta **Pincel**.  
  
 Puede establecer un color de primer plano y un color de fondo.  Ambos admiten un canal alfa que proporciona opacidad definida por el usuario.  Los valores se aplican a todas las herramientas.  Si usa un mouse, el botón primario corresponde al color de primer plano y el botón secundario del mouse corresponde al color de fondo.  
  
 En la tabla siguiente se describen las propiedades de la herramienta.  
  
|Herramienta|Propiedades|  
|-----------------|-----------------|  
|Todas las herramientas y las selecciones|**Girar**<br /> Define la cantidad, en grados, que la selección o el efecto de la herramienta está activada en la dirección a la derecha.|  
|**Lápiz**, **Pincel**, **Aerógrafo**, **Borrador**|**Thickness**<br /> Define el tamaño del área que se ve afectada por la herramienta.|  
|**Texto**|**Suavizado de contorno**<br /> Dibuja texto que tiene bordes con suavizado.  Esto proporciona al texto una apariencia más suave.<br /><br /> **Valor**<br /> Texto que se va a dibujar.<br /><br /> **Fuente**<br /> Fuente usada para dibujar el texto.<br /><br /> **Size**<br /> Tamaño del texto.<br /><br /> **Negrita**<br /> Hace que la fuente tenga formato de negrita.<br /><br /> **Cursiva**<br /> Hace que la fuente tenga formato de cursiva.<br /><br /> **Subrayado**<br /> Subraya la fuente.|  
|**Tipos primitivos 2\-D**|**Suavizado de contorno**<br /> Dibuja primitivos que tienen bordes con suavizado.  Esto les da una apariencia más suave.<br /><br /> **Thickness**<br /> Define el grosor de la línea que forma el límite de primitivo.<br /><br /> **Radio X**<br /> \(Solo rectángulo redondeado\) define el radio de redondeo para los bordes superior e inferior del primitivo.<br /><br /> **Radio Y**<br /> \(Solo rectángulo redondeado\) define el radio de redondeo para los bordes izquierdo y derecho del primitivo.|  
|**Lápiz**, **Pincel**, **Aerógrafo**, **Primitivo 2D**|**Canales**<br /> Habilita o deshabilita canales de color específicos para ver y para dibujar.  Si **Ver** se establece en un canal de color específico, ese canal está visible en la imagen; de lo contrario, no lo estará.  Si se establece **Dibujar** para un canal de color específico, ese canal se verá afectado por las operaciones de dibujo; de lo contrario, no.|  
|**Selección de varita**, **Relleno**|**Tolerancia**<br /> Define la diferencia máxima entre colores adyacentes en la que se consideran similares, de forma que menos o más colores similares formarán parte de la región afectada o seleccionada.  De forma predeterminada, el valor es 32, lo que significa que los píxeles adyacentes dentro de 32 sombras \(más claros o más oscuros\) del color original se considerarán que son parte de la región.|  
  
## Métodos abreviados de teclado  
  
|Command|Métodos abreviados de teclado|  
|-------------|-----------------------------------|  
|Cambiar al modo **Seleccionar**|S|  
|Cambiar al modo **Zoom**|Z|  
|Cambiar al modo **Movimiento panorámico**|K|  
|Seleccionar todo|Ctrl\+A|  
|Eliminar la selección actual.|Delete|  
|Cancelar la selección actual|Escape|  
|Acercar|Ctrl\+rueda del mouse hacia delante<br /><br /> Ctrl\+Retroceso de página \(RePág\)<br /><br /> Signo más \(\+\)|  
|Alejar|Ctrl\-rueda del mouse hacia atrás<br /><br /> Ctrl\-AvPág<br /><br /> Signo menos \(\-\)|  
|Movimiento panorámico de la imagen hacia arriba|Rueda del mouse hacia atrás<br /><br /> AvPág|  
|Movimiento panorámico de la imagen hacia abajo|Rueda del mouse hacia delante<br /><br /> RePág|  
|Movimiento panorámico de la imagen hacia la izquierda|Mayús\+rueda del mouse hacia atrás<br /><br /> Rueda del mouse a la izquierda<br /><br /> Mayús\+AvPág|  
|Movimiento panorámico de la imagen hacia la derecha|Mayús\+rueda del mouse hacia delante<br /><br /> Rueda del mouse a la derecha<br /><br /> Mayús\+RePág|  
|Zoom al tamaño real|Ctrl\+0 \(cero\)|  
|Ajustar la imagen en la ventana|Ctrl\+G, Ctrl\+F|  
|Ajustar imagen al ancho de la ventana|Ctrl\+G, Ctrl\+I|  
|Alternar cuadrícula|Ctrl\+G, Ctrl\+G|  
|Recortar imagen según la selección actual|Ctrl\+G, Ctrl\+C|  
|Ver nivel de MIP siguiente \(más detalles\)|Ctrl\+G, Ctrl\+6|  
|Ver nivel de MIP anterior \(menos detalles\)|Ctrl\+G, Ctrl\+7|  
|Alternar el canal de color rojo|Ctrl\+G, Ctrl\+1|  
|Alternar el canal de color verde|Ctrl\+G, Ctrl\+2|  
|Alternar el canal de color azul|Ctrl\+G, Ctrl\+3|  
|Alternar el canal alfa \(transparencia\)|Ctrl\+G, Ctrl\+4|  
|Alternar el patrón de tablero alfa|Ctrl\+G, Ctrl\+B|  
|Cambiar a la herramienta Selección irregular|L|  
|Cambiar a la herramienta de selección de varita|M|  
|Cambiar a la herramienta de lápiz|P|  
|Cambiar a la herramienta Pincel|B|  
|Cambiar a la herramienta Rellenar|F|  
|Cambiar a la herramienta de borrador|E|  
|Cambiar a la herramienta de texto|T|  
|Cambiar a la herramienta de selección de color \(cuentagotas\)|I|  
|Mueva la selección activa y su contenido.|Teclas de dirección.|  
|Cambiar el tamaño de la selección activa y de su contenido.|Teclas Ctrl\+flecha|  
|Mueva la selección activa, pero no su contenido.|Mayús\+teclas de dirección|  
|Cambiar el tamaño de la selección activa, pero no su contenido.|Teclas Mayús\+Ctrl\+Flecha|  
|Confirmar el nivel actual|Devolución|  
|Disminuir el grosor de la herramienta|\[|  
|Aumentar el grosor de la herramienta|\]|  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Trabajar con activos 3D para juegos y aplicaciones](../designers/working-with-3-d-assets-for-games-and-apps.md)|Proporciona información general sobre las herramientas que puede usar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con activos de gráficos como texturas e imágenes, modelos 3D y efectos de sombreador.|  
|[Editor de modelos](../designers/model-editor.md)|Describe cómo usar el editor de modelos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con modelos 3D.|  
|[Diseñador de sombras](../designers/shader-designer.md)|Describe cómo usar el diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para operar con sombreadores.|