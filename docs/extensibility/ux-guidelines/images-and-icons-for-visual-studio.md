---
title: "Im&#225;genes e iconos para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Im&#225;genes e iconos para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="a-namebkmkimageuseinvisualstudioa-image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a> Uso de imágenes en Visual Studio  
 Antes de crear la ilustración, considere la posibilidad de hacer uso de las imágenes de más de 1.000 en la [biblioteca de imágenes de Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Tipos de imágenes  
  
-   **Iconos**. Imágenes pequeñas que aparecen en los comandos, las jerarquías, plantillas y así sucesivamente. El tamaño de icono predeterminado utilizado en Visual Studio es un archivo PNG de 16 x 16. Generado automáticamente por el servicio de imágenes de iconos generan el formato XAML para la compatibilidad con HDPI.  
  
     **NOTA:** mientras que las imágenes se utilizan en el sistema de menús, no debería crear un icono para cada comando. Consulte [menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver si el comando debería obtener un icono.  
  
-   **Vistas en miniatura.** Imágenes utilizadas en el área de vista previa de un cuadro de diálogo, como el cuadro de diálogo nuevo proyecto.  
  
-   **Imágenes del cuadro de diálogo.** Imágenes que aparecen en los cuadros de diálogo o asistentes, como gráficos descriptivos o indicadores de mensaje. Utilice con poca frecuencia y sólo cuando sea necesario para ilustrar un concepto difícil u obtener la atención del usuario (alerta de advertencia).  
  
-   **Imágenes animadas.** Se utiliza en los indicadores de progreso, barras de estado y los cuadros de diálogo de la operación.  
  
-   **Cursores.** Utilizado para indicar si una operación está permitida con el mouse, donde se puede colocar un objeto y así sucesivamente.  
  
##  <a name="a-namebkmkicondesigna-icon-design"></a><a name="BKMK_IconDesign"></a> Diseño de los iconos  
  
### <a name="overview"></a>Información general  
 Visual Studio utiliza los iconos de estilo moderno, que tienen un saldo 50/50 positivo o negativo (claro/oscuro) y geometría limpia y utilizar metáforas directas y comprensibles. Diseño de icono crucial puntos giran en torno claridad, la simplificación y el contexto.  
  
-   **Claridad:** centrarse en la metáfora de núcleo que proporciona un icono de su significado y la personalidad.  
  
-   **Simplificación:** reducir el icono a su significado core: transmitir el tema con sólo los elementos necesarios y no frills.  
  
-   **Contexto:** tener en cuenta todos los aspectos de la función de un icono durante el desarrollo del concepto, que es fundamental a la hora de decidir qué elementos constituyen la metáfora del núcleo del icono.  
  
 Con iconos, hay un número de puntos de diseño para evitar:  
  
-   No utilice los iconos que indican los elementos de interfaz de Usuario excepto cuando sea adecuado. Elegir un enfoque más abstracto o simbólico cuando el elemento de interfaz de Usuario común, evidente, ni único.  
  
-   No abusar de los elementos comunes como documentos, carpetas, flechas y la Lupa. Use estos elementos solo cuando es esencial para el significado del icono. Por ejemplo, la lupa hacia la derecha debe indicar sólo buscar, examinar y buscar.  
  
-   Aunque algunos elementos de icono heredado mantienen el uso de perspectiva, no cree nuevos iconos con una perspectiva a menos que el elemento no tiene una mayor claridad sin él.  
  
-   No verter hasta demasiada información en un icono. Una imagen sencilla que puede reconoce fácilmente o adquirida como un símbolo reconocible es mucho más útil que una imagen demasiado compleja. Un icono no muestra todo el panorama.  
  
### <a name="icon-creation"></a>Creación de icono  
  
#### <a name="concept-development"></a>Desarrollo del concepto  
 Visual Studio tiene dentro de su interfaz de Usuario una gran variedad de tipos de icono. Considere cuidadosamente el tipo de icono durante el desarrollo. No utilice objetos de interfaz de Usuario es confuso o poco comunes para los elementos de icono. Elegir el vínculo simbólico en estos casos, como con el icono de etiqueta inteligente. Tenga en cuenta que el significado de la etiqueta abstracta a la izquierda es más obvio que la versión imprecisa y de interfaz de Usuario de la derecha:  
  
|||  
|-|-|  
|**Uso correcto de imágenes simbólico**|**Uso incorrecto de imágenes simbólico**|  
|![Icono de etiqueta inteligente correcta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icono de etiqueta inteligente incorrecta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|  
  
 Hay casos en que los elementos de interfaz de Usuario estándares, fácilmente reconocibles funcionan bien para iconos. Agregar que ventana es un ejemplo:  
  
|||  
|-|-|  
|**Elemento de interfaz de Usuario correcto en un icono**|**Elemento de interfaz de Usuario incorrecto en un icono**|  
|![Icono de agregar ventana correcto](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icono de agregar ventana incorrecto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|  
  
 No use un documento como un elemento base a menos que sea esencial para el significado del icono. Sin el documento de elemento en Agregar documento (el significado a continuación) se pierde, mientras que actualice el elemento de documento no es necesario comunicar el significado.  
  
|||  
|-|-|  
|**Uso correcto del icono de documento**|**Uso incorrecto del icono de documento**|  
|![Icono de documento correcto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icono de documento incorrecto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|  
  
 El concepto de "show" se debe representar mediante el icono que mejor ilustra lo que se muestra, tal como en el ejemplo de mostrar todos los archivos. Puede utilizarse una metáfora de la lente para indicar el concepto de "vista" si es necesario, como en el ejemplo de la vista de recursos.  
  
|||  
|-|-|  
|**"Mostrar"**|**"Vista"**|  
|![Icono Mostrar](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icono Vista](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|  
  
 El hacia la derecha lupa icono debe representan sólo buscar, buscar y examinar. La variante hacia la izquierda con el signo más o un signo menos debe representar solo el zoom para acercar, Alejar.  
  
|||  
|-|-|  
|**"Búsqueda"**|**"Zoom"**|  
|![Icono Búsqueda](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icono Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|  
  
 En las vistas de árbol, no utilice el icono de carpeta y un modificador. Cuando esté disponible, use sólo el modificador.  
  
|||  
|-|-|  
|**Iconos de la vista de árbol correcto**|**Iconos de la vista de árbol incorrecto**|  
|![Icono de vista de árbol correcta &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![Icono de vista de árbol correcta &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icono de vista de árbol incorrecta &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![Icono de vista de árbol incorrecta &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Detalles de estilo  
  
#### <a name="layout"></a>Diseño  
 Elementos de la pila que se muestra para los iconos de 16 x 16 estándar:  
  
 ![Pila de diseño para los iconos de 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")  
  
 **Pila de diseño para los iconos de 16 x 16**  
  
 Elementos de notificación de estado son más usados como iconos independiente. Hay contextos, sin embargo, en el que una notificación debe ser apilada del elemento base, como con el icono de la tarea completada:  
  
 ![Notificaciones independientes en Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")  
  
 **Iconos de notificación independiente**  
  
 ![Icono de tarea completa](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")  
  
 **Icono de tarea completa**  
  
 Iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. La mayoría de los iconos de 16 x 16 contienen los mismos elementos. Las versiones de 32 x 32 tienen más detalles, incluidos el tipo de proyecto cuando sea aplicable.  
  
 ![Iconos de proyecto en Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")  
  
 **Iconos de proyecto de biblioteca de controles de Windows de VB, 16 x 16 y 32 x 32**  
  
 Centro de un icono dentro de su marco de píxel. Si esto no es posible, alinear el icono en la parte superior o derecha del marco.  
  
 ![Icono centrado en el fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")  
  
 **Icono centrado en el fotograma de píxeles**  
  
 ![Icono alineado en la parte superior derecha del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")  
  
 **Icono alineado en la parte superior derecha del marco**  
  
 ![Icono centrado y alineado en la parte superior del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")  
  
 **Icono centrado y alineado en la parte superior del marco**  
  
 Para lograr el equilibrio y alineación ideal, evite obstrucción de elemento de base del icono con los glifos de acción. Coloque el glifo en la parte superior izquierdo del elemento base. Cuando se agrega un elemento adicional, considere la posibilidad de la alineación y el saldo del icono.  
  
|||  
|-|-|  
|**Equilibrio y alineación correcta**|**Equilibrio y alineación incorrecta**|  
|![Equilibrio y alineación correctos de los iconos](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio y alineación incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|  
  
 Asegúrese de paridad de tamaño de los iconos que comparten elementos y se utilizan en conjuntos. Tenga en cuenta que en el emparejamiento incorrecto, el círculo y flecha son demasiado grandes y no coinciden.  
  
|||  
|-|-|  
|**Paridad del tamaño correcto**|**Paridad de tamaño incorrecto**|  
|![Tamaño y paridad correctos de los iconos](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Tamaño y paridad incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|  
  
 Usar línea coherente y pesos visuales. Evaluar cómo compara el icono que se va a compilar otros iconos utilizando una comparación en paralelo. Nunca utilice todo el fotograma de 16 x 16, utilice 15 x 15 o más pequeño. La proporción de positivo a negativo (oscuro a luz) debe ser de 50/50.  
  
|||  
|-|-|  
|**Proporción de positivo a negativo correcta**|**Proporción de positivo a negativo incorrecta**|  
|![Corregir el grosor visual para los iconos &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Corregir el grosor visual para los iconos &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Corregir el grosor visual para los iconos &#40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Grosor visual incorrecto para iconos](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|  
  
 Usar formas simples, comparables y ángulos complementario para crear los elementos sin sacrificar la integridad del elemento. Utilice los ángulos de 45° o 90° siempre que sea posible.  
  
 ![Ángulos de icono correctos](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Perspectiva  
 Mantenga el icono claro y comprensible. Perspectiva de uso y una fuente de luz sólo cuando sea necesario. Aunque con perspectiva en elementos de icono, se debe evitar algunos elementos están irreconocibles sin él. En estos casos, una perspectiva ESTILIZADA comunica la claridad del elemento.  
  
 ![3 &#45; punto de perspectiva](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")  
  
 **perspectiva de 3 puntos**  
  
 ![1 &#45; punto de perspectiva](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")  
  
 **perspectiva de 1 punto**  
  
 La mayoría de los elementos deben ser accesibles desde o en ángulo a la derecha.  
  
 ![Iconos en ángulo derecho](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")  
  
 Usar fuentes de luz sólo cuando agrega claridad necesaria a un objeto.  
  
|||  
|-|-|  
|**Fuente de luz correcta**|**Fuente de luz incorrecta**|  
|![Fuentes de luz correctas para iconos](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Fuentes de luz incorrectas para iconos](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|  
  
 Utilizar esquemas sólo para mejorar la legibilidad o para comunicar mejor la metáfora. El saldo de negativo positivo (dark luz) debe ser de 50/50.  
  
|||  
|-|-|  
|**Uso correcto de contornos**|**Uso incorrecto de contornos**|  
|![Contornos correctos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Contornos incorrectos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Tipos de icono  
 **La barra de comandos y shell** iconos constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o estado.  
  
 ![Iconos de barra de comandos y shell](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")  
  
 **Ejemplos de iconos de barra de comandos y shell**  
  
 **Barra de comandos de ventana de herramienta** iconos constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o estado.  
  
 ![Iconos de barra de comandos de ventana de herramientas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")  
  
 **Ejemplos de iconos de barra de comandos de ventana de herramienta**  
  
 **Para eliminar la ambigüedad vista árbol** iconos constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o estado.  
  
 ![Iconos para eliminar la ambigüedad de la vista de árbol](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")  
  
 **Ejemplos de árbol de la vista iconos para eliminar la ambigüedad**  
  
 **Taxonomía de valor basado en estado** iconos existen en los siguientes estados: activo, activo deshabilitado y deshabilitado inactiva.  
  
 ![Estado &#45; iconos de valor de taxonomía basado en](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")  
  
 **Ejemplos de iconos de taxonomía basado en estado de valor**  
  
 **IntelliSense** iconos constan de no más de tres de los siguientes elementos: una base, un modificador y estado.  
  
 ![Iconos de IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")  
  
 **Ejemplos de iconos de IntelliSense**  
  
 **Pequeño (16 x 16) proyecto** iconos deben tener no más de dos elementos: una base y un modificador.  
  
 ![icono de proyecto de 16 x 16 &#40; 1 &#41;](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![icono de proyecto de 16 x 16 &#40; 2 &#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![icono de proyecto de 16 x 16 &#40; 3 &#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")  
  
 **Ejemplos de iconos pequeños de proyecto (16 x 16)**  
  
 **Proyecto de gran tamaño (32 x 32)** iconos consisten en no más de cuatro de los siguientes elementos: una base, uno o dos modificadores y un lenguaje de superposición.  
  
 ![Iconos de proyecto de 32 x 32](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")  
  
 **Ejemplos de iconos grandes de proyecto (32 x 32)**  
  
### <a name="production-details"></a>Detalles de la producción  
 Todos los nuevos elementos de interfaz de Usuario se deben crear con Windows Presentation Foundation (WPF) y todos los nuevos iconos para WPF deben estar en formato PNG de 32 bits. El PNG de 24 bits es un formato heredado que no admiten la transparencia y, por tanto, no se recomienda para los iconos.  
  
 Guarde la resolución a 96 PPP.  
  
#### <a name="file-types"></a>Tipos de archivo  
  
-   **PNG de 32 bits:** el formato preferido para los iconos. Formato de archivo de compresión sin pérdida de datos que puede almacenar una imagen de mapa de bits única (píxeles). archivos PNG de 32 bits compatible con la transparencia del canal alfa, la corrección gamma y entrelazado.  
  
-   **BMP de 32 bits:** para los controles de WPF no. También se denomina XP o color de alta densidad, 32 bits BMP es un formato de imagen RGB o A una imagen de color verdadero con una transparencia del canal alfa. El canal alfa es un nivel de transparencia designado en Adobe Photoshop y que, a continuación, se guarda en el mapa de bits como un adicional (cuarto) canal de color. Se agrega un fondo negro durante la producción de material gráfico a todos los archivos BMP de 32 bits para proporcionar una indicación visual rápida acerca de la profundidad de color. Este fondo negro representa el área que se enmascaran en la interfaz de Usuario.  
  
-   **ICO de 32 bits:** para los iconos de proyecto y agregar elemento. Todos los archivos ICO son true color de 32 bits con transparencia del canal alfa (RGB/A). Como los archivos ICO pueden almacenar distintos tamaños y profundidades de color, iconos de Vista suelen en formato ICO que contiene 16 x 16, 32 x 32, 48 x 48 y tamaños de imagen de 256 x 256. Para poder mostrar correctamente en el Explorador de Windows, archivos ICO se deben guardar profundidad profundidades de color de 24 bits y 8 bits para cada tamaño de la imagen.  
  
-   **XAML:** para superficies de diseño y los controles Adorner de Windows. Iconos XAML son los archivos de imagen basada en vectores que admiten escalar, girar, archivado y transparencia. Hoy en día no son comunes en Visual Studio, pero son cada vez más populares debido a su flexibilidad.  
  
-   **SVG**  
  
-   **24 bits BMP:** de la barra de comandos de Visual Studio. Un formato de imágenes de color verdadero RGB de 24 bits BMP es una convención de icono que crea una capa de transparencia mediante magenta (R = 255, G = 0, B = 255) como clave de color de una capa de transparencia fuera de realizar. En 24 bits BMP, todas las superficies magenta se muestran con el color de fondo.  
  
-   **24 bits GIF:** de la barra de comandos de Visual Studio. Formato de imagen RGB de color verdadero que admite la transparencia. GIF (archivos) a menudo se utilizan en animaciones GIF e ilustraciones de asistente.  
  
### <a name="icon-construction"></a>Construcción de icono  
 El tamaño más pequeño de icono en Visual Studio es 16 x 16. El mayor en común uso es 32 x 32. Tenga en cuenta que no se llenará todo el fotograma de 16 x 16, 24 x 24 o 32 x 32 al diseñar un icono. Construcción de icono legibles y uniforme es esencial para el reconocimiento de usuarios. Respetar los siguientes puntos al crear iconos.  
  
-   Iconos deben ser clara, comprensible y coherente.  
  
-   Es mejor utilizar los elementos de notificación de estado como iconos únicos y no a apilar encima de un elemento base del icono. En ciertos contextos, la interfaz de Usuario podría requerir el elemento de estado para emparejarse con un elemento base.  
  
-   Iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. Se actualizan los iconos 16 x 16, 24 x 24 y 32 x 32. La mayoría de los iconos de 16 x 16 y 24 x 24 contendrá los mismos elementos. Los iconos de 32 x 32 contienen más detalles, incluido el tipo de lenguaje del proyecto cuando sea aplicable.  
  
-   Para los iconos de 32 x 32, los elementos base generalmente tienen un grosor de línea de 2 píxeles. Un grosor de línea de 1 o 2 píxeles puede usarse para los elementos de detalle. Utilice su criterio para determinar cuál es el más adecuado.  
  
-   Tiene al menos un espacio de 1 píxel entre iconos de 24 x 24 y elementos de 16 x 16. Para los iconos de 32 x 32, utilice 2 píxeles espaciado entre los elementos y entre el modificador y el elemento base.  
  
 ![Espaciado de elementos para iconos 16 x 16, 24 x 24 y 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")  
  
 **Espaciado de elementos para iconos de tamaño de 16 x 16, 24 x 24 y 32 x 32**  
  
#### <a name="color-and-accessibility"></a>Color y accesibilidad  
 Directrices de compatibilidad de Visual Studio requieren que todos los iconos en el producto pasan los requisitos de accesibilidad para el color y el contraste. Esto se logra a través de la inversión de icono y al diseñar, debe tener en cuenta que se invierte mediante programación en el producto.  
  
 Para obtener más información sobre el uso de color en los iconos de Visual Studio, consulte [con color en imágenes](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="a-namebkmkusingcolorinimagesa-using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a> Uso de color en imágenes  
  
### <a name="overview"></a>Información general  
 Los iconos de Visual Studio son principalmente monocromáticos. Color está reservado para transmitir información específica y nunca para la decoración. Se utiliza el color:  
  
-   para indicar una acción  
  
-   para avisar al usuario una notificación de estado  
  
-   Para designar la afiliación de lenguaje  
  
-   para diferenciar los elementos dentro de IntelliSense  
  
### <a name="accessibility"></a>Accesibilidad  
 Directrices de compatibilidad de Visual Studio requieren que todos los iconos comprueban en la fase de producto de color y contraste los requisitos de accesibilidad. Colores de la paleta de lenguaje visual se han probado y cumplan estos requisitos.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversión de colores para temas oscuros  
 Para poder crear iconos aparecen con la relación de contraste correcto en el tema oscuro de Visual Studio, una inversión se aplica mediante programación. Los colores en esta guía se han elegido en parte para que invierte correctamente. Restringir el uso de color de esta paleta u obtendrá resultados imprevisibles cuando se aplica la inversión.  
  
 ![Ejemplos de iconos cuyos colores se han invertido](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")  
  
 **Ejemplos de iconos que han tenido los colores invertidos**  
  
### <a name="base-palette"></a>Paleta básica  
 Todos los iconos estándares contienen tres colores bases. Iconos no contienen degradados o sombras paralelas, con una o dos excepciones para los iconos de herramienta 3D.  
  
|Uso|Nombre|Valor (tema claro)|Muestra|Ejemplo|  
|-----------|----------|---------------------------|------------|-------------|  
|Fondo/oscuro|VS BG|424242 / 66,66,66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Ejemplo de paleta básica](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|  
|Primer plano o ligeros|FG DE VS|F0EFF1 / 240,239,241|![Muestra F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Esquema|FRENTE a|F6F6F6 / 246,246,246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Además de los colores bases, cada icono puede contener adicionales a un color de la paleta extendido.  
  
### <a name="extended-palette"></a>Paleta extendido  
  
#### <a name="action-modifiers"></a>Modificadores de acción  
 Los cuatro colores a continuación indican los tipos de acciones requeridas por los modificadores de acción:  
  
|Uso|Nombre|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Positivo|Verde de la acción de VS|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativo|VS acción rojo|A1260D / 161,38,13|![Muestra A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|Azul de la acción de VS|C 00539 / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Crear nuevo|Naranja de la acción de VS|C27D1A / 194,156,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Ejemplos  
 Verde se utiliza para los modificadores de acción positiva como "Add", "Run", "Reproducir" y "Validar".  
  
|||||  
|-|-|-|-|  
|![Icono de ejecución de](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **Ejecutar**|![Icono de consulta ejecutar](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery") **Ejecutar consulta**|![Icono reproducir todos los pasos](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps") **reproducir todos los pasos**|![Icono de control de agregar](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl") **Agregar Control**|  
  
 Rojo se usa para modificadores de acción negativo como "Delete," "Stop", "Cancelar" y "Cerrar".  
  
|||||  
|-|-|-|-|  
|![Icono Eliminar relación](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship") **Eliminar relación**|![Icono Eliminar columna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn") **Eliminar columna**|![Icono de detención consulta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery") **Detener consulta**|![Icono sin conexión](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline") **conexión sin conexión**|  
  
 Azul se aplica a la acción neutro modificadores normalmente representan como flechas, como "Abierto" "Siguiente", "Anterior", "Importación" y "Exportación".  
  
|||||  
|-|-|-|-|  
|![Vaya al icono del campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField") **Ir al campo**|![Por lotes comprobación &#45; icono](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn") **por lotes de protección**|![Icono de editor de direcciones](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor") **Editor de direcciones**|![Icono de editor de asociación](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor") **Editor de asociaciones**|  
  
 Oro oscuro se utiliza principalmente para el modificador "Nuevo".  
  
|||||  
|-|-|-|-|  
|![Icono de proyecto nuevo](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject") **nuevo proyecto**|![Crear nuevo icono de gráfico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph") **crear un nuevo gráfico**|![Icono nueva prueba unitaria](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest") **nueva prueba de unidad**|![Icono de elemento de lista nuevo](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem") **nuevo elemento de lista**|  
  
#### <a name="special-cases"></a>Casos especiales  
 En casos especiales, un modificador de acción color se puede utilizar independientemente como un icono independiente. El color usado para el icono refleja las acciones que está asociado el icono. Este uso se limita a un pequeño subconjunto de iconos, incluidos:  
  
||||||  
|-|-|-|-|-|  
|![Icono de ejecución de](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun") **Ejecutar**|![Icono de detención](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop") **Detener**|![Icono Eliminar](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete") **Eliminar**|![Icono Guardar](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save") **Guardar**|![Icono de atrás Navigate](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack") **desplazarse hacia atrás**|  
  
### <a name="code-hierarchy-palette"></a>Paleta de jerarquía de código  
  
#### <a name="folder"></a>Carpeta  
  
|Uso|Nombre|Valor (todos los temas)|Muestra|Ejemplo|  
|-----------|----------|--------------------------|------------|-------------|  
|Carpetas|Carpeta|DCB67A / 220,182,122|![Muestra DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icono Carpeta de color](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Lenguajes de Visual Studio  
 Cada uno de los lenguajes común o plataformas disponibles en Visual Studio tiene un color asociado. Estos colores se utilizan en el icono de base, o acerca de los modificadores de lenguaje que aparecen en la esquina superior derecha de los iconos compuestas.  
  
|Uso|Nombre|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF azul|7 0095D / 0,149,215|![Muestra 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP púrpura|9B4F96 / 155,79,150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS verde (VS acción verde)|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Rojo CSS|BD1E2D / 189,30,45|![Muestra BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|Púrpura de FS|672878 / 103,40,120|![Muestra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS naranja|F16421 / 241,100,33|![Muestra F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB azul (VS acción azul)|C 00539 / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Naranja de TS|E04C06 / 224,76,6|![Muestra E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|PY verde|879636 / 135,150,54|![Muestra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Ejemplos de iconos con modificadores de lenguaje  
  
|||||||  
|-|-|-|-|-|-|  
|![Icono de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB") **VB**|![C &#35; icono](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp") **C#**|![C &#43; &#43; icono](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus") **C++**|![F &#35; icono](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp") **F #**|![Icono de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript") **JavaScript**|![Icono de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python") **Python**|  
|![Icono de HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML") **HTML**|![Icono WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF") **WPF**|![Icono de ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP") **ASP**|![Icono de CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS") **CSS**|![Icono de typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript") **TypeScript**||  
  
#### <a name="intellisense"></a>IntelliSense  
 Iconos de IntelliSense utilizan una paleta de colores exclusivo. Estos colores se utilizan para ayudar a los usuarios a distinguir rápidamente entre los distintos elementos de la lista emergente de IntelliSense.  
  
|Uso|Nombre|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Clase de evento|Naranja de la acción de VS|C27D1A / 194,125,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Método de extensión, método, módulo, delegado|Púrpura de acción de VS|652 90 D / 101,45,144|![Muestra 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Campo, elemento de enumeración, macros, estructura, tipo de valor de unión, operador, interfaz|Azul de la acción de VS|C 00539 / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objeto|Verde de la acción de VS|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Constante, excepción, el elemento de enumeración, mapa, elemento de mapa, espacio de nombres de plantilla, una definición de tipo|Fondo (VS BG)|424242 / 66,66,66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Ejemplos de iconos de IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Icono de clase de IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass") **(clase)**|![Icono de evento privado de IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent") **evento privado**|![Icono de delegado de IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate") **delegar**|![Icono de amigo de método de IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend") **Friend (método)**|![Icono del campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field") **campo**|  
|![IntelliSense protegido icono de elemento de enumeración](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem") **elemento de enumeración protegida**|![Icono de objeto de IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject") **objeto**|![Icono de plantilla de IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate") **plantilla**|![Icono de acceso directo de IntelliSense excepción](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut") **acceso directo (excepción)**||  
  
### <a name="notifications"></a>Notificaciones  
 Notificaciones en Visual Studio se utilizan para indicar el estado. La paleta de notificación utiliza los siguientes cuatro colores, así como opciones de relleno de primer plano blanco o negro para definir notificaciones con los siguientes niveles de estado.  
  
|Uso|Nombre|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Estado: neutro|Notificación azul (VS azul)|1BA1E2 / 27,161,226|![Muestra 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Estado: positivo|Notificación verde (VS verde)|339933 / 51,153,51|![Muestra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Estado: negativo|Notificación rojo (VS rojo)|E51400 / 229,20,0|![Muestra E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Estado: advertencia|Notificación amarillo (VS naranja)|FFCC00 / 255,204,0|![Muestra FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Relleno de primer plano|Notificación negro (negro)|000000 / 0,0,0|![Muestrario &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Relleno de primer plano|Notas de la notificación (blanco)|FFFFFF / 255,255,255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Ejemplos de iconos de notificación  
  
|||||  
|-|-|-|-|  
|![Icono de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert") **alerta**|![Icono de advertencia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning") **Advertencia**|![Icono de completado](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete") **completado**|![Icono de detención](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop") **Detener**|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 En general, Visual Studio Online consta de características que se hospeda en un explorador. Varía el color en entornos diferentes, pero el estilo sigue siendo la misma.  
  
|Agrupar|Uso|Nombre|Valor (todos los temas)|Muestra|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Fondo|TFSO BG|656565/ 101, 101, 101|![Muestra 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Esquema|TFSO OUT|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Mónaco|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|Grey_Primary de F12|555555 / 85, 85, 85|![Muestra 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Al mantener el puntero|Blue_Hover de F12|2279BF / 34,121,191|![Muestra 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Deshabilitado|LtGrey_Disabled de F12|ABABAC / 171,171,172|![Muestra ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Segundo plano al mantener el mouse|Al mantener el mouse bg|D9EBF7 / 217,235,247|![Muestra D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Fondo presionado|Bg presionado|B2D7F0 / 178,215,240|![Muestra B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Esquema|FRENTE A|F6F6F6 / 246,246,246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Información|Información|00BCF2 / 0,188,242|![Muestra 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Advertencia|Advertencia|F28300 / 242,131,0|![Muestra F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Error / negativo|Error_Negative|E81123 / 232,17,35|![Muestra E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Iniciar / positivo|Start_Positive|009E49 / 0,158,73|![Muestra 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Tipo de salto|Tipo de salto|9B4F96 / 155,79,150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Marca de evento|Marca de evento|A51F00 / 165,31,0|![Muestra A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Marca de usuario|Marca de usuario|F16220 / 241,98,32|![Muestra F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Ejemplos de iconos de Visual Studio Online  
  
|TFS en línea||||  
|----------------|-|-|-|  
|![Icono de equipo de TFS en línea](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam") **equipo Online**|![Icono de información de TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation") **información**|![Icono de historial TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory") **historial**|![Icono de bifurcación TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch") **sucursales**|  
  
|Napa||||  
|----------|-|-|-|  
|![Icono de contenido de Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent") **contenido**|![Icono de correo electrónico de office de Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail") **correo electrónico de Office**|![Icono de SharePoint de Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint") **SharePoint**|![Icono de panel de tareas de Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane") **panel de tareas**|  
  
|Mónaco||||  
|------------|-|-|-|  
|![Icono de Mónaco archivos](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles") **archivos**|![Icono de Git de Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit") **Git**|![Icono de búsqueda de Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch") **búsqueda**|![Icono de texto de Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText") **texto**|  
  
|F12||||  
|---------|-|-|-|  
|![Icono de F12 bastante](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode") **bastante código**|![Icono de advertencia de F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning") **Advertencia**|![Icono emular de F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate") **emular**|