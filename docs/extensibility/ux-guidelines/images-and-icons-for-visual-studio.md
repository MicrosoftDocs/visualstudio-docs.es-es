---
title: Imágenes e iconos para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301600"
---
# <a name="images-and-icons-for-visual-studio"></a>Imágenes e iconos para Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Uso de imágenes en Visual Studio
 Antes de crear ilustraciones, considere la posibilidad de usar más de 1.000 imágenes en la biblioteca de imágenes de [Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipos de imágenes

- **Iconos**. Imágenes pequeñas que aparecen en comandos, jerarquías, plantillas, etc. El tamaño de icono predeterminado utilizado en Visual Studio es un PNG de 16x16. Los iconos generados por el servicio de imágenes generan automáticamente el formato XAML para la compatibilidad con HDPI.

    > [!NOTE]
    > Mientras que las imágenes se utilizan en el sistema de menús, no debe crear un icono para cada comando. Consulte [Menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver si el comando debe obtener un icono.

- **Miniaturas.** Imágenes utilizadas en el área de vista previa de un cuadro de diálogo, como el cuadro de diálogo Nuevo proyecto.

- **Imágenes de cuadro de diálogo.** Imágenes que aparecen en cuadros de diálogo o asistentes, ya sea como gráficos descriptivos o indicadores de mensajes. Utilice con poca frecuencia y solo cuando sea necesario para ilustrar un concepto difícil o llamar la atención del usuario (alerta, advertencia).

- **Imágenes animadas.** Se utiliza en indicadores de progreso, barras de estado y cuadros de diálogo de operación.

- **Cursores.** Se utiliza para indicar si se permite una operación con el mouse, donde se puede quitar un objeto, etc.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Diseño de icono

### <a name="overview"></a>Información general
 Visual Studio usa iconos de estilo moderno, que tienen geometría limpia y un equilibrio 50/50 de positivo/negativo (luz/oscuridad) y usan metáforas directas y comprensibles. Los puntos de diseño de iconos cruciales se centran en la claridad, la simplificación y el contexto.

- **Claridad:** concéntrese en la metáfora central que da a un icono su significado e individualidad.

- **Simplificación:** reduzca el icono a su significado central - obtener el tema a través con sólo los elementos necesarios y sin lujos.

- **Contexto:** considerar todos los aspectos del papel de un icono durante el desarrollo del concepto, que es crucial a la hora de decidir qué elementos constituyen la metáfora central del icono.

  Con los iconos, hay una serie de puntos de diseño para evitar:

- No use iconos que signifiquen elementos de interfaz de usuario, excepto cuando corresponda. Elija un enfoque más abstracto o simbólico cuando el elemento de interfaz de usuario no es común, evidente ni único.

- No utilice en exceso elementos comunes como documentos, carpetas, flechas y la lupa. Utilice estos elementos sólo cuando sea esencial para el significado del icono. Por ejemplo, la lupa orientada a la derecha debe indicar solo Buscar, Examinar y Buscar.

- Aunque algunos elementos de icono heredados mantienen el uso de la perspectiva, no cree nuevos iconos con perspectiva a menos que el elemento carezca de claridad sin él.

- No abarques demasiada información en un icono. Una imagen simple que se puede reconocer o aprender fácilmente como un símbolo reconocible es mucho más útil que una imagen demasiado compleja. Un icono no puede contar toda la historia.

### <a name="icon-creation"></a>Creación de iconos

#### <a name="concept-development"></a>Desarrollo de conceptos
 Visual Studio tiene dentro de su interfaz de usuario una amplia variedad de tipos de icono. Considere cuidadosamente el tipo de icono durante el desarrollo. No utilice objetos de interfaz de usuario poco claros o poco comunes para los elementos de icono. Opte por el símbolo en estos casos, como con el icono de etiqueta inteligente. Tenga en cuenta que el significado de la etiqueta abstracta de la izquierda es más obvio que la vaga versión basada en la interfaz de usuario de la derecha:

|||
|-|-|
|**Uso correcto de imágenes simbólicas**|**Uso incorrecto de imágenes simbólicas**|
|![Icono de etiqueta inteligente correcta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icono de etiqueta inteligente incorrecta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Hay casos en los que los elementos de interfaz de usuario estándar y fácilmente reconocibles funcionan bien para los iconos. Agregar ventana es uno de estos ejemplos:

|||
|-|-|
|**Elemento de interfaz de usuario correcto en un icono**|**Elemento de interfaz de usuario incorrecto en un icono**|
|![Icono de agregar ventana correcto](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icono de agregar ventana incorrecto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 No utilice un documento como elemento base a menos que sea esencial para el significado del icono. Sin el elemento de documento en Agregar documento (abajo) se pierde el significado, mientras que con Actualizar el elemento de documento no es necesario comunicar el significado.

|||
|-|-|
|**Uso correcto del icono del documento**|**Uso incorrecto del icono del documento**|
|![Icono de documento correcto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icono de documento incorrecto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 El concepto de "show" debe estar representado por el icono que mejor ilustra lo que se muestra, como con el ejemplo Mostrar todos los archivos. Una metáfora de lente se puede utilizar para indicar el concepto de "vista" si es necesario, como con el ejemplo de la vista de recursos.

|||
|-|-|
|**"Espectáculo"**|**"Vista"**|
|![Icono Mostrar](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icono Vista](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 El icono de lupa orientado a la derecha solo debe representar Buscar, Buscar y Examinar. La variante orientada a la izquierda con el signo más o signo menos debe representar solo acercar/alejar.

|||
|-|-|
|**"Buscar"**|**"Zoom"**|
|![Icono de búsqueda](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icono Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 En las vistas de árbol, no utilice el icono de carpeta ni un modificador. Cuando esté disponible, utilice solo el modificador.

|||
|-|-|
|**Iconos de vista de árbol correctos**|**Iconos de vista de árbol incorrectos**|
|![El icono de vista de árbol correcto &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") icono Corregir vista de árbol &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icono](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") de vista de árbol incorrecto &#40;1&#41;Icono de vista de árbol incorrecto &#40;2 ![&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Detalles de estilo

#### <a name="layout"></a>Diseño
 Elementos de pila como se muestra para los iconos estándar de 16x16:

 ![Pila de diseño para los iconos de 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pila de diseño para los iconos de 16 x 16

 Los elementos de notificación de estado se utilizan mejor como iconos independientes. Sin embargo, hay contextos en los que se debe apilar una notificación en el elemento base, como con el icono Tarea completada:

 ![Notificaciones independientes en Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Iconos de notificación independientes

 ![Icono de tarea completa](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icono Tarea completada

 Los iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. La mayoría de los iconos 16x16 contienen los mismos elementos. Las versiones 32x32 tienen más detalles, incluido el tipo de proyecto cuando corresponda.

 ![Iconos de proyecto en Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Iconos del proyecto de la biblioteca de control de Windows de VB, 16x16 y 32x32

 Centra un icono dentro de su marco de píxeles. Si eso no es posible, alinee el icono con la parte superior y/o derecha del marco.

 ![Icono centrado en el fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icono centrado en el fotograma de píxeles

 ![Icono alineado en la parte superior derecha del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icono alineado a la parte superior derecha del marco

 ![Icono centrado y alineado en la parte superior del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icono centrado y alineado a la parte superior del marco

 Para lograr una alineación y un equilibrio ideales, evite obstruir el elemento base del icono con glifos de acción. Coloque el glifo cerca de la parte superior izquierda del elemento base. Al agregar un elemento adicional, tenga en cuenta la alineación y el equilibrio del icono.

|||
|-|-|
|**Alineación y equilibrio correctos**|**Alineación y equilibrio incorrectos**|
|![Equilibrio y alineación correctos de los iconos](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio y alineación incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Asegúrese de la paridad de tamaño para los iconos que comparten elementos y se utilizan en conjuntos. Tenga en cuenta que en el emparejamiento incorrecto, el círculo y la flecha están sobredimensionados y no coinciden.

|||
|-|-|
|**Paridad de tamaño correcta**|**Paridad de tamaño incorrecta**|
|![Tamaño y paridad correctos de los iconos](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Tamaño y paridad incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Utilice grosores visuales y de línea coherentes. Evalúe cómo se compara el icono que está creando con otros iconos mediante una comparación en paralelo. Nunca utilice toda la trama de 16x16, utilice 15x15 o más pequeño. La relación negativo-positivo (oscuro-claro) debe ser 50/50.

|||
|-|-|
|**Relación negativa-positiva correcta**|**Relación negativa-positiva incorrecta**|
|![Peso visual correcto para iconos &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Peso visual correcto para iconos &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Peso visual correcto para iconos &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Grosor visual incorrecto para iconos](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Utilice formas simples y comparables y ángulos complementarios para construir sus elementos sin sacrificar la integridad de los elementos. Utilice ángulos de 45o o 90o siempre que sea posible.

 ![Ángulos de icono correctos](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspectiva
 Mantenga el icono claro y comprensible. Utilice la perspectiva y una fuente de luz solo cuando sea necesario. Aunque se debe evitar el uso de perspectiva en elementos de icono, algunos elementos son irreconocibles sin él. En tales casos, una perspectiva estilizada comunica la claridad del elemento.

 ![Perspectiva de 3 puntos](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspectiva de 3 puntos

 ![Perspectiva de 1 punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspectiva de 1 punto

 La mayoría de los elementos deben estar orientados o en ángulo a la derecha:

 ![Iconos en ángulo derecho](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Utilice fuentes de luz solo cuando añada la claridad necesaria a un objeto.

|||
|-|-|
|**Fuente de luz correcta**|**Fuente de luz incorrecta**|
|![Fuentes de luz correctas para iconos](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Fuentes de luz incorrectas para iconos](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Utilice contornos solo para mejorar la legibilidad o para comunicar mejor la metáfora. El balance negativo-positivo (luz oscura) debe ser 50/50.

|||
|-|-|
|**Uso correcto de esquemas**|**Uso incorrecto de contornos**|
|![Contornos correctos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Contornos incorrectos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipos de icono
 Los iconos de shell y barra de **comandos** constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de shell y barra de comandos](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Ejemplos de iconos de shell y barra de comandos

 Los iconos de la barra de **comandos** de la ventana de herramientas constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de la barra de comandos de la ventana de herramientas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Ejemplos de iconos de la barra de comandos de la ventana de herramientas

 Los iconos de **desambiguator** de vista de árbol constan de no más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de desambiguadores de vista de árbol](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Ejemplos de iconos de desambiguadores de vista de árbol

 Los iconos de taxonomía de **valores basados** en estado existen en los siguientes estados: activo, deshabilitado activo e inactivo deshabilitado.

 ![Ejemplos de iconos de taxonomía de valor basados en el estado](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Ejemplos de iconos de taxonomía de valor basados en el estado

 Los iconos de **IntelliSense** constan de no más de tres de los siguientes elementos: una base, un modificador y un estado.

 ![Ejemplos de iconos de IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Ejemplos de iconos de IntelliSense

 Los iconos de **proyecto pequeños (16x16)** no deben tener más de dos elementos: una base y un modificador.

 ![Ejemplos de iconos de proyecto pequeños (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") icono de ![proyecto 16x16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") icono de proyecto de ![16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Ejemplos de iconos de proyectos pequeños (16x16)

 Los iconos de **proyecto grandes (32x32)** constan de no más de cuatro de los siguientes elementos: una base, uno a dos modificadores y una superposición de idioma.

 ![Ejemplos de iconos de proyecto grandes (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Ejemplos de iconos de proyecto grandes (32x32)

### <a name="production-details"></a>Detalles de la producción
 Todos los nuevos elementos de interfaz de usuario se deben crear con Windows Presentation Foundation (WPF) y todos los iconos nuevos para WPFWPF deben estar en formato PNG de 32 bits. El PNG de 24 bits es un formato heredado que no admite transparencia y, por lo tanto, no se recomienda para iconos.

 Guarde la resolución a 96 DPI.

#### <a name="file-types"></a>Tipos de archivo

- **PNG de 32 bits:** el formato preferido para los iconos. Formato de archivo de compresión de datos sin pérdidas que puede almacenar una sola imagen ráster (píxel). Los archivos PNG de 32 bits admiten transparencia de canal alfa, corrección gamma y entrelazado.

- **BMP de 32 bits:** para controles que no son DEWPF. También llamado XP o de color alto, BMP de 32 bits es un formato de imagen RGB/A, una imagen de color verdadero con una transparencia de canal alfa. El canal alfa es una capa de transparencia designada en Adobe Photoshop que, a continuación, se guarda dentro del mapa de bits como un canal de color adicional (cuarto). Se añade un fondo negro durante la producción de ilustraciones a todos los archivos BMP de 32 bits para proporcionar una indicación visual rápida sobre la profundidad de color. Este fondo negro representa el área que se va a enmascarar en la interfaz de usuario.

- **ICO de 32 bits:** para iconos de proyecto y Agregar elemento. Todos los archivos ICO son de color verdadero de 32 bits con transparencia de canal alfa (RGB/A). Dado que los archivos ICO pueden almacenar varios tamaños y profundidades de color, los iconos de Vista suelen estar en un formato ICO que contiene tamaños de imagen de 16x16, 32x32, 48x48 y 256x256. Para que se muestren correctamente en el Explorador de Windows, los archivos ICO deben guardarse en profundidades de color de 24 bits y 8 bits para cada tamaño de imagen.

- **XAML:** para superficies de diseño y adornos de Windows. Los iconos XAML son archivos de imagen basados en vectores que admiten escalado, rotación, archivado y transparencia. No son comunes en Visual Studio hoy en día, pero se están volviendo más populares debido a su flexibilidad.

- **SVG**

- **BMP de 24 bits:** para la barra de comandos de Visual Studio. Un formato de imagen RGB de color verdadero, BMP de 24 bits es una convención de icono que crea una capa de transparencia mediante el uso de magenta (R-255, G-0, B-255) como una clave de color para una capa de transparencia knock-out. En un BMP de 24 bits, todas las superficies magenta se muestran utilizando el color de fondo.

- **GIF de 24 bits:** para la barra de comandos de Visual Studio. Un formato de imagen RGB de color verdadero que admite transparencia. Los archivos GIF se utilizan a menudo en ilustraciones del asistente y animaciones GIF.

### <a name="icon-construction"></a>Construcción de icono
 El tamaño de icono más pequeño de Visual Studio es 16x16. El más grande en uso común es 32x32. Tenga en cuenta no llenar todo el marco de 16x16, 24x24 o 32x32 al diseñar un icono. La construcción de iconos legibles y uniformes es esencial para el reconocimiento del usuario. Adherirse a los siguientes puntos al crear iconos.

- Los iconos deben ser claros, comprensibles y coherentes.

- Es mejor utilizar los elementos de notificación de estado como iconos únicos y no apilarlos encima de un elemento base de icono. En determinados contextos, la interfaz de usuario puede requerir que el elemento de estado se empareje con un elemento base.

- Los iconos de proyecto suelen ser archivos .ico que contienen varios tamaños. Solo se actualizan los iconos 16x16, 24x24 y 32x32. La mayoría de los iconos 16x16 y 24x24 contendrán los mismos elementos. Los iconos de 32x32 contienen más detalles, incluido el tipo de idioma del proyecto cuando corresponda.

- Para los iconos de 32x32, los elementos base generalmente tienen un grosor de línea de 2 píxeles. Se puede utilizar un grosor de línea de 1 o 2 píxeles para los elementos de detalle. Utilice su mejor criterio para determinar cuál es más adecuado.

- Tener al menos un espaciado de 1 píxel entre los elementos para los iconos 16x16 y 24x24. Para iconos de 32x32, utilice el espaciado de 2 píxeles entre los elementos y entre el modificador y el elemento base.

  ![Espaciado de elementos para iconos de tamaño 16x16, 24x24 y 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espaciado de elementos para iconos de tamaño 16x16, 24x24 y 32x32

#### <a name="color-and-accessibility"></a>Color y accesibilidad
 Las directrices de cumplimiento de Visual Studio requieren que todos los iconos del producto superen los requisitos de accesibilidad para el color y el contraste. Esto se logra a través de la inversión de icono, y cuando usted está diseñando, usted debe ser consciente de que se invertirán mediante programación en el producto.

 Para obtener más información sobre el uso del color en los iconos de Visual Studio, vea [Uso del color en imágenes](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Uso del color en imágenes

### <a name="overview"></a>Información general
 Los iconos de Visual Studio son principalmente monocromáticos. El color está reservado para transmitir información específica y nunca para la decoración. Se utiliza el color:

- para indicar una acción

- para alertar al usuario de una notificación de estado

- designar afiliación al idioma

- para diferenciar elementos dentro de IntelliSense

### <a name="accessibility"></a>Accesibilidad
 Las directrices de cumplimiento de Visual Studio requieren que todos los iconos registrados en el producto superen los requisitos de accesibilidad para el color y el contraste. Los colores de la paleta de idiomas visuales se han probado y cumplen estos requisitos.

#### <a name="color-inversion-for-dark-themes"></a>Inversión de color para temas oscuros
 Para que los iconos aparezcan con la relación de contraste correcta en el tema oscuro de Visual Studio, se aplica una inversión mediante programación. Los colores de esta guía se han elegido en parte para que se inviertan correctamente. Restringe el uso del color a esta paleta, o obtendrá resultados impredecibles cuando se aplique la inversión.

 ![Ejemplos de iconos que han invertido sus colores](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Ejemplos de iconos que han invertido sus colores

### <a name="base-palette"></a>Paleta base
 Todos los iconos estándar contienen tres colores base. Los iconos no contienen degradados ni sombras paralelas, con una o dos excepciones para los iconos de herramientas 3D.

|Uso|Nombre|Valor (tema de luz)|Swatch|Ejemplo|
|-----------|----------|---------------------------|------------|-------------|
|Fondo/Oscuro|VS BG|424242 / 66,66,66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Ejemplo de paleta básica](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primer plano/luz|VS FG|F0EFF1 / 240.239.241|![Muestra F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Esquema|VS Out|F6F6F6 / 246.246.246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Además de los colores base, cada icono puede contener un color adicional de la paleta extendida.

### <a name="extended-palette"></a>Paleta extendida

#### <a name="action-modifiers"></a>Modificadores de acción
 Los cuatro colores siguientes indican los tipos de acciones requeridas por los modificadores de acción:

|Uso|Nombre|Valor (todos los temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Positive|VS Acción Verde|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negative|VS Acción Rojo|A1260D / 161,38,13|![Muestra A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutra|VS Action Blue|00539C / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crear/Nuevo|VS Acción Naranja|C27D1A / 194.156,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Ejemplos
 El verde se utiliza para modificadores de acción positiva como "Agregar", "Ejecutar", "Reproducir" y "Validar".

|||||
|-|-|-|-|
|![Icono Ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Ejecute|![Icono Ejecutar consulta](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")<br />Ejecutar consulta|![Icono Reproducir todos los pasos](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")<br />Reproducir todos los pasos|![Icono Agregar control](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")<br />Añadir control|

 El rojo se utiliza para modificadores de acción negativos como "Eliminar", "Detener", "Cancelar" y "Cerrar."

|||||
|-|-|-|-|
|![Icono Eliminar relación](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")<br />Eliminar relación|![Icono Eliminar columna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")<br />Eliminar columna|![Icono Detener consulta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")<br />Detener consulta|![Icono Sin conexión](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")<br />Conexión sin conexión|

 El azul se aplica a los modificadores de acción neutral más comúnmente representados como flechas, como "Abrir", "Siguiente", "Anterior", "Importar" y "Exportar."

|||||
|-|-|-|-|
|![Icono Ir al campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")<br />Ir al campo|![El&#45;de registro por lotes en el icono](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")<br />Check-In por lotes|![Icono de editor de direcciones](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")<br />Editor de direcciones|![Icono de editor de asociación](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")<br />Editor de la Asociación|

 El oro oscuro se utiliza principalmente para el modificador "Nuevo".

|||||
|-|-|-|-|
|![Icono de proyecto nuevo](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")<br />Nuevo proyecto|![Icono Crear nuevo gráfico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")<br />Crear nuevo gráfico|![Icono Nueva prueba unitaria](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")<br />Nueva prueba unitaria|![Icono Nuevo elemento de lista](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")<br />Nuevo elemento de lista|

#### <a name="special-cases"></a>Casos especiales
 En casos especiales, un modificador de acción de color se puede utilizar de forma independiente como un icono independiente. El color utilizado para el icono refleja las acciones a las que está asociado el icono. Este uso se limita a un pequeño subconjunto de iconos, incluyendo:

||||||
|-|-|-|-|-|
|![Icono Ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")<br />Ejecute|![Icono de detención](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")<br />Stop|![Icono Eliminar](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")<br />Eliminar|![Icono Save (Guardar)](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")<br />Save|![Icono Navegar hacia atrás](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")<br />Navegar hacia atrás|

### <a name="code-hierarchy-palette"></a>Paleta de jerarquía de código

#### <a name="folder"></a>Carpeta

|Uso|Nombre|Valor (todos los temas)|Swatch|Ejemplo|
|-----------|----------|--------------------------|------------|-------------|
|Carpetas|Carpeta|DCB67A / 220,182,122|![Muestra DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icono Carpeta de color](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Idiomas de Visual Studio
 Cada uno de los lenguajes comunes o plataformas disponibles en Visual Studio tiene un color asociado. Estos colores se utilizan en el icono base o en los modificadores de idioma que aparecen en la esquina superior derecha de los iconos compuestos.

|Uso|Nombre|Valor (todos los temas)|Swatch|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF Azul|0095D7 / 0,149,215|![Muestra 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|CPP Purple|9B4F96 / 155,79,150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|CS Verde (VS Action Green)|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|CSS Rojo|BD1E2D / 189,30,45|![Muestra BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|FS Purple|672878 / 103,40,120|![Muestra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|JS Orange|F16421 / 241,100,33|![Muestra F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|AZUL VB (azul de acción VS)|00539C / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|TS Orange|E04C06 / 224,76,6|![Muestra E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY Green|879636 / 135,150,54|![Muestra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Ejemplos de iconos con modificadores de idioma

|||||||
|-|-|-|-|-|-|
|![Icono de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")<br />VB|![Icono de&#35; C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")<br />C#|![C icono&#43;&#43; ](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")<br />C++|![Icono de&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")<br />F#|![Icono de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")<br />JavaScript|![Icono de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")<br />Python|
|![Icono de HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icono de WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icono de ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icono de CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icono de TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Los iconos de IntelliSense utilizan una paleta de colores exclusiva. Estos colores se utilizan para ayudar a los usuarios a distinguir rápidamente entre los diferentes elementos de la lista emergente de IntelliSense.

|Uso|Nombre|Valor (todos los temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Clase, Evento|VS Acción Naranja|C27D1A / 194.125,26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Método de extensión, método, módulo, delegado|VS Acción Púrpura|652D90 / 101,45,144|![Muestra 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, Elemento de enumeración, Macro, Estructura, Tipo de valor de unión, Operador, Interfaz|VS Action Blue|00539C / 0,83,156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|VS Acción Verde|388A34 / 56,138,52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, Excepción, Elemento de enumeración, Mapa, Elemento de mapa, Espacio de nombres, Plantilla, Definición de tipo|Fondo (VS BG)|424242 / 66,66,66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Ejemplos de iconos de IntelliSense

||||||
|-|-|-|-|-|
|![Icono de clase de IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")<br />Clase|![Icono de evento privado de IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")<br />Evento privado|![Icono de delegado de IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")<br />Delegar|![Icono de amigo de método de IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")<br />Amigo del método|![Icono de campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")<br />Campo|
|![Icono de elemento de enumeración protegida de IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")<br />Artículo de enum protegido|![Icono de objeto de IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")<br />Object|![Icono de plantilla de IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")<br />Plantilla|![Icono de acceso directo a excepción de IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")<br />Acceso directo a excepciones||

### <a name="notifications"></a>Notificaciones
 Las notificaciones en Visual Studio se usan para indicar el estado. La paleta de notificaciones utiliza los cuatro colores siguientes, así como las opciones de relleno de primer plano en blanco o negro, para definir notificaciones con los siguientes niveles de estado.

|Uso|Nombre|Valor (todos los temas)|Swatch|
|-----------|----------|--------------------------|------------|
|Estado: neutral|Azul de notificación (AZUL VS)|1BA1E2 / 27.161.226|![Muestra 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Estado: positivo|Notificación verde (verde VS)|339933 / 51,153,51|![Muestra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Estado: negativo|Notificación roja (VS Rojo)|E51400 / 229,20,0|![Muestra E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Estado: advertencia|Notificación amarilla (VS naranja)|FFCC00 / 255,204,0|![Muestra FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Relleno de primer plano|Notificación Negro (Negro)|000000 / 0,0,0|![Swatch &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Relleno de primer plano|Notificación blanco (blanco)|FFFFFF / 255.255.255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Ejemplos de iconos de notificación

|||||
|-|-|-|-|
|![Icono de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")<br />Alerta|![Icono de advertencia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")<br />Advertencia|![Icono de Completado](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")<br />Operación completada|![Icono de detención](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")<br />Stop|

### <a name="visual-studio-online"></a>Visual Studio Online
 En general, Visual Studio Online consta de características hospedadas en un explorador. El color varía en diferentes ambientes, pero el estilo sigue siendo el mismo.

|Grupo|Uso|Nombre|Valor (todos los temas)|Swatch|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Información previa|TFSO BG|656565/ 101, 101, 101|![Muestra 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Esquema|TFSO OUT|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Información previa|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Mónaco|Información previa|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Información previa|Blanco|FFFFFF / 255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normal|F12 Grey_Primary|555555 / 85, 85, 85|![Muestra 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Al mantener el puntero|F12 Blue_Hover|2279BF / 34,121,191|![Muestra 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Disabled|F12 LtGrey_Disabled|ABABAC / 171.171.172|![Muestra ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Pase el ratón por el fondo|Hover bg|D9EBF7 / 217.235.247|![Muestra D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Fondo prensado|Presionado bg|B2D7F0 / 178.215.240|![Muestra B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Esquema|VS OUT|F6F6F6 / 246.246.246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Information|Information|00BCF2 / 0,188,242|![Muestra 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Advertencia|Advertencia|F28300 / 242.131,0|![Muestra F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Error / Negativo|Error_Negative|E81123 / 232,17,35|![Muestra E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Inicio / Positivo|Start_Positive|009E49 / 0,158,73|![Muestra 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Tipo de rotura|Tipo de rotura|9B4F96 / 155,79,150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Marca del evento|Marca del evento|A51F00 / 165,31,0|![Muestra A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Marca de usuario|Marca de usuario|F16220 / 241,98,32|![Muestra F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Ejemplos de iconos de Visual Studio Online

|TFS Online||||
|----------------|-|-|-|
|![Icono de equipo de TFS en línea](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405-49_TFSOnlineTeam")<br />Equipo en línea|![Icono de información de TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50_TFSInformation")<br />Information|![Icono de historial de TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405-51_TFSHistory")<br />Historial|![Icono de bifurcación de TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405-52_TFSBranch")<br />Rama|

|Napa||||
|----------|-|-|-|
|![Icono de contenido de Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405-53_NapaContent")<br />Contenido|![Icono de correo electrónico de Office de Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405-54_NapaOfficeMail")<br />Correo de oficina|![Icono de SharePoint de Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405-55_NapaSharePoint")<br />SharePoint|![Icono de panel de tareas de Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405-56_NapaTaskPane")<br />Panel de tareas|

|Mónaco||||
|------------|-|-|-|
|![Icono de archivos de Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405-57_MonacoFiles")<br />Archivos|![Icono de Git de Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405-58_MonacoGit")<br />Git|![Icono de búsqueda de Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405-59_MonacoSearch")<br />Search|![Icono de texto de Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405-60_MonacoText")<br />Texto|

|F12|||
|---------|-|-|
|![Icono de sintaxis resaltada de F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405-61_F12PrettyCode")<br />Pretty Code|![Icono de advertencia de F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405-62_F12Warning")<br />Advertencia|![Icono Emular de F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405-63_F12Emulate")<br />Emular|