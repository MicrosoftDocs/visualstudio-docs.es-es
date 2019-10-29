---
title: Imágenes e iconos de Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e449fb30bd95319a46d1db50da63778f6800a70
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983869"
---
# <a name="images-and-icons-for-visual-studio"></a>Imágenes e iconos de Visual Studio
## <a name="BKMK_ImageUseInVisualStudio"></a>Uso de imágenes en Visual Studio
 Antes de crear material gráfico, considere la posibilidad de utilizar las más de 1000 imágenes en la [biblioteca de imágenes de Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipos de imágenes

- **Iconos**. Imágenes pequeñas que aparecen en comandos, jerarquías, plantillas, etc. El tamaño de icono predeterminado que se usa en Visual Studio es un PNG de 16x16. Los iconos generados por el servicio de imágenes generan automáticamente el formato XAML para la compatibilidad con HDPI.

    > [!NOTE]
    > Mientras que las imágenes se usan en el sistema de menús, no debe crear un icono para cada comando. Consulte [menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver si el comando debe obtener un icono.

- **Miniaturas.** Imágenes usadas en el área de vista previa de un cuadro de diálogo, como el cuadro de diálogo nuevo proyecto.

- **Imágenes de cuadro de diálogo.** Imágenes que aparecen en los cuadros de diálogo o los asistentes, ya sea como gráficos descriptivos o indicadores de mensaje. Use con poca frecuencia y solo cuando sea necesario para ilustrar un concepto difícil u obtener la atención del usuario (alerta, ADVERTENCIA).

- **Imágenes animadas.** Se usa en indicadores de progreso, barras de estado y cuadros de diálogo de operaciones.

- **Cursores.** Se utiliza para indicar si se permite una operación con el mouse, dónde se puede quitar un objeto, etc.

## <a name="BKMK_IconDesign"></a>Diseño de iconos

### <a name="overview"></a>Información general
 Visual Studio usa iconos de estilo moderno, que tienen geometría limpia y un equilibrio de 50/50 de positivo/negativo (claro/oscuro) y usan metáforas directas y comprensibles. Los puntos de diseño de iconos cruciales se centran en la claridad, la simplificación y el contexto.

- **Claridad:** céntrese en la metáfora principal que proporciona un icono de su significado y de su propiaidad.

- **Simplificación:** reduzca el icono a su significado principal: obtenga el tema con solo los elementos necesarios y sin frills.

- **Contexto:** tenga en cuenta todos los aspectos del rol de un icono durante el desarrollo del concepto, lo que es fundamental a la hora de decidir qué elementos constituyen la metáfora principal del icono.

  Con los iconos, hay una serie de puntos de diseño para evitar:

- No use iconos que representen elementos de la interfaz de usuario excepto cuando sea apropiado. Elija un enfoque más abstracto o simbólico si el elemento de la interfaz de usuario no es común, evidente ni único.

- No abusos de elementos comunes como documentos, carpetas, flechas y la lupa. Use estos elementos solo cuando sea esencial para el significado del icono. Por ejemplo, la lupa que apunta a la derecha debe indicar solo buscar, examinar y buscar.

- Aunque algunos elementos de icono heredado mantienen el uso de la perspectiva, no cree nuevos iconos con perspectiva a menos que el elemento no tenga claridad sin él.

- No CRAM demasiada información en un icono. Una imagen simple que se puede reconocer o aprender fácilmente como un símbolo reconocible es mucho más útil que una imagen demasiado compleja. Un icono no puede indicar la historia completa.

### <a name="icon-creation"></a>Creación de iconos

#### <a name="concept-development"></a>Desarrollo de concepto
 Visual Studio tiene dentro de la interfaz de usuario una gran variedad de tipos de iconos. Considere cuidadosamente el tipo de icono durante el desarrollo. No use objetos de interfaz de usuario no claros o infrecuentes para los elementos de icono. Optar por el simbólico en estos casos, como con el icono de la etiqueta inteligente. Tenga en cuenta que el significado de la etiqueta abstracta de la izquierda es más obvio que la versión imprecisa basada en la interfaz de usuario a la derecha:

|||
|-|-|
|**Uso correcto de imágenes simbólicas**|**Uso incorrecto de imágenes simbólicas**|
|![Icono corregir etiqueta inteligente](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01 _SmartTagCorrect")|![Icono de etiqueta inteligente incorrecto](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 -02 _SmartTagIncorrect")|

 Hay instancias en las que los elementos de interfaz de usuario estándar y fácilmente reconocibles funcionan bien para los iconos. Agregar ventana es un ejemplo de este tipo:

|||
|-|-|
|**Corregir el elemento de la interfaz de usuario en un icono**|**Elemento de interfaz de usuario incorrecto en un icono**|
|![Icono Agregar ventana correcta](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 -03 _AddWindowCorrect")|![Icono Agregar ventana incorrecta](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 -04 _AddWindowIncorrect")|

 No utilice un documento como elemento base a menos que sea esencial para el significado del icono. Sin el elemento de documento en agregar documento (abajo), se pierde el significado, mientras que al actualizar el elemento de documento no es necesario comunicar el significado.

|||
|-|-|
|**Uso correcto del icono de documento**|**Uso incorrecto del icono de documento**|
|![Icono de documento correcto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 -05 _DocumentIconCorrect")|![Icono de documento incorrecto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 -06 _DocumentIconIncorrect")|

 El concepto de "Mostrar" debe estar representado por el icono que mejor ilustra lo que se muestra, como sucede en el ejemplo de Mostrar todos los archivos. Se puede usar una metáfora de lente para indicar el concepto de "vista" si es necesario, como en el ejemplo Vista de recursos.

|||
|-|-|
|**Feria**|**Visores**|
|![Mostrar icono](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 -07 _ Mostrar")|![Icono de vista](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 -08 _View")|

 El icono de lupa hacia la derecha debe representar solo buscar, buscar y examinar. La variante de la izquierda con el signo más o el signo menos solo debe representar o alejar.

|||
|-|-|
|**Buscan**|**General**|
|![Icono de búsqueda](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 -09 _ Search")|![Icono de zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 -10 _Zoom")|

 En las vistas de árbol, no utilice el icono de carpeta y un modificador. Si está disponible, use solo el modificador.

|||
|-|-|
|**Iconos de vista de árbol correctos**|**Iconos de vista de árbol incorrectos**|
|![Icono &#40;de vista de árbol&#41; correcto 1](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 -11 _TreeViewCorrect1") ![ &#40;icono de vista&#41; de árbol correcto 2](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 -12 _TreeViewCorrect2")|![Icono &#40;de vista de árbol&#41; incorrecto 1](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 -13 _TreeViewIncorrect1") ![ &#40;icono de vista&#41; de árbol incorrecta 2](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 -14 _TreeViewIncorrect2")|

### <a name="style-details"></a>Detalles de estilo

#### <a name="layout"></a>Diseño
 Elementos de la pila como se muestra para los iconos estándar de 16x16:

 ![Pila de diseño para iconos de 16x16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 errores _LayoutStack")<br />Pila de diseño para los iconos de 16 x 16

 Los elementos de notificación de estado se usan mejor como iconos independientes. Sin embargo, hay contextos en los que una notificación se debe apilar en el elemento base, como con el icono de tarea completada:

 ![Notificaciones independientes en Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16 _StandaloneNotificationIcons")<br />Iconos de notificación independientes

 ![Icono de tarea completada](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 -17 _TaskComplete")<br />Icono de tarea completada

 Los iconos de proyecto suelen ser archivos. ico que contienen varios tamaños. La mayoría de los iconos de 16x16 contienen los mismos elementos. Las versiones de 32x32 tienen más detalles, incluido el tipo de proyecto cuando proceda.

 ![Iconos de proyecto en Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 -18 _IconProjectThreeSizes")<br />Iconos de proyecto de biblioteca de controles de Windows de VB, 16x16 y 32x32

 Centrar un icono dentro de su marco de píxeles. Si eso no es posible, alinee el icono con la parte superior o derecha del marco.

 ![Icono centrado en el marco de píxeles](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 -19 _IconCentered")<br />Icono centrado en el fotograma de píxeles

 ![Icono alineado en la parte superior derecha del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 -20 _IconTopRight")<br />Icono alineado en la parte superior derecha del marco

 ![Icono centrado y alineado en la parte superior del marco de píxeles](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 -21 _IconTopAlign")<br />Icono centrado y alineado en la parte superior del marco

 Para lograr una alineación y un equilibrio ideales, evite obstruir el elemento base del icono con glifos de acción. Coloque el glifo cerca de la parte superior izquierda del elemento base. Al agregar un elemento adicional, tenga en cuenta la alineación y el equilibrio del icono.

|||
|-|-|
|**Corregir la alineación y el equilibrio**|**Alineación y equilibrio incorrectos**|
|![Equilibrio de icono y alineación correctos](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 -22 _AlignBalanceCorrect")|![Equilibrio de icono y alineación incorrectos](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 -23 _AlignBalanceIncorrect")|

 Asegúrese de que la paridad de tamaño para los iconos que comparten elementos y se usan en conjuntos. Tenga en cuenta que, en el emparejamiento incorrecto, el círculo y la flecha tienen un tamaño y no coinciden.

|||
|-|-|
|**Paridad de tamaño correcta**|**Paridad de tamaño incorrecta**|
|![Tamaño y paridad correctos de los iconos](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 -24 _SizeParityCorrect")|![Tamaño y paridad de icono incorrectos](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 -25 _SizeParityIncorrect")|

 Use los pesos de línea y visual coherentes. Evalúe el modo en que el icono que va a compilar se compara con otros iconos usando una comparación en paralelo. Nunca use el marco 16x16 completo, use 15x15 o inferior. La relación de negativo a positivo (oscuro a claro) debe ser 50/50.

|||
|-|-|
|**Relación de negativo a positivo correcta**|**Relación de negativo a positivo incorrecta**|
|![Peso visual correcto para los &#40;iconos 1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 -26 _VisualWeightCorrect1")<br /><br /> ![Peso visual correcto para iconos &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 -27 _VisualWeightCorrect2)<br /><br /> ![Peso visual correcto para los &#40;iconos 3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 -28 _VisualWeightCorrect3)|![Peso visual incorrecto para los iconos](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 -29 _VisualWeightIncorrect")|

 Use formas simples, comparables y ángulos complementarios para crear sus elementos sin sacrificar la integridad de los elementos. Use los ángulos 45 ° o 90 ° siempre que sea posible.

 ![Ángulos de icono correctos](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 -30 _IconAnglesCorrect")

#### <a name="perspective"></a>Perspectiva
 Mantenga el icono claro y comprensible. Use la perspectiva y una fuente de luz solo cuando sea necesario. Aunque debe evitarse el uso de la perspectiva en los elementos de icono, algunos elementos son irreconocibles sin él. En tales casos, una perspectiva estilizada comunica la claridad del elemento.

 ![perspectiva de 3 puntos](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 -31 _3PointPerspective")<br />Perspectiva de 3 puntos

 ![perspectiva de punto 1](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 -32 _1PointPerspective")<br />Perspectiva de 1 punto

 La mayoría de los elementos deben estar orientados o inclinados hacia la derecha:

 ![Iconos en ángulo recto](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 -33 _AngledRight")

 Use fuentes ligeras solo cuando agregue la claridad necesaria a un objeto.

|||
|-|-|
|**Fuente de luz correcta**|**Fuente de luz incorrecta**|
|![Corregir fuentes de luz para iconos](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 -34 _LightSourcesCorrect")|![Fuentes de luz incorrectas para iconos](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 -35 _LightSourcesIncorrect")|

 Use los esquemas solo para mejorar la legibilidad o para comunicar mejor la metáfora. El saldo positivo negativo (oscuro claro) debe ser 50/50.

|||
|-|-|
|**Uso correcto de los esquemas**|**Uso incorrecto de los esquemas**|
|![Corregir contornos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 -36 _OutlinesCorrect")|![Contornos incorrectos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 -37 _OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipos de icono
 Los iconos de **Shell y de barra de comandos** no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de Shell y de barra de comandos](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 -38 _ShellIcons")<br />Ejemplos de iconos de Shell y de barra de comandos

 Los iconos de la barra de comandos de la **ventana de herramientas** no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de la barra de comandos de la ventana de herramientas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 -39 _ToolWindowCommandBarIcons")<br />Ejemplos de iconos de la barra de comandos de la ventana de herramientas

 Los iconos de **desambiguamiento** de la vista de árbol no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de desambiguación de vista de árbol](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 -40 _TreeViewIcons")<br />Ejemplos de iconos de desambiguación de vista de árbol

 Los iconos de **taxonomía de valores basados en estado** existen en los siguientes Estados: activo, activo deshabilitado e inactivo deshabilitado.

 ![Ejemplos de iconos de taxonomía de valores basados en estado](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41 _StateBasedTaxonomy")<br />Ejemplos de iconos de taxonomía de valores basados en estado

 Los iconos de **IntelliSense** no constan de más de tres de los siguientes elementos: una base, un modificador y un estado.

 ![Ejemplos de iconos de IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 -42 _IntelliSenseIcons")<br />Ejemplos de iconos de IntelliSense

 Los iconos de **proyecto pequeños (16x16)** no deben tener más de dos elementos: una base y un modificador.

 ![Ejemplos de iconos de proyecto pequeños (16x16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 -43 _16x16Project1") ![icono &#40;de proyecto&#41; de 16x16 2](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 -44 _16x16Project2") ![ &#40;icono&#41; de proyecto 16x16 3](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 -45 _16x16Project3")<br />Ejemplos de iconos de proyecto pequeños (16x16)

 Los iconos de **proyecto de gran tamaño (32x32)** no incluyen más de cuatro de los siguientes elementos: una base, uno a dos modificadores y una superposición de lenguaje.

 ![Ejemplos de iconos de proyecto grandes (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 -46 _32x32Project")<br />Ejemplos de iconos de proyecto grandes (32x32)

### <a name="production-details"></a>Detalles de producción
 Todos los nuevos elementos de la interfaz de usuario deben crearse mediante Windows Presentation Foundation (WPF) y todos los iconos nuevos de WPF deben tener el formato PNG de 32 bits. El PNG de 24 bits es un formato heredado que no admite la transparencia y, por lo tanto, no se recomienda para los iconos.

 Guarde la resolución a 96 ppp.

#### <a name="file-types"></a>Tipos de archivo

- **PNG de 32 bits:** el formato preferido para los iconos. Un formato de archivo de compresión de datos sin pérdida que puede almacenar una sola imagen de trama (píxel). los archivos PNG de 32 bits admiten transparencia de canal alfa, corrección gamma y entrelazado.

- **BMP de 32 bits:** para controles que no son de WPF. También se denomina XP o color de alta densidad. BMP de 32 bits es un formato de imagen RGB/A, una imagen de color verdadero con una transparencia de canal alfa. El canal alfa es una capa de transparencia designada en Adobe Photoshop que se guarda en el mapa de bits como un canal de color adicional (cuarto). Durante la producción de material gráfico se agrega un fondo negro a todos los archivos BMP de 32 bits para proporcionar una indicación visual rápida sobre la profundidad de color. Este fondo negro representa el área que se va a enmascarar en la interfaz de usuario.

- **32 bits ICO:** para iconos de proyecto y Agregar elemento. Todos los archivos ICO tienen un color verdadero de 32 bits con transparencia de canal alfa (RGB/A). Dado que los archivos ICO pueden almacenar varios tamaños y profundidades de color, los iconos de vista suelen tener un formato ICO que contiene los tamaños de imagen 16x16, 32x32, 48x48 y 256x256. Para que se muestren correctamente en el explorador de Windows, los archivos ICO se deben guardar en profundidad de color de 24 bits y 8 bits para cada tamaño de imagen.

- **XAML:** para las superficies de diseño y los adornos de Windows. Los iconos XAML son archivos de imagen basados en vectores que admiten el escalado, la rotación, el almacenamiento y la transparencia. En la actualidad, no son comunes en Visual Studio, pero se están volviendo más populares debido a su flexibilidad.

- **Import**

- **BMP de 24 bits:** para la barra de comandos de Visual Studio. Un formato de imagen RGB de color verdadero, BMP de 24 bits es una Convención de iconos que crea una capa de transparencia usando magenta (R = 255, G = 0, B = 255) como clave de color para una capa de transparencia de salida. En un BMP de 24 bits, todas las superficies magenta se muestran con el color de fondo.

- **GIF de 24 bits:** para la barra de comandos de Visual Studio. Formato de imagen RGB de color verdadero que admite la transparencia. Los archivos GIF se usan a menudo en ilustraciones del asistente y animaciones GIF.

### <a name="icon-construction"></a>Construcción de iconos
 El tamaño de icono más pequeño en Visual Studio es 16x16. El mayor valor de uso común es 32x32. Tenga en cuenta que no debe llenar todo el marco de 16x16, 24x24 o 32x32 al diseñar un icono. La construcción de iconos uniforme y legible es esencial para el reconocimiento de usuarios. Siga los siguientes puntos al generar iconos.

- Los iconos deben ser claros, comprensibles y coherentes.

- Es mejor usar los elementos de notificación de estado como iconos únicos y no apilarlos encima de un elemento de base de icono. En ciertos contextos, la interfaz de usuario podría requerir que el elemento de estado se emparejara con un elemento base.

- Los iconos de proyecto suelen ser archivos. ico que contienen varios tamaños. Solo se actualizan los iconos 16x16, 24x24 y 32x32. La mayoría de los iconos 16x16 y 24x24 contendrán los mismos elementos. Los iconos de 32x32 contienen más detalles, incluido el tipo de idioma del proyecto cuando proceda.

- En el caso de los iconos 32x32, los elementos base suelen tener un grosor de línea de 2 píxeles. Se puede usar un grosor de línea de 1 o 2 píxeles para los elementos de detalle. Utilice el mejor criterio para determinar cuál es más adecuado.

- Tener al menos un espaciado de 1 píxel entre los elementos de los iconos 16x16 y 24x24. En el caso de los iconos 32x32, use el espaciado de 2 píxeles entre los elementos y entre el modificador y el elemento base.

  ![Espaciado de elementos para iconos con tamaño 16x16, 24x24 y 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 -47 _ElementSpacing")<br />Espaciado de elementos para iconos con tamaño 16x16, 24x24 y 32x32

#### <a name="color-and-accessibility"></a>Color y accesibilidad
 Las directrices de cumplimiento de Visual Studio requieren que todos los iconos del producto pasen los requisitos de accesibilidad para el color y el contraste. Esto se consigue a través de la inversión de icono y, al diseñar, debe tener en cuenta que se invertirá mediante programación en el producto.

 Para obtener más información sobre el uso de colores en los iconos de Visual Studio, vea [usar el color en las imágenes](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="BKMK_UsingColorInImages"></a>Usar el color en las imágenes

### <a name="overview"></a>Información general
 Los iconos de Visual Studio son principalmente monocromáticos. El color se reserva para transmitir información específica y nunca para la decoración. Se usa el color:

- para indicar una acción

- para avisar al usuario de una notificación de estado

- para designar la afiliación de idioma

- para diferenciar elementos en IntelliSense

### <a name="accessibility"></a>Accesibilidad
 Las instrucciones de cumplimiento de Visual Studio requieren que todos los iconos protegidos en el producto superen los requisitos de accesibilidad para el color y el contraste. Los colores de la paleta del lenguaje visual se han probado y cumplen estos requisitos.

#### <a name="color-inversion-for-dark-themes"></a>Inversión de color para los temas oscuros
 Para que aparezcan iconos con la relación de contraste correcta en el tema oscuro de Visual Studio, se aplica una inversión mediante programación. Los colores de esta guía se han elegido en parte para que se inviertan correctamente. Restrinja el uso de color a esta paleta o obtendrá resultados imprevisibles cuando se aplique la inversión.

 ![Ejemplos de iconos a los que se han invertido sus colores](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01 _DarkThemeInversion")<br />Ejemplos de iconos a los que se han invertido sus colores

### <a name="base-palette"></a>Paleta base
 Todos los iconos estándar contienen tres colores base. Los iconos no contienen degradados ni sombras paralelas, con una o dos excepciones para los iconos de herramientas 3D.

|Uso|Name|Valor (tema claro)|Muestras|Ejemplo|
|-----------|----------|---------------------------|------------|-------------|
|Fondo/oscuro|VS BG|424242/66, 66, 66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Ejemplo de paleta base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 -02 _BasePaletteExample")|
|Primer plano/claro|FRENTE A FG|F0EFF1/240.239.241|![Muestrario F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Contorno|FRENTE a out|F6F6F6/246.246.246|![Muestrario F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Además de los colores base, cada icono puede contener un color adicional de la paleta extendida.

### <a name="extended-palette"></a>Paleta extendida

#### <a name="action-modifiers"></a>Modificadores de acción
 Los cuatro colores siguientes indican los tipos de acciones requeridas por los modificadores de acción:

|Uso|Name|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Positivo|Acción de VS verde|388A34/56138, 52|![Muestrario 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negativo|Acción de VS rojo|A1260D/161, 38, 13|![Muestrario A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutral|Acción de VS azul|00539C/0, 83156|![Muestrario 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crear o nuevo|Naranja de acción de VS|C27D1A/194156, 26|![Muestrario C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Ejemplos
 Green se usa para los modificadores de acción positivos como "Add", "Run", "Play" y "Validate".

|||||
|-|-|-|-|
|![Icono de ejecución](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Run|![Icono ejecutar consulta](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 -04 _ExecuteQuery")<br />Ejecutar consulta|![Icono reproducir todos los pasos](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 -05 _PlayAllSteps")<br />Reproducir todos los pasos|![Icono Agregar control](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 -06 _AddControl")<br />Agregar control|

 Rojo se usa para los modificadores de acción negativos como "eliminar", "detener", "Cancelar" y "cerrar".

|||||
|-|-|-|-|
|![Icono Eliminar relación](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 -07 _DeleteRelationship")<br />Eliminar relación|![Icono Eliminar columna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 -08 _DeleteColumn")<br />Eliminar columna|![Icono detener consulta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 -09 _StopQuery")<br />Detener consulta|![Icono conexión sin conexión](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 -10 _ConnectionOffline")<br />Conexión sin conexión|

 Blue se aplica a los modificadores de acción neutros que se suelen representar como flechas, como "Open", "Next", "PREVIOUS", "Import" y "Export".

|||||
|-|-|-|-|
|![Icono ir a campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 -11 _GoToField")<br />Ir a campo|![Icono de inserción&#45;en el repositorio por lotes](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 -12 _BatchedCheckIn")<br />Inserción en el repositorio por lotes|![Icono del editor de direcciones](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 -13 _AddressEditor")<br />Editor de direcciones|![Icono del editor de asociaciones](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 -14 _AssociationEditor")<br />Editor de asociaciones|

 El oro oscuro se usa principalmente para el modificador "nuevo".

|||||
|-|-|-|-|
|![Icono nuevo proyecto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 errores _NewProject")<br />nuevo proyecto|![Icono Crear nuevo gráfico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16 _CreateNewGraph")<br />Crear nuevo gráfico|![Icono nueva prueba unitaria](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 -17 _NewUnitTest")<br />Nueva prueba unitaria|![Icono nuevo elemento de lista](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 -18 _NewListItem")<br />Nuevo elemento de lista|

#### <a name="special-cases"></a>Casos especiales
 En casos especiales, un modificador de acción coloreado se puede usar de forma independiente como un icono independiente. El color usado para el icono refleja las acciones con las que está asociado el icono. Este uso está limitado a un pequeño subconjunto de iconos, entre los que se incluyen:

||||||
|-|-|-|-|-|
|![Icono de ejecución](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 -03 _ActionModifierRun")<br />Run|![Icono de detención](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 -19 _Stop")<br />Detener|![Eliminar icono](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 -20 _ eliminar")<br />Eliminar|![Icono guardar](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 -21 _Save")<br />Save|![Icono navegar hacia atrás](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 -22 _NavigateBack")<br />Navegar hacia atrás|

### <a name="code-hierarchy-palette"></a>Paleta de jerarquía de código

#### <a name="folder"></a>Carpeta

|Uso|Name|Valor (todos los temas)|Muestras|Ejemplo|
|-----------|----------|--------------------------|------------|-------------|
|Folder|Carpeta|DCB67A/220.182.122|![Muestrario DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icono de color de carpeta](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 -23 _FolderColor")|

#### <a name="visual-studio-languages"></a>Lenguajes de Visual Studio
 Cada uno de los lenguajes o plataformas comunes disponibles en Visual Studio tiene un color asociado. Estos colores se usan en el icono base o en los modificadores de idioma que aparecen en la esquina superior derecha de los iconos compuestos.

|Uso|Name|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF azul|0095D7/0149.215|![Muestrario 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Púrpura de CPP|9B4F96/155, 79150|![Muestrario 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|Verde CS (VS acción verde)|388A34/56138, 52|![Muestrario 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Rojo de CSS|BD1E2D/189, 30, 45|![Muestrario BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Púrpura de FS|672878/103, 40120|![Muestra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Naranja de JS|F16421/241100, 33|![Muestrario F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB azul (VS Action Blue)|00539C/0, 83156|![Muestrario 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Naranja de TS|E04C06/224, 76, 6|![Muestrario E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Plantillas de|PY verde|879636/135150, 54|![Muestra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Ejemplos de iconos con modificadores de lenguaje

|||||||
|-|-|-|-|-|-|
|![Icono de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 -25 _VB")<br />VB|![Icono&#35; de C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 -26 _CSharp")<br />C#|![Icono&#43; &#43; de C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 -27 _CPlusPlus")<br />C++|![Icono&#35; de F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 -28 _FSharp")<br />F#|![Icono de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 -29 _JavaScript")<br />JavaScript|![Icono de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 -30 _Python")<br />Plantillas de|
|![Icono HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 -31 _HTML")<br />HTML|![Icono de WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 -32 _WPF")<br />WPF|![Icono de ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 -33 _ASP")<br />ASP|![Icono de CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 -34 _CSS")<br />CSS|![Icono de TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 -35 _TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Los iconos de IntelliSense utilizan una paleta de colores exclusiva. Estos colores se usan para ayudar a los usuarios a distinguir rápidamente entre los distintos elementos de la lista emergente de IntelliSense.

|Uso|Name|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Clase, evento|Naranja de acción de VS|C27D1A/194125, 26|![Muestrario C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Método de extensión, método, módulo, delegado|Acción de VS púrpura|652D90/101, 45144|![Muestrario 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, elemento de enumeración, macro, estructura, tipo de valor de Unión, operador, interfaz|Acción de VS azul|00539C/0, 83156|![Muestrario 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|Acción de VS verde|388A34/56138, 52|![Muestrario 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, excepción, elemento de enumeración, asignación, elemento de asignación, espacio de nombres, plantilla, definición de tipo|Background (VS BG)|424242/66, 66, 66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Ejemplos de iconos de IntelliSense

||||||
|-|-|-|-|-|
|![Icono de clase de IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 -36 _IntelliSenseClass")<br />Clase|![Icono de evento privado de IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 -37 _IntelliSensePrivateEvent")<br />Evento privado|![Icono de delegado de IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 -38 _IntelliSenseDelegate")<br />delegado|![Icono Friend del método IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 -39 _IntelliSenseMethodFriend")<br />Friend (método)|![Icono de campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 -40 _Field")<br />Campo|
|![Icono de elemento de enumeración protegido de IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41 _IntelliSenseProtectedEnumItem")<br />Elemento de enumeración protegido|![Icono de objeto de IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 -42 _IntelliSenseObject")<br />Object|![Icono de plantilla de IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 -43 _IntelliSenseTemplate")<br />Plantilla|![Icono de acceso directo de excepción de IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 -44 _IntelliSenseExceptionShortcut")<br />Acceso directo de excepción||

### <a name="notifications"></a>Notificaciones
 Las notificaciones en Visual Studio se usan para indicar el estado. En la paleta de notificaciones se usan los cuatro colores siguientes, así como las opciones de relleno de primer plano en blanco o negro, para definir notificaciones con los niveles de estado siguientes.

|Uso|Name|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Estado: neutro|Azul de notificación (y azul)|1BA1E2/27.161.226|![Muestrario 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Estado: positivo|Notificación verde (frente a verde)|339933/51153, 51|![Muestra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Estado: negativo|Notificación roja (frente a rojo)|E51400/229, 20, 0|![Muestrario E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Estado: ADVERTENCIA|Notificación amarilla (VS naranja)|FFCC00/255204, 0|![Muestrario FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Relleno de primer plano|Notificación de negro (negro)|000000/0, 0, 0|![Muestra &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Relleno de primer plano|Notificación de blanco (blanco)|FFFFFF/255.255.255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Ejemplos de iconos de notificación

|||||
|-|-|-|-|
|![Icono de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 -45 _Alert")<br />Alerta|![Icono de advertencia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 -48 _Warning")<br />Advertencia|![Icono completar](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 -46 _Complete")<br />Completado|![Icono de detención](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 -47 _Stop")<br />Detener|

### <a name="visual-studio-online"></a>Visual Studio Online
 En general, Visual Studio online se compone de características hospedadas en un explorador. El color varía en entornos diferentes, pero el estilo sigue siendo el mismo.

|Agrupar|Uso|Name|Valor (todos los temas)|Muestras|
|-----------|-----------|----------|--------------------------|------------|
|TFS|Fondo|TFSO BG|656565/101, 101, 101|![Muestra 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|
|TFS|Contorno|TFSO|FFFFFF/255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Napa|Fondo|Blanco|FFFFFF/255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|Monaco|Fondo|Blanco|FFFFFF/255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Fondo|Blanco|FFFFFF/255, 255, 255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|
|F12|Normal|Grey_Primary F12|555555/85, 85, 85|![Muestra 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|
|F12|Al mantener el puntero|Blue_Hover F12|2279BF/34.121.191|![Muestrario 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|
|F12|Deshabilitado|LtGrey_Disabled F12|ABABAC/171.171.172|![Muestrario ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|
|F12|Fondo de mantener el mouse|Mantener el mouse|D9EBF7/217.235.247|![Muestrario D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|
|F12|Fondo presionado|BG presionado|B2D7F0/178.215.240|![Muestrario B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|
|F12|Contorno|FRENTE A OUT|F6F6F6/246.246.246|![Muestrario F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|
|F12|Información|Información|00BCF2/0188.242|![Muestrario 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|
|F12|Advertencia|Advertencia|F28300/242131, 0|![Muestrario F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|
|F12|Error/negativo|Error_Negative|E81123/232, 17, 35|![Muestrario E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|
|F12|Inicio/positivo|Start_Positive|009E49/0158, 73|![Muestrario 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|
|F12|Tipo de interrupción|Tipo de interrupción|9B4F96/155, 79150|![Muestrario 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|F12|Marca de evento|Marca de evento|A51F00/165, 31, 0|![Muestrario A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|
|F12|Marca de usuario|Marca de usuario|F16220/241, 98, 32|![Muestrario F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|

#### <a name="examples-of-visual-studio-online-icons"></a>Ejemplos de iconos de Visual Studio online

|TFS en línea||||
|----------------|-|-|-|
|![Icono de equipo en línea de TFS](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 -49 _TFSOnlineTeam")<br />Equipo en línea|![Icono de información de TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405-50 _TFSInformation")<br />Información|![Icono de historial de TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 -51 _TFSHistory")<br />Historial|![Icono de rama de TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 -52 _TFSBranch")<br />Bifurcar|

|Napa||||
|----------|-|-|-|
|![Icono de contenido de Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 -53 _NapaContent")<br />Contenido|![Icono de correo de Office de Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 -54 _NapaOfficeMail")<br />Correo de Office|![Icono de SharePoint de Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 -55 _NapaSharePoint")<br />SharePoint|![Icono del panel de tareas de Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 -56 _NapaTaskPane")<br />Panel de tareas|

|Monaco||||
|------------|-|-|-|
|![Icono de archivos de Mónaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 -57 _MonacoFiles")<br />Archivos|![Icono de Git de Mónaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 -58 _MonacoGit")<br />Git|![Icono de búsqueda de Mónaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 -59 _MonacoSearch")<br />Buscar|![Icono de texto de Mónaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 -60 _MonacoText")<br />Text|

|F12|||
|---------|-|-|
|![Icono de código Pretty F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 -61 _F12PrettyCode")<br />Código Pretty|![Icono de advertencia F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 -62 _F12Warning")<br />Advertencia|![Icono de emulación de F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 -63 _F12Emulate")<br />Emular|