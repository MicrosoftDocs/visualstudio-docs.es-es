---
title: "Imágenes e iconos para Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7856f8fac7e986f3e5383fa91261de39fe815a28
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="images-and-icons-for-visual-studio"></a>Imágenes e iconos para Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a>Uso de imágenes en Visual Studio  
 Antes de crear el material gráfico, considere la posibilidad de hacer que el uso de las imágenes de más de 1.000 en el [biblioteca de imágenes de Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Tipos de imágenes  
  
-   **Iconos**. Imágenes pequeñas que aparecen en los comandos, las jerarquías, plantillas y así sucesivamente. El tamaño de icono predeterminado utilizado en Visual Studio es un archivo PNG de 16 x 16. Generado automáticamente por el servicio de imágenes de iconos generan el formato XAML para la compatibilidad con HDPI.  
  
     **Nota:** mientras que las imágenes se utilizan en el sistema de menús, no debería crear un icono para cada comando. Consulte [menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver si el comando debería obtener un icono.  
  
-   **Vistas en miniatura.** Imágenes que se utilizan en el área de vista previa de un cuadro de diálogo, por ejemplo, el cuadro de diálogo nuevo proyecto.  
  
-   **Imágenes del cuadro de diálogo.** Imágenes que aparecen en los cuadros de diálogo o asistentes, como gráficos descriptivos o indicadores de mensaje. Usar con poca frecuencia y solo cuando sea necesario ilustrar un concepto difícil o conseguir la atención del usuario (advertencia de alerta,).  
  
-   **Imágenes animadas.** Se utiliza en los indicadores de progreso, barras de estado y los cuadros de diálogo de la operación.  
  
-   **Cursores.** Utilizado para indicar si se permite una operación mediante el mouse, donde se puede colocar un objeto y así sucesivamente.  
  
##  <a name="BKMK_IconDesign"></a>Diseño de los iconos  
  
### <a name="overview"></a>Información general  
 Visual Studio usa iconos de estilo moderno, que tienen geometry limpia y un equilibrio entre 50/50 positivo o negativo (claro/oscuro) y usar metáforas directa y comprensibles. Diseño de los iconos fundamental apunta giran en torno claridad, simplificación y contexto.  
  
-   **Claridad:** centrarse en la metáfora de núcleo que proporciona un icono de su significado y personalidad.  
  
-   **Simplificación:** reducir el icono a su significado core - comunicar el tema con solo los elementos necesarios y no frills.  
  
-   **Contexto:** tenga en cuenta todos los aspectos del rol de un icono durante el desarrollo del concepto, que es fundamental a la hora de decidir qué elementos constituyen la metáfora del núcleo del icono.  
  
 Con iconos, hay un número de puntos de diseño para evitar:  
  
-   No use los iconos que indican elementos de interfaz de usuario excepto cuando corresponda. Elegir un enfoque más abstracto o simbólico cuando el elemento de interfaz de usuario no es común, evidente, ni único.  
  
-   No uso excesivo de elementos comunes como documentos, carpetas, flechas y la Lupa. Use estos elementos solo cuando es esencial para el significado del icono. Por ejemplo, la lupa hacia la derecha debe indicar sólo buscar, examinar y buscar.  
  
-   Aunque algunos elementos de icono heredado mantienen el uso de perspectiva, no se crean nuevos iconos con una perspectiva a menos que el elemento no tiene una mayor claridad sin él.  
  
-   No cram demasiada información en un icono. Una imagen sencilla que se puede fácilmente reconoce o aprendida como un símbolo reconocible es mucho más útil que una imagen demasiado compleja. Un icono no muestra todo el panorama.  
  
### <a name="icon-creation"></a>Creación de icono  
  
#### <a name="concept-development"></a>Desarrollo del concepto  
 Visual Studio en su interfaz de usuario tiene una amplia variedad de tipos de icono. Tenga en cuenta el tipo de icono durante el desarrollo. No use claros o poco habituales de los objetos de interfaz de usuario para los elementos de icono. Optar por simbólico en estos casos, como con el icono de etiqueta inteligente. Tenga en cuenta que el significado de la etiqueta abstracta de la izquierda es más evidente que la versión imprecisa, basado en la interfaz de usuario de la derecha:  
  
|||  
|-|-|  
|**Uso correcto de imágenes simbólico**|**Uso incorrecto de imágenes simbólico**|  
|![Icono de etiqueta inteligente correcta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "01_SmartTagCorrect 0404")|![Icono de etiqueta inteligente incorrecta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "02_SmartTagIncorrect 0404")|  
  
 Hay casos en que los elementos de interfaz de usuario estándar y fácil de reconocer funciona bien para iconos. Agregar que ventana es un ejemplo:  
  
|||  
|-|-|  
|**Elemento de interfaz de usuario correcto en un icono**|**Elemento de interfaz de usuario incorrecto en un icono**|  
|![Icono Agregar ventana correcto](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "03_AddWindowCorrect 0404")|![Icono Agregar ventana incorrecto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "04_AddWindowIncorrect 0404")|  
  
 No use un documento como un elemento base a menos que sea esencial para el significado del icono. Sin el documento de elemento en el documento de agregar (el significado a continuación) se pierde, mientras que con la actualización es necesario comunicar el significado del elemento de documento.  
  
|||  
|-|-|  
|**Uso correcto de icono de documento**|**Uso incorrecto del icono de documento**|  
|![Icono de documento correcto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "05_DocumentIconCorrect 0404")|![Icono de documento incorrecto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "06_DocumentIconIncorrect 0404")|  
  
 El concepto de "Mostrar" debe estar representado por el icono que ilustra mejor lo que se está mostrando, por ejemplo, al igual que con el ejemplo de mostrar todos los archivos. Una metáfora de la lente puede utilizarse para indicar el concepto de "vista" si es necesario, como con el ejemplo de vista de recursos.  
  
|||  
|-|-|  
|**"Mostrar"**|**"Vista"**|  
|![Mostrar icono de](../../extensibility/ux-guidelines/media/0404-07_show.png "07_Show 0404")|![Icono de vista](../../extensibility/ux-guidelines/media/0404-08_view.png "08_View 0404")|  
  
 El hacia la derecha lupa icono de debe representan sólo buscar, buscar y examinar. La variante hacia la izquierda con el signo más o un signo menos debe representan sola zoom para acercar / alejar.  
  
|||  
|-|-|  
|**"Búsqueda"**|**"Zoom"**|  
|![Icono de búsqueda](../../extensibility/ux-guidelines/media/0404-09_search.png "09_Search 0404")|![Icono de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "10_Zoom 0404")|  
  
 En las vistas de árbol, no utilice el icono de carpeta y un modificador. Cuando esté disponible, use sólo el modificador.  
  
|||  
|-|-|  
|**Iconos de la vista de árbol correcto**|**Iconos de la vista de árbol incorrecta**|  
|![Icono de vista de árbol correcta &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![corregir el icono de vista de árbol &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Icono de vista de árbol incorrecta &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![incorrecta icono de vista de árbol &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Detalles de estilo  
  
#### <a name="layout"></a>Diseño  
 Elementos de la pila como se muestra para los iconos de 16 x 16 estándar:  
  
 ![Pila de diseño para iconos 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "15_LayoutStack 0404")<br />Pila de diseño para los iconos de 16 x 16
  
 Elementos de notificación de estado son más usados como iconos independiente. Hay contextos, sin embargo, en el que una notificación debe ser apilada en el elemento base, como con el icono de la tarea completada:  
  
 ![Notificaciones independientes en Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "16_StandaloneNotificationIcons 0404")<br />Iconos de notificación independiente
  
 ![Icono de tarea completa](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "17_TaskComplete 0404")<br />Icono de tarea completa
  
 Iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. Iconos de 16 x 16 mayoría contienen los mismos elementos. Las versiones de 32 x 32 tengan más detalles, incluido el tipo de proyecto cuando sea aplicable.  
  
 ![Proyecto de iconos en Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "18_IconProjectThreeSizes 0404")<br />Iconos de proyecto de biblioteca de controles de Windows de VB, 16 x 16 y 32 x 32 
  
 Centro de un icono en el fotograma de píxeles. Si esto no es posible, alinear el icono a la parte superior o derecha del marco.  
  
 ![Icono centrado en el fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "19_IconCentered 0404")<br />Icono centrado en el fotograma de píxeles
  
 ![Icono alineado para parte superior derecha del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "20_IconTopRight 0404")<br />Icono alineado en la parte superior derecha del fotograma
  
 ![Icono centrado y alineado en la parte superior del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "21_IconTopAlign 0404")<br />Icono centrado y alineado en la parte superior del marco
  
 Para lograr equilibrio y alineación ideal, no dificultar el elemento de base del icono con los glifos de acción. Coloque el glifo en la parte superior izquierdo del elemento base. Cuando se agrega un elemento adicional, considere la posibilidad de la alineación y el saldo del icono.  
  
|||  
|-|-|  
|**Equilibrio y alineación correcto**|**Equilibrio y alineación incorrecta**|  
|![Corregir icono equilibrio y alineación](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "22_AlignBalanceCorrect 0404")|![Icono incorrecto equilibrio y alineación](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "23_AlignBalanceIncorrect 0404")|  
  
 Asegúrese de paridad de tamaño de los iconos que comparten elementos y se utilizan en conjuntos. Tenga en cuenta que en el emparejamiento incorrecto, el círculo y flecha son demasiado grandes y no coinciden.  
  
|||  
|-|-|  
|**Paridad de tamaño correcto**|**Paridad de tamaño incorrecto**|  
|![Corregir el tamaño de icono y paridad](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "24_SizeParityCorrect 0404")|![Tamaño de icono incorrecto y paridad](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "25_SizeParityIncorrect 0404")|  
  
 Usar línea coherente y pesos visuales. Evaluar cómo compara el icono que se va a compilar otros iconos mediante el uso de una comparación en paralelo. Nunca utilice todo el fotograma de 16 x 16, utilice 15 x 15 o más pequeño. La proporción de positivo a negativo (dark-a-light) debe ser 50/50.  
  
|||  
|-|-|  
|**Relación de positivo a negativo correcta**|**Proporción de positivo a negativo incorrecto**|  
|![Corregir grosor visual para iconos &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "26_VisualWeightCorrect1 0404")<br /><br /> ![Corregir grosor visual para iconos &#40; 2 &#41; ] (../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "27_VisualWeightCorrect2 0404")<br /><br /> ![Corregir grosor visual para iconos &#40; 3 &#41; ] (../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "28_VisualWeightCorrect3 0404")|![Grosor visual incorrecto para iconos](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "29_VisualWeightIncorrect 0404")|  
  
 Usar formas simples, de forma similares y ángulos complementario para compilar sus elementos sin sacrificar la integridad del elemento. Usar ángulos de 45° o 90 º siempre que sea posible.  
  
 ![Corregir ángulos de icono](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "30_IconAnglesCorrect 0404")  
  
#### <a name="perspective"></a>Perspectiva  
 Mantenga el icono claro y comprensible. Perspectiva de uso y una fuente de luz solo cuando sea necesario. Aunque la utilización de una perspectiva en elementos de icono, se debe evitar algunos elementos están irreconocibles sin él. En tales casos, una perspectiva ESTILIZADA comunica claridad del elemento.  
  
 ![perspectiva de 3 puntos](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "31_3PointPerspective 0404")<br />Perspectiva de 3 puntos
  
 ![perspectiva de 1 punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "32_1PointPerspective 0404")<br />Perspectiva de 1 punto
  
 Mayoría de los elementos debe ser accesibles desde o en ángulo a la derecha:  
  
 ![Iconos en ángulo derecho](../../extensibility/ux-guidelines/media/0404-33_angledright.png "33_AngledRight 0404")  
  
 Usar fuentes de luz sólo al agregar claridad necesaria a un objeto.  
  
|||  
|-|-|  
|**Origen de luz correcta**|**Origen de luz incorrecta**|  
|![Corregir las fuentes de luz para iconos](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "34_LightSourcesCorrect 0404")|![Fuentes de luz incorrectas para iconos](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "35_LightSourcesIncorrect 0404")|  
  
 Use contornos solo para mejorar la legibilidad o para comunicar mejor la metáfora de. El saldo de negativo positivo (dark-light) debe ser 50/50.  
  
|||  
|-|-|  
|**Uso correcto de esquemas**|**Uso incorrecto de esquemas**|  
|![Corregir contornos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "36_OutlinesCorrect 0404")|![Contornos incorrectos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "37_OutlinesIncorrect 0404")|  
  
#### <a name="icon-types"></a>Tipos de icono  
 **Barra de comandos y shell** iconos consisten en no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.  
  
 ![Ejemplos de iconos de barra de comandos y shell](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "38_ShellIcons 0404")<br />Ejemplos de iconos de barra de comandos y shell
  
 **Barra de comandos de ventana de herramienta** iconos consisten en no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.  
  
 ![Iconos de barra de comandos ejemplos de ventana de herramientas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "39_ToolWindowCommandBarIcons 0404")<br />Ejemplos de iconos de barra de comandos de ventana de herramienta
  
 **Desambiguador de vista de árbol** iconos consisten en no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.  
  
 ![Ejemplos de árbol ver iconos de desambiguador](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "40_TreeViewIcons 0404")<br />Ejemplos de árbol ver iconos de eliminar la ambigüedad
  
 **Taxonomía basado en estado valor** iconos existen en los siguientes estados: activo y active deshabilitado, deshabilitado inactiva.  
  
 ![Ejemplos de iconos de taxonomía basado en estado valor](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "41_StateBasedTaxonomy 0404")<br />Ejemplos de iconos de taxonomía basado en estado valor
  
 **IntelliSense** iconos consisten en no más de tres de los siguientes elementos: una base, un modificador y estado.  
  
 ![Ejemplos de iconos de IntelliSense de](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "42_IntelliSenseIcons 0404")<br />Ejemplos de iconos de IntelliSense
  
 **Pequeño (16 x 16) proyecto** iconos deben tener no más de dos elementos: una base y un modificador.  
  
 ![Ejemplos de pequeño (16 x 16) del proyecto iconos](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![el icono de proyecto de 16 x 16 &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![el icono de proyecto de 16 x 16 &#40; 3 &#41;] (../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />Ejemplos de iconos pequeños de proyecto (16 x 16)
  
 **Proyecto (32 x 32) grande** iconos consisten en no más de cuatro de los siguientes elementos: una base, modificadores de uno o dos y un idioma de superposición.  
  
 ![Ejemplos de gran tamaño (32 x 32) del proyecto iconos](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "46_32x32Project 0404")<br />Ejemplos de iconos grandes de proyecto (32 x 32)
  
### <a name="production-details"></a>Detalles de la producción  
 Todos los nuevos elementos de interfaz de usuario deben crearse mediante Windows Presentation Foundation (WPF) y todos los nuevos iconos para WPF deben estar en formato PNG de 32 bits. El PNG de 24 bits es un formato heredado que no admiten la transparencia y, por tanto, no se recomienda para los iconos.  
  
 Guarde la resolución a 96 PPP.  
  
#### <a name="file-types"></a>Tipos de archivo  
  
-   **PNG de 32 bits:** el formato preferido para iconos. Un formato de archivo de compresión sin pérdida de datos que puede almacenar una imagen de mapa de bits única (píxeles). archivos PNG de 32 bits compatible con transparencia del canal alfa, la corrección gamma y entrelazado.  
  
-   **BMP de 32 bits:** para los controles no son de WPF. También se denomina XP o color de alta densidad, BMP de 32 bits es un formato de imagen RGB/A, una imagen de color verdadero con una transparencia del canal alfa. El canal alfa es un nivel de transparencia designado de Adobe Photoshop que, a continuación, se guarda en el mapa de bits como un adicional (cuarto) canal de color. Se agrega un fondo negro durante la producción de material gráfico a todos los archivos BMP de 32 bits para proporcionar una indicación visual rápida acerca de la profundidad de color. Este fondo negro representa el área que se enmascaran en la interfaz de usuario.  
  
-   **ICO de 32 bits:** como iconos de proyecto y agregar elemento. Todos los archivos ICO están color verdadero de 32 bits con transparencia del canal alfa (RGB/A). Dado que pueden almacenar archivos ICO varios tamaños y profundidades de color, iconos de Vista a menudo tienen un formato ICO que contiene 16 x 16, 32 x 32, 48 x 48 y tamaños de imagen de 256 x 256. Para que se muestren correctamente en el Explorador de Windows, archivos ICO se deben guardar profundidad profundidades de color de 24 bits y 8 bits para cada tamaño de la imagen.  
  
-   **XAML:** para superficies de diseño y los controles Adorner de Windows. Los iconos XAML son archivos de imagen basada en vectores que admiten ajuste de escala, rotación, archivado y transparencia. Hoy en día no son comunes en Visual Studio, pero son cada vez más populares debido a su flexibilidad.  
  
-   **SVG**  
  
-   **24 bits BMP:** para la barra de comandos de Visual Studio. Un formato de imagen de color verdadero RGB, BMP de 24 bits es una convención de icono que se crea una capa de transparencia mediante fucsia (R = 255, G = 0, B = 255) como una clave de color de una capa de transparencia de knock horizontal. En un archivo de 24 bits BMP, todas las superficies magenta se muestran con el color de fondo.  
  
-   **24 bits GIF:** para la barra de comandos de Visual Studio. Formato de imagen RGB de color verdadero que admite la transparencia. GIF (archivos) a menudo se utilizan en animaciones GIF e ilustraciones de asistente.  
  
### <a name="icon-construction"></a>Construcción de icono  
 El tamaño más pequeño de icono en Visual Studio es 16 x 16. El mayor en común uso es 32 x 32. Tenga en cuenta que no para ocupar todo el fotograma de 16 x 16, 24 x 24 o 32 x 32 al diseñar un icono. Construcción de icono legibles, uniforme es esencial para el reconocimiento de usuario. Cumplir los siguientes puntos al crear iconos.  
  
-   Iconos deben ser claros, comprender y coherente.  
  
-   Es mejor utilizar los elementos de notificación de estado como iconos únicos y no a ellos se apilan uno sobre un elemento de base de icono. En algunos contextos, la interfaz de usuario podría requerir el elemento de estado para emparejarse con un elemento base.  
  
-   Iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. Se están actualizando los iconos 16 x 16, 24 x 24 y 32 x 32. La mayoría de los iconos de 16 x 16 y 24 x 24 contendrá los mismos elementos. Los iconos de 32 x 32 contienen más detalles, incluido el tipo de lenguaje del proyecto cuando sea aplicable.  
  
-   Para los iconos de 32 x 32, los elementos base normalmente tienen un grosor de línea de 2 píxeles. Un grosor de línea de 1 o 2 píxeles puede usarse para los elementos de detalle. Utilice su criterio para determinar cuál es la más adecuada.  
  
-   Tener al menos un espaciado 1 píxel entre iconos de 24 x 24 y elementos de 16 x 16. Para los iconos de 32 x 32, use 2 píxeles espaciado entre los elementos y entre el modificador y el elemento base.  
  
 ![Elemento espaciado de tamaño de iconos de 16 x 16, 24 x 24 y 32 x 32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "47_ElementSpacing 0404")<br />Tamaño de espaciado de elementos para iconos 16 x 16, 24 x 24 y 32 x 32
  
#### <a name="color-and-accessibility"></a>Color y accesibilidad  
 Directrices de cumplimiento de normas de Visual Studio requieren que todos los iconos en el producto pasan los requisitos de accesibilidad para el color y el contraste. Esto se logra a través de la inversión de icono y la hora de diseñar, debe ser consciente de que se invierte mediante programación en el producto.  
  
 Para obtener más información sobre el uso de color en iconos de Visual Studio, vea [con color en imágenes](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a>Usar color de imágenes  
  
### <a name="overview"></a>Información general  
 Iconos en Visual Studio son principalmente monocroma. Color se reserva para transmitir información específica y nunca para la decoración. Se utiliza el color:  
  
-   para indicar una acción  
  
-   para avisar al usuario a una notificación de estado  
  
-   Para designar la afiliación de un idioma  
  
-   para diferenciar los elementos dentro de IntelliSense  
  
### <a name="accessibility"></a>Accesibilidad  
 Directrices de cumplimiento de normas de Visual Studio requieren que todos los iconos de los elementos verificados a la fase de producto los requisitos de accesibilidad para el color y el contraste. Colores de la paleta del lenguaje visual se han comprobado y cumplan estos requisitos.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversión de color para los temas oscuros  
 Para realizar iconos aparecen con la relación de contraste correcto en el tema oscuro de Visual Studio, una inversión se aplica mediante programación. Los colores en esta guía se han elegido en parte para que invierte correctamente. Restringir el uso de color a esta paleta, o se producirán resultados imprevisibles cuando se aplica la inversión.  
  
 ![Ejemplos de iconos que han tenido sus colores invertidos](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "01_DarkThemeInversion 0405")<br />Ejemplos de iconos que han tenido sus colores invertidos
  
### <a name="base-palette"></a>Paleta básica  
 Todos los iconos estándares contienen tres colores base. Iconos no contienen degradados o las sombras paralelas, con una o dos excepciones para iconos de herramienta 3D.  
  
|Uso|Name|Valor (el tema claro)|Muestra|Ejemplo|  
|-----------|----------|---------------------------|------------|-------------|  
|Segundo plano/oscuro|VS BG|424242 / 66,66,66|![Muestrario 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Ejemplo de paleta básica](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "02_BasePaletteExample 0405")|  
|Primer plano/ligero|FG DE VS|F0EFF1 / 240,239,241|![Muestra F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Esquema|FRENTE a|F6F6F6 / 246,246,246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Además de los colores base, cada icono puede contener adicionales a un color de la paleta extendido.  
  
### <a name="extended-palette"></a>Paleta extendido  
  
#### <a name="action-modifiers"></a>Modificadores de acción  
 Los cuatro colores a continuación indican los tipos de acciones requeridas por modificadores de acción:  
  
|Uso|Name|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Positivo|Verde de acción de VS|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativo|Rojo de la acción de VS|A1260D / 161,38,13|![Muestra A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Neutral|Azul de la acción de VS|00539C / 0,83,156|![Muestra 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Crear nuevo|VS acción naranja|C27D1A / 194,156,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Ejemplos  
 Verde se utiliza para los modificadores de acción positiva como "Agregar", "Ejecutar", "Reproducción" y "Validación".  
  
|||||  
|-|-|-|-|  
|![Icono ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "03_ActionModifierRun 0405")<br />Run|![Icono Ejecutar consulta](../../extensibility/ux-guidelines/media/0405-04_executequery.png "04_ExecuteQuery 0405")<br />Ejecutar consulta|![Icono reproducir todos los pasos](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "05_PlayAllSteps 0405")<br />Reproducir todos los pasos|![Icono Agregar control](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "06_AddControl 0405")<br />Agregar Control|  
  
 Color rojo se usa para los modificadores de acción negativo como "Delete", "Stop", "Cancelar" y "Cierre".  
  
|||||  
|-|-|-|-|  
|![Icono Eliminar relación](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "07_DeleteRelationship 0405")<br />Eliminar relación|![Icono Eliminar columna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "08_DeleteColumn 0405")<br />Eliminar columna|![Icono del signo Detener consulta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "09_StopQuery 0405")<br />Detener consulta|![Icono sin conexión](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "10_ConnectionOffline 0405")<br />No está conectado|  
  
 Azul se aplica a la acción neutro modificadores normalmente representan como flechas, como "Abrir," "Siguiente", "Anterior", "Importación" y "Exportación".  
  
|||||  
|-|-|-|-|  
|![Vaya al icono del campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "11_GoToField 0405")<br />Ir al campo|![Procesar por lotes comprobación &#45; en el icono de](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "12_BatchedCheckIn 0405")<br />Por lotes en el repositorio|![Icono de editor de direcciones](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "13_AddressEditor 0405")<br />Editor de direcciones|![Icono de editor de asociación](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "14_AssociationEditor 0405")<br />Editor de asociaciones|  
  
 Oro oscuro se utiliza principalmente para el modificador "Nuevo".  
  
|||||  
|-|-|-|-|  
|![Icono nuevo proyecto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "15_NewProject 0405")<br />Nuevo proyecto|![Icono Crear nuevo gráfico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "16_CreateNewGraph 0405")<br />Crear un nuevo gráfico|![Icono nueva prueba unitaria](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "17_NewUnitTest 0405")<br />Nueva prueba unitaria|![Icono de elemento de lista nuevo](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "18_NewListItem 0405")<br />Nuevo elemento de lista|  
  
#### <a name="special-cases"></a>Casos especiales  
 En casos especiales, un modificador de acción color puede usarse de forma independiente como un icono independiente. El color usado para el icono refleja las acciones que está asociado el icono. Este uso está limitado a un pequeño subconjunto de iconos, incluidos:  
  
||||||  
|-|-|-|-|-|  
|![Icono ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "03_ActionModifierRun 0405")<br />Run|![Icono de detención](../../extensibility/ux-guidelines/media/0405-19_stop.png "19_Stop 0405")<br />Detener|![Icono Eliminar](../../extensibility/ux-guidelines/media/0405-20_delete.png "20_Delete 0405")<br />Eliminar|![Icono Guardar](../../extensibility/ux-guidelines/media/0405-21_save.png "21_Save 0405")<br />Guardar|![Icono navegar hacia atrás](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "22_NavigateBack 0405")<br />Navegar hacia atrás|  
  
### <a name="code-hierarchy-palette"></a>Paleta de jerarquía de código  
  
#### <a name="folder"></a>Carpeta  
  
|Uso|Name|Valor (todos los temas)|Muestra|Ejemplo|  
|-----------|----------|--------------------------|------------|-------------|  
|Carpetas|Carpeta|DCB67A / 220,182,122|![Muestra DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icono carpeta de color](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "23_FolderColor 0405")|  
  
#### <a name="visual-studio-languages"></a>Lenguajes de Visual Studio  
 Cada uno de los lenguajes comunes o de plataformas disponibles en Visual Studio tiene un color asociado. Estos colores se utilizan en el icono de base, o acerca de los modificadores de lenguaje que aparecen en la esquina superior derecha de los iconos compuestas.  
  
|Uso|Name|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF azul|0095D 7 / 0,149,215|![Muestra 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP púrpura|9B4F96 / 155,79,150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS verde (VS acción verde)|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Rojo CSS|BD1E2D / 189,30,45|![Muestra BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|FS púrpura|672878 / 103,40,120|![Muestrario 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS naranja|F16421 / 241,100,33|![Muestra F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB azul (Blue acción de VS)|00539C / 0,83,156|![Muestra 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|TS naranja|E04C06 / 224,76,6|![Muestra E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|Copiar verde|879636 / 135,150,54|![Muestrario 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Ejemplos de iconos con modificadores de lenguaje  
  
|||||||  
|-|-|-|-|-|-|  
|![Icono de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "25_VB 0405")<br />VB|![C &#35; icono](../../extensibility/ux-guidelines/media/0405-26_csharp.png "26_CSharp 0405")<br />C#|![C &#43; &#43; icono](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "27_CPlusPlus 0405")<br />C++|![F &#35; icono](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "28_FSharp 0405")<br />F#|![Icono de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "29_JavaScript 0405")<br />JavaScript|![Icono de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "30_Python 0405")<br />Python|  
|![Icono HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "31_HTML 0405")<br />HTML|![Icono WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "32_WPF 0405")<br />WPF|![Icono ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "33_ASP 0405")<br />ASP|![Icono CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "34_CSS 0405")<br />CSS|![Icono de typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "35_TypeScript 0405")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 Iconos de IntelliSense utilizan una paleta de colores exclusivo. Estos colores se usan para ayudar a los usuarios distinguir rápidamente entre los distintos elementos de la lista emergente de IntelliSense.  
  
|Uso|Name|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Clase de evento|VS acción naranja|C27D1A / 194,125,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Método de extensión, método, módulo, delegado|Púrpura de acción de VS|652 90 D / 101,45,144|![Muestra 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Campo, elemento de enumeración, Macro, estructura, tipo de valor de unión, operador, interfaz|Azul de la acción de VS|00539C / 0,83,156|![Muestra 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Objeto|Verde de acción de VS|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Constante, excepción, el elemento de enumeración, mapa, elemento de mapa, Namespace, plantilla, una definición de tipo|Fondo (VS BG)|424242 / 66,66,66|![Muestrario 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Ejemplos de iconos de IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Icono de clase de IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "36_IntelliSenseClass 0405")<br />Clase|![Icono de evento privado de IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "37_IntelliSensePrivateEvent 0405")<br />Evento privado|![Icono de delegado de IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "38_IntelliSenseDelegate 0405")<br />Delegate|![Icono de amigo de método de IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "39_IntelliSenseMethodFriend 0405")<br />Friend (método)|![Icono del campo](../../extensibility/ux-guidelines/media/0405-40_field.png "40_Field 0405")<br />Campo|  
|![IntelliSense protegido icono de elemento de enumeración](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "41_IntelliSenseProtectedEnumItem 0405")<br />Elemento de enumeración protegido|![Icono de objeto de IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "42_IntelliSenseObject 0405")<br />Objeto|![Icono de plantilla de IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "43_IntelliSenseTemplate 0405")<br />Plantilla|![Icono de acceso directo de excepción de IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "44_IntelliSenseExceptionShortcut 0405")<br />Acceso directo de la excepción||  
  
### <a name="notifications"></a>Notificaciones  
 Las notificaciones en Visual Studio se utilizan para indicar el estado. La paleta de notificación usa los siguientes cuatro colores, así como opciones de relleno de primer plano o negro, para definir notificaciones con los siguientes niveles de estado.  
  
|Uso|Name|Valor (todos los temas)|Muestra|  
|-----------|----------|--------------------------|------------|  
|Estado: neutro|Notificación azul (VS azul)|1BA1E2 / 27,161,226|![Muestra 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Estado: positivo|Notificación verde (VS verde)|339933 / 51,153,51|![Muestrario 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Estado: negativo|Notificación rojo (VS rojo)|E51400 / 229,20,0|![Muestra E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Estado: advertencia|Notificación amarillo (VS naranja)|FFCC00 / 255,204,0|![Muestra FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Relleno de primer plano|Notificación negro (negro)|000000 / 0,0,0|![Muestrario &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Relleno de primer plano|Notas de la notificación (blanco)|FFFFFF / 255,255,255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Ejemplos de iconos de notificación  
  
|||||  
|-|-|-|-|  
|![Icono de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "45_Alert 0405")<br />Alerta|![Icono de advertencia](../../extensibility/ux-guidelines/media/0405-48_warning.png "48_Warning 0405")<br />Advertencia|![Icono completa](../../extensibility/ux-guidelines/media/0405-46_complete.png "46_Complete 0405")<br />Completado|![Icono de detención](../../extensibility/ux-guidelines/media/0405-47_stop.png "47_Stop 0405")<br />Detener|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 En general, Visual Studio Online consta de características que se hospedan en un explorador. El color varía en entornos diferentes, pero el estilo sigue siendo el mismo.  
  
|Agrupar|Uso|Name|Valor (todos los temas)|Muestra|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Fondo|TFSO BG|656565/ 101, 101, 101|![Muestrario 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Esquema|TFSO OUT|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Mónaco|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Fondo|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normal|Grey_Primary de F12|555555 / 85, 85, 85|![Muestrario 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
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
|![Icono de equipo de TFS en línea](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "49_TFSOnlineTeam 0405")<br />Equipo en línea|![Icono de información de TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "50_TFSInformation 0405")<br />Información|![Icono de historial TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "51_TFSHistory 0405")<br />Historial|![Icono de bifurcación TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "52_TFSBranch 0405")<br />Rama|  
  
|Napa||||  
|----------|-|-|-|  
|![Icono de contenido de Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "53_NapaContent 0405")<br />Contenido|![Icono de correo electrónico de office de Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "54_NapaOfficeMail 0405")<br />Correo electrónico de Office|![Icono de SharePoint de Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "55_NapaSharePoint 0405")<br />SharePoint|![Icono de panel de tareas de Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "56_NapaTaskPane 0405")<br />Panel de tareas|  
  
|Mónaco||||  
|------------|-|-|-|  
|![Icono de archivos de Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "57_MonacoFiles 0405")<br />Archivos|![Icono de Git de Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "58_MonacoGit 0405")<br />Git|![Icono de búsqueda de Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "59_MonacoSearch 0405")<br />Buscar|![Icono de texto de Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "60_MonacoText 0405")<br />Texto|  
  
|F12|||  
|---------|-|-|  
|![Icono de resaltada de F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "61_F12PrettyCode 0405")<br />Resaltada|![Icono de advertencia de F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "62_F12Warning 0405")<br />Advertencia|![Icono emular de F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "63_F12Emulate 0405")<br />Emular|