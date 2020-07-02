---
title: Imágenes e iconos de Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7de4488a8304b21b578b2ad5ac2c29deafcf1b0a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537545"
---
# <a name="images-and-icons-for-visual-studio"></a>Imágenes e iconos para Visual Studio
## <a name="image-use-in-visual-studio"></a><a name="BKMK_ImageUseInVisualStudio"></a>Uso de imágenes en Visual Studio
 Antes de crear material gráfico, considere la posibilidad de utilizar las más de 1000 imágenes en la [biblioteca de imágenes de Visual Studio](https://www.microsoft.com/download/details.aspx?id=35825).

### <a name="types-of-images"></a>Tipos de imágenes

- **Iconos**. Imágenes pequeñas que aparecen en comandos, jerarquías, plantillas, etc. El tamaño de icono predeterminado que se usa en Visual Studio es un PNG de 16x16. Los iconos generados por el servicio de imágenes generan automáticamente el formato XAML para la compatibilidad con HDPI.

    > [!NOTE]
    > Mientras que las imágenes se usan en el sistema de menús, no debe crear un icono para cada comando. Consulte [menús y comandos de Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) para ver si el comando debe obtener un icono.

- **Miniaturas.** Imágenes usadas en el área de vista previa de un cuadro de diálogo, como el cuadro de diálogo nuevo proyecto.

- **Imágenes de cuadro de diálogo.** Imágenes que aparecen en los cuadros de diálogo o los asistentes, ya sea como gráficos descriptivos o indicadores de mensaje. Use con poca frecuencia y solo cuando sea necesario para ilustrar un concepto difícil u obtener la atención del usuario (alerta, ADVERTENCIA).

- **Imágenes animadas.** Se usa en indicadores de progreso, barras de estado y cuadros de diálogo de operaciones.

- **Cursores.** Se utiliza para indicar si se permite una operación con el mouse, dónde se puede quitar un objeto, etc.

## <a name="icon-design"></a><a name="BKMK_IconDesign"></a>Diseño de iconos

### <a name="overview"></a>Introducción
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

|**Uso correcto de imágenes simbólicas**|**Uso incorrecto de imágenes simbólicas**|
|-|-|
|![Icono de etiqueta inteligente correcta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404-01_SmartTagCorrect")|![Icono de etiqueta inteligente incorrecta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404-02_SmartTagIncorrect")|

 Hay instancias en las que los elementos de interfaz de usuario estándar y fácilmente reconocibles funcionan bien para los iconos. Agregar ventana es un ejemplo de este tipo:

|**Corregir el elemento de la interfaz de usuario en un icono**|**Elemento de interfaz de usuario incorrecto en un icono**|
|-|-|
|![Icono de agregar ventana correcto](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404-03_AddWindowCorrect")|![Icono de agregar ventana incorrecto](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404-04_AddWindowIncorrect")|

 No utilice un documento como elemento base a menos que sea esencial para el significado del icono. Sin el elemento de documento en agregar documento (abajo), se pierde el significado, mientras que al actualizar el elemento de documento no es necesario comunicar el significado.

|**Uso correcto del icono de documento**|**Uso incorrecto del icono de documento**|
|-|-|
|![Icono de documento correcto](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404-05_DocumentIconCorrect")|![Icono de documento incorrecto](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404-06_DocumentIconIncorrect")|

 El concepto de "Mostrar" debe estar representado por el icono que mejor ilustra lo que se muestra, como sucede en el ejemplo de Mostrar todos los archivos. Se puede usar una metáfora de lente para indicar el concepto de "vista" si es necesario, como en el ejemplo Vista de recursos.

|**Feria**|**Visores**|
|-|-|
|![Icono Mostrar](../../extensibility/ux-guidelines/media/0404-07_show.png "0404-07_Show")|![Icono Vista](../../extensibility/ux-guidelines/media/0404-08_view.png "0404-08_View")|

 El icono de lupa hacia la derecha debe representar solo buscar, buscar y examinar. La variante de la izquierda con el signo más o el signo menos solo debe representar o alejar.

|**Buscan**|**General**|
|-|-|
|![Icono de búsqueda](../../extensibility/ux-guidelines/media/0404-09_search.png "0404-09_Search")|![Icono Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404-10_Zoom")|

 En las vistas de árbol, no utilice el icono de carpeta y un modificador. Si está disponible, use solo el modificador.

|**Iconos de vista de árbol correctos**|**Iconos de vista de árbol incorrectos**|
|-|-|
|![Icono de vista de árbol correcto &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404-11_TreeViewCorrect1") ![icono de vista de árbol correcto &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404-12_TreeViewCorrect2")|![Icono de vista de árbol incorrecto &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404-13_TreeViewIncorrect1") ![icono de vista de árbol incorrecto &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404-14_TreeViewIncorrect2")|

### <a name="style-details"></a>Detalles de estilo

#### <a name="layout"></a>Layout
 Elementos de la pila como se muestra para los iconos estándar de 16x16:

 ![Pila de diseño para los iconos de 16 x 16](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404-15_LayoutStack")<br />Pila de diseño para los iconos de 16 x 16

 Los elementos de notificación de estado se usan mejor como iconos independientes. Sin embargo, hay contextos en los que una notificación se debe apilar en el elemento base, como con el icono de tarea completada:

 ![Notificaciones independientes en Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404-16_StandaloneNotificationIcons")<br />Iconos de notificación independientes

 ![Icono de tarea completa](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404-17_TaskComplete")<br />Icono de tarea completada

 Los iconos de proyecto suelen ser archivos. ico que contienen varios tamaños. La mayoría de los iconos de 16x16 contienen los mismos elementos. Las versiones de 32x32 tienen más detalles, incluido el tipo de proyecto cuando proceda.

 ![Iconos de proyecto en Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404-18_IconProjectThreeSizes")<br />Iconos de proyecto de biblioteca de controles de Windows de VB, 16x16 y 32x32

 Centrar un icono dentro de su marco de píxeles. Si eso no es posible, alinee el icono con la parte superior o derecha del marco.

 ![Icono centrado en el fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404-19_IconCentered")<br />Icono centrado en el fotograma de píxeles

 ![Icono alineado en la parte superior derecha del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404-20_IconTopRight")<br />Icono alineado en la parte superior derecha del marco

 ![Icono centrado y alineado en la parte superior del fotograma de píxeles](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404-21_IconTopAlign")<br />Icono centrado y alineado en la parte superior del marco

 Para lograr una alineación y un equilibrio ideales, evite obstruir el elemento base del icono con glifos de acción. Coloque el glifo cerca de la parte superior izquierda del elemento base. Al agregar un elemento adicional, tenga en cuenta la alineación y el equilibrio del icono.

|**Corregir la alineación y el equilibrio**|**Alineación y equilibrio incorrectos**|
|-|-|
|![Equilibrio y alineación correctos de los iconos](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404-22_AlignBalanceCorrect")|![Equilibrio y alineación incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404-23_AlignBalanceIncorrect")|

 Asegúrese de que la paridad de tamaño para los iconos que comparten elementos y se usan en conjuntos. Tenga en cuenta que, en el emparejamiento incorrecto, el círculo y la flecha tienen un tamaño y no coinciden.

|**Paridad de tamaño correcta**|**Paridad de tamaño incorrecta**|
|-|-|
|![Tamaño y paridad correctos de los iconos](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404-24_SizeParityCorrect")|![Tamaño y paridad incorrectos de los iconos](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404-25_SizeParityIncorrect")|

 Use los pesos de línea y visual coherentes. Evalúe el modo en que el icono que va a compilar se compara con otros iconos usando una comparación en paralelo. Nunca use el marco 16x16 completo, use 15x15 o inferior. La relación de negativo a positivo (oscuro a claro) debe ser 50/50.

|**Relación de negativo a positivo correcta**|**Relación de negativo a positivo incorrecta**|
|-|-|
|![Peso visual correcto para los iconos &#40;1&#41;](../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404-26_VisualWeightCorrect1")<br /><br /> ![Peso visual correcto para los iconos &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404-27_VisualWeightCorrect2")<br /><br /> ![Peso visual correcto para los iconos &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404-28_VisualWeightCorrect3")|![Grosor visual incorrecto para iconos](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404-29_VisualWeightIncorrect")|

 Use formas simples, comparables y ángulos complementarios para crear sus elementos sin sacrificar la integridad de los elementos. Use los ángulos 45 ° o 90 ° siempre que sea posible.

 ![Ángulos de icono correctos](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404-30_IconAnglesCorrect")

#### <a name="perspective"></a>Perspectiva
 Mantenga el icono claro y comprensible. Use la perspectiva y una fuente de luz solo cuando sea necesario. Aunque debe evitarse el uso de la perspectiva en los elementos de icono, algunos elementos son irreconocibles sin él. En tales casos, una perspectiva estilizada comunica la claridad del elemento.

 ![Perspectiva de 3 puntos](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404-31_3PointPerspective")<br />Perspectiva de 3 puntos

 ![Perspectiva de 1 punto](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404-32_1PointPerspective")<br />Perspectiva de 1 punto

 La mayoría de los elementos deben estar orientados o inclinados hacia la derecha:

 ![Iconos en ángulo derecho](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404-33_AngledRight")

 Use fuentes ligeras solo cuando agregue la claridad necesaria a un objeto.

|**Fuente de luz correcta**|**Fuente de luz incorrecta**|
|-|-|
|![Fuentes de luz correctas para iconos](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404-34_LightSourcesCorrect")|![Fuentes de luz incorrectas para iconos](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404-35_LightSourcesIncorrect")|

 Use los esquemas solo para mejorar la legibilidad o para comunicar mejor la metáfora. El saldo positivo negativo (oscuro claro) debe ser 50/50.

|**Uso correcto de los esquemas**|**Uso incorrecto de los esquemas**|
|-|-|
|![Contornos correctos](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404-36_OutlinesCorrect")|![Contornos incorrectos](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404-37_OutlinesIncorrect")|

#### <a name="icon-types"></a>Tipos de icono
 Los iconos de **Shell y de barra de comandos** no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de Shell y de barra de comandos](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404-38_ShellIcons")<br />Ejemplos de iconos de Shell y de barra de comandos

 Los iconos de la barra de comandos de la **ventana de herramientas** no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de la barra de comandos de la ventana de herramientas](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404-39_ToolWindowCommandBarIcons")<br />Ejemplos de iconos de la barra de comandos de la ventana de herramientas

 Los iconos de **desambiguamiento** de la vista de árbol no incluyen más de tres de los siguientes elementos: una base, un modificador, una acción o un estado.

 ![Ejemplos de iconos de desambiguación de vista de árbol](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404-40_TreeViewIcons")<br />Ejemplos de iconos de desambiguación de vista de árbol

 Los iconos de **taxonomía de valores basados en estado** existen en los siguientes Estados: activo, activo deshabilitado e inactivo deshabilitado.

 ![Ejemplos de iconos de taxonomía de valores basados en estado](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404-41_StateBasedTaxonomy")<br />Ejemplos de iconos de taxonomía de valores basados en estado

 Los iconos de **IntelliSense** no constan de más de tres de los siguientes elementos: una base, un modificador y un estado.

 ![Ejemplos de iconos de IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404-42_IntelliSenseIcons")<br />Ejemplos de iconos de IntelliSense

 Los iconos de **proyecto pequeños (16x16)** no deben tener más de dos elementos: una base y un modificador.

 ![Ejemplos de iconos de proyecto pequeños (16x16) icono de](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404-43_16x16Project1") ![proyecto 16x16 &#40;2&#41;](../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404-44_16x16Project2") ![icono de proyecto 16x16 &#40;3&#41;](../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404-45_16x16Project3")<br />Ejemplos de iconos de proyecto pequeños (16x16)

 Los iconos de **proyecto de gran tamaño (32x32)** no incluyen más de cuatro de los siguientes elementos: una base, uno a dos modificadores y una superposición de lenguaje.

 ![Ejemplos de iconos de proyecto grandes (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404-46_32x32Project")<br />Ejemplos de iconos de proyecto grandes (32x32)

### <a name="production-details"></a>Detalles de producción
 Todos los nuevos elementos de la interfaz de usuario deben crearse mediante Windows Presentation Foundation (WPF) y todos los iconos nuevos de WPF deben tener el formato PNG de 32 bits. El PNG de 24 bits es un formato heredado que no admite la transparencia y, por lo tanto, no se recomienda para los iconos.

 Guarde la resolución a 96 ppp.

#### <a name="file-types"></a>Tipos de archivo

- **PNG de 32 bits:** el formato preferido para los iconos. Un formato de archivo de compresión de datos sin pérdida que puede almacenar una sola imagen de trama (píxel). los archivos PNG de 32 bits admiten transparencia de canal alfa, corrección gamma y entrelazado.

- **BMP de 32 bits:** para controles que no son de WPF. También se denomina XP o color de alta densidad. BMP de 32 bits es un formato de imagen RGB/A, una imagen de color verdadero con una transparencia de canal alfa. El canal alfa es una capa de transparencia designada en Adobe Photoshop que se guarda en el mapa de bits como un canal de color adicional (cuarto). Durante la producción de material gráfico se agrega un fondo negro a todos los archivos BMP de 32 bits para proporcionar una indicación visual rápida sobre la profundidad de color. Este fondo negro representa el área que se va a enmascarar en la interfaz de usuario.

- **32 bits ICO:** para iconos de proyecto y Agregar elemento. Todos los archivos ICO tienen un color verdadero de 32 bits con transparencia de canal alfa (RGB/A). Dado que los archivos ICO pueden almacenar varios tamaños y profundidades de color, los iconos de vista suelen tener un formato ICO que contiene los tamaños de imagen 16x16, 32x32, 48x48 y 256x256. Para que se muestren correctamente en el explorador de Windows, los archivos ICO se deben guardar en profundidad de color de 24 bits y 8 bits para cada tamaño de imagen.

- **XAML:** para las superficies de diseño y los adornos de Windows. Los iconos XAML son archivos de imagen basados en vectores que admiten el escalado, la rotación, el almacenamiento y la transparencia. En la actualidad, no son comunes en Visual Studio, pero se están volviendo más populares debido a su flexibilidad.

- **SVG**

- **BMP de 24 bits:** para la barra de comandos de Visual Studio. Un formato de imagen RGB de color verdadero, BMP de 24 bits es una Convención de iconos que crea una capa de transparencia usando magenta (R = 255, G = 0, B = 255) como clave de color para una capa de transparencia de salida. En un BMP de 24 bits, todas las superficies magenta se muestran con el color de fondo.

- **GIF de 24 bits:** para la barra de comandos de Visual Studio. Formato de imagen RGB de color verdadero que admite la transparencia. Los archivos GIF se usan a menudo en ilustraciones del asistente y animaciones GIF.

### <a name="icon-construction"></a>Construcción de iconos
 El tamaño de icono más pequeño en Visual Studio es 16x16. El mayor valor de uso común es 32x32. Tenga en cuenta que no debe llenar todo el marco de 16x16, 24x24 o 32x32 al diseñar un icono. La construcción de iconos uniforme y legible es esencial para el reconocimiento de usuarios. Siga los siguientes puntos al generar iconos.

- Los iconos deben ser claros, comprensibles y coherentes.

- Es mejor usar los elementos de notificación de estado como iconos únicos y no apilarlos encima de un elemento de base de icono. En ciertos contextos, la interfaz de usuario podría requerir que el elemento de estado se emparejara con un elemento base.

- Los iconos de proyecto suelen ser archivos. ico que contienen varios tamaños. Solo se actualizan los iconos 16x16, 24x24 y 32x32. La mayoría de los iconos 16x16 y 24x24 contendrán los mismos elementos. Los iconos de 32x32 contienen más detalles, incluido el tipo de idioma del proyecto cuando proceda.

- En el caso de los iconos 32x32, los elementos base suelen tener un grosor de línea de 2 píxeles. Se puede usar un grosor de línea de 1 o 2 píxeles para los elementos de detalle. Utilice el mejor criterio para determinar cuál es más adecuado.

- Tener al menos un espaciado de 1 píxel entre los elementos de los iconos 16x16 y 24x24. En el caso de los iconos 32x32, use el espaciado de 2 píxeles entre los elementos y entre el modificador y el elemento base.

  ![Espaciado de elementos para iconos con tamaño 16x16, 24x24 y 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404-47_ElementSpacing")<br />Espaciado de elementos para iconos con tamaño 16x16, 24x24 y 32x32

#### <a name="color-and-accessibility"></a>Color y accesibilidad
 Las directrices de cumplimiento de Visual Studio requieren que todos los iconos del producto pasen los requisitos de accesibilidad para el color y el contraste. Esto se consigue a través de la inversión de icono y, al diseñar, debe tener en cuenta que se invertirá mediante programación en el producto.

 Para obtener más información sobre el uso de colores en los iconos de Visual Studio, vea [usar el color en las imágenes](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).

## <a name="using-color-in-images"></a><a name="BKMK_UsingColorInImages"></a>Usar el color en las imágenes

### <a name="overview"></a>Introducción
 Los iconos de Visual Studio son principalmente monocromáticos. El color se reserva para transmitir información específica y nunca para la decoración. Se usa el color:

- para indicar una acción

- para avisar al usuario de una notificación de estado

- para designar la afiliación de idioma

- para diferenciar elementos en IntelliSense

### <a name="accessibility"></a>Accesibilidad
 Las instrucciones de cumplimiento de Visual Studio requieren que todos los iconos protegidos en el producto superen los requisitos de accesibilidad para el color y el contraste. Los colores de la paleta del lenguaje visual se han probado y cumplen estos requisitos.

#### <a name="color-inversion-for-dark-themes"></a>Inversión de color para los temas oscuros
 Para que aparezcan iconos con la relación de contraste correcta en el tema oscuro de Visual Studio, se aplica una inversión mediante programación. Los colores de esta guía se han elegido en parte para que se inviertan correctamente. Restrinja el uso de color a esta paleta o obtendrá resultados imprevisibles cuando se aplique la inversión.

 ![Ejemplos de iconos a los que se han invertido sus colores](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405-01_DarkThemeInversion")<br />Ejemplos de iconos a los que se han invertido sus colores

### <a name="base-palette"></a>Paleta base
 Todos los iconos estándar contienen tres colores base. Los iconos no contienen degradados ni sombras paralelas, con una o dos excepciones para los iconos de herramientas 3D.

|Uso|NOMBRE|Valor (tema claro)|Muestras|Ejemplo|
|-----------|----------|---------------------------|------------|-------------|
|Fondo/oscuro|VS BG|424242/66, 66, 66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Ejemplo de paleta básica](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405-02_BasePaletteExample")|
|Primer plano/claro|FRENTE A FG|F0EFF1/240.239.241|![Muestra F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||
|Esquema|FRENTE a out|F6F6F6/246.246.246|![Muestra F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||

 Además de los colores base, cada icono puede contener un color adicional de la paleta extendida.

### <a name="extended-palette"></a>Paleta extendida

#### <a name="action-modifiers"></a>Modificadores de acción
 Los cuatro colores siguientes indican los tipos de acciones requeridas por los modificadores de acción:

|Uso|NOMBRE|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Positive|Acción de VS verde|388A34/56138, 52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Negative|Acción de VS rojo|A1260D/161, 38, 13|![Muestra A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|
|Neutra|Acción de VS azul|00539C/0, 83156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Crear o nuevo|Naranja de acción de VS|C27D1A/194156, 26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|

##### <a name="examples"></a>Ejemplos
 Green se usa para los modificadores de acción positivos como "Add", "Run", "Play" y "Validate".

|Ejecute|Ejecutar consulta|Reproducir todos los pasos|Agregar control|
|-|-|-|-|
|![Icono Ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icono Ejecutar consulta](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405-04_ExecuteQuery")|![Icono Reproducir todos los pasos](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405-05_PlayAllSteps")|![Icono Agregar control](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405-06_AddControl")|

 Rojo se usa para los modificadores de acción negativos como "eliminar", "detener", "Cancelar" y "cerrar".

|Eliminar relación|Eliminar columna|Detener consulta|Conexión sin conexión|
|-|-|-|-|
|![Icono Eliminar relación](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405-07_DeleteRelationship")|![Icono Eliminar columna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405-08_DeleteColumn")|![Icono Detener consulta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405-09_StopQuery")|![Icono Sin conexión](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405-10_ConnectionOffline")|

 Blue se aplica a los modificadores de acción neutros que se suelen representar como flechas, como "Open", "Next", "PREVIOUS", "Import" y "Export".

|Ir a campo|Inserción en el repositorio por lotes|Editor de direcciones|Editor de asociaciones|
|-|-|-|-|
|![Icono Ir al campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405-11_GoToField")|![Icono de&#45;de comprobación por lotes en el icono](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405-12_BatchedCheckIn")|![Icono de editor de direcciones](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405-13_AddressEditor")|![Icono de editor de asociación](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405-14_AssociationEditor")|

 El oro oscuro se usa principalmente para el modificador "nuevo".

|nuevo proyecto|Crear nuevo gráfico|Nueva prueba unitaria|Nuevo elemento de lista|
|-|-|-|-|
|![Icono de proyecto nuevo](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405-15_NewProject")|![Icono Crear nuevo gráfico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405-16_CreateNewGraph")|![Icono Nueva prueba unitaria](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405-17_NewUnitTest")|![Icono Nuevo elemento de lista](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405-18_NewListItem")|

#### <a name="special-cases"></a>Casos especiales
 En casos especiales, un modificador de acción coloreado se puede usar de forma independiente como un icono independiente. El color usado para el icono refleja las acciones con las que está asociado el icono. Este uso está limitado a un pequeño subconjunto de iconos, entre los que se incluyen:

|Ejecute|Stop|Eliminar|Guardar|Navegar hacia atrás|
|-|-|-|-|-|
|![Icono Ejecutar](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405-03_ActionModifierRun")|![Icono de detención](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405-19_Stop")|![Eliminar icono](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405-20_Delete")|![Icono Save (Guardar)](../../extensibility/ux-guidelines/media/0405-21_save.png "0405-21_Save")|![Icono Navegar hacia atrás](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405-22_NavigateBack")|

### <a name="code-hierarchy-palette"></a>Paleta de jerarquía de código

#### <a name="folder"></a>Carpeta

|Uso|NOMBRE|Valor (todos los temas)|Muestras|Ejemplo|
|-----------|----------|--------------------------|------------|-------------|
|Carpetas|Carpeta|DCB67A/220.182.122|![Muestra DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icono Carpeta de color](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405-23_FolderColor")|

#### <a name="visual-studio-languages"></a>Lenguajes de Visual Studio
 Cada uno de los lenguajes o plataformas comunes disponibles en Visual Studio tiene un color asociado. Estos colores se usan en el icono base o en los modificadores de idioma que aparecen en la esquina superior derecha de los iconos compuestos.

|Uso|NOMBRE|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|ASP, HTML, WPF|ASP HTML WPF azul|0095D7/0149.215|![Muestra 0095D7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|
|C++|Púrpura de CPP|9B4F96/155, 79150|![Muestra 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|
|C#|Verde CS (VS acción verde)|388A34/56138, 52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|CSS|Rojo de CSS|BD1E2D/189, 30, 45|![Muestra BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|
|F#|Púrpura de FS|672878/103, 40120|![Muestra 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|
|JavaScript|Naranja de JS|F16421/241100, 33|![Muestra F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|
|VB|VB azul (VS Action Blue)|00539C/0, 83156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|TypeScript|Naranja de TS|E04C06/224, 76, 6|![Muestra E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|
|Python|PY verde|879636/135150, 54|![Muestra 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|

##### <a name="examples-of-icons-with-language-modifiers"></a>Ejemplos de iconos con modificadores de lenguaje

|VB|C#|F#|JavaScript|Python|
|-|-|-|-|-|-|
|![Icono de Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405-25_VB")|![Icono de&#35; de C](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405-26_CSharp")|![Icono de&#43;&#43; de C](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405-27_CPlusPlus")|![Icono de&#35; F](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405-28_FSharp")|![Icono de JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405-29_JavaScript")|![Icono de Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405-30_Python")|

|HTML|WPF|ASP|CSS|TypeScript|
|-|-|-|-|-|-|
|![Icono de HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405-31_HTML")<br />HTML|![Icono de WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405-32_WPF")<br />WPF|![Icono de ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405-33_ASP")<br />ASP|![Icono de CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405-34_CSS")<br />CSS|![Icono de TypeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405-35_TypeScript")<br />TypeScript||

#### <a name="intellisense"></a>IntelliSense
 Los iconos de IntelliSense utilizan una paleta de colores exclusiva. Estos colores se usan para ayudar a los usuarios a distinguir rápidamente entre los distintos elementos de la lista emergente de IntelliSense.

|Uso|NOMBRE|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Clase, evento|Naranja de acción de VS|C27D1A/194125, 26|![Muestra C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|
|Método de extensión, método, módulo, delegado|Acción de VS púrpura|652D90/101, 45144|![Muestra 652D90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|
|Campo, elemento de enumeración, macro, estructura, tipo de valor de Unión, operador, interfaz|Acción de VS azul|00539C/0, 83156|![Muestra 00539C](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|
|Object|Acción de VS verde|388A34/56138, 52|![Muestra 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|
|Constante, excepción, elemento de enumeración, asignación, elemento de asignación, espacio de nombres, plantilla, definición de tipo|Background (VS BG)|424242/66, 66, 66|![Muestra 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|

##### <a name="examples-of-intellisense-icons"></a>Ejemplos de iconos de IntelliSense

|Clase|Evento privado|delegado|Friend (método)|Campo|
|-|-|-|-|-|
|![Icono de clase de IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405-36_IntelliSenseClass")|![Icono de evento privado de IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405-37_IntelliSensePrivateEvent")|![Icono de delegado de IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405-38_IntelliSenseDelegate")|![Icono de amigo de método de IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405-39_IntelliSenseMethodFriend")|![Icono de campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405-40_Field")|

|Elemento de enumeración protegido|Object|Plantilla|Acceso directo de excepción|
|-|-|-|-|
|![Icono de elemento de enumeración protegida de IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405-41_IntelliSenseProtectedEnumItem")|![Icono de objeto de IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405-42_IntelliSenseObject")|![Icono de plantilla de IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405-43_IntelliSenseTemplate")|![Icono de acceso directo a excepción de IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405-44_IntelliSenseExceptionShortcut")|

### <a name="notifications"></a>Notificaciones
 Las notificaciones en Visual Studio se usan para indicar el estado. En la paleta de notificaciones se usan los cuatro colores siguientes, así como las opciones de relleno de primer plano en blanco o negro, para definir notificaciones con los niveles de estado siguientes.

|Uso|NOMBRE|Valor (todos los temas)|Muestras|
|-----------|----------|--------------------------|------------|
|Estado: neutro|Azul de notificación (y azul)|1BA1E2/27.161.226|![Muestra 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|
|Estado: positivo|Notificación verde (frente a verde)|339933/51153, 51|![Muestra 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|
|Estado: negativo|Notificación roja (frente a rojo)|E51400/229, 20, 0|![Muestra E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|
|Estado: ADVERTENCIA|Notificación amarilla (VS naranja)|FFCC00/255204, 0|![Muestra FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|
|Relleno de primer plano|Notificación de negro (negro)|000000/0, 0, 0|![Muestra &#35;000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|
|Relleno de primer plano|Notificación de blanco (blanco)|FFFFFF/255.255.255|![Muestra FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|

#### <a name="examples-of-notification-icons"></a>Ejemplos de iconos de notificación

|Alerta|Advertencia|Completo|Stop|
|-|-|-|-|
|![Icono de alerta](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405-45_Alert")|![Icono de advertencia](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405-48_Warning")|![Icono de Completado](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405-46_Complete")|![Icono de detención](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405-47_Stop")|