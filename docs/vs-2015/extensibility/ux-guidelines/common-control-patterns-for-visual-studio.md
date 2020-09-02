---
title: Patrones de control comunes
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547451"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de control comunes para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Controles comunes

### <a name="overview"></a>Información general
 Los controles comunes componen la mayor parte de la interfaz de usuario en Visual Studio. Los controles más comunes que se usan en la interfaz de Visual Studio deben seguir las [directrices de interacción del escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este documento es específico de Visual Studio y cubre situaciones especiales o detalles que aumentan esas directrices de Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comunes en este tema

- [Barras](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Casillas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Agrupar marcos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Estilo visual
 Lo primero que hay que tener en cuenta al aplicar estilos a los controles es si los controles se van a utilizar en la interfaz de usuario con nombre. Los controles de la interfaz de usuario estándar son una interfaz de usuario no relacionada y deben seguir el [estilo normal del escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), lo que significa que no se vuelven a crear plantillas y deben aparecer en su apariencia de control predeterminada.

- **Cuadros de diálogo estándar (utilidad):** no se trata de ellos. No volver a crear plantillas. Usar valores predeterminados de estilo de control básico.

- **Ventanas de herramientas, editores de documentos, superficies de diseño y cuadros de diálogo:** Use la apariencia especializada con el servicio de color.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a> Barras
 Las barras de desplazamiento deben seguir [patrones de interacción comunes para las barras de desplazamiento de Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , a menos que se aumenten con información de contenido, como en el editor de código.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Campos de entrada
 Para un comportamiento de interacción típico, siga las [instrucciones del escritorio de Windows para los cuadros de texto](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo visual

- Los campos de entrada no deben tener estilo en los cuadros de diálogo de la utilidad. Use el estilo básico intrínseco para el control.

- Los campos de entrada con datos solo se deben usar en cuadros de diálogo y ventanas de herramientas.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Los campos de solo lectura tendrán un fondo gris (deshabilitado) pero el primer plano predeterminado (activo).

- Los campos obligatorios deben tener **\<Required>** como marcas de agua dentro de ellos. No debe cambiar el color del fondo excepto en raras ocasiones.

- Validación de errores: ver [notificaciones y progreso de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Los campos de entrada deben cambiar de tamaño para ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para que coincidan arbitrariamente con la longitud de un campo largo, como una ruta de acceso. La longitud puede ser una indicación al usuario de las limitaciones en cuanto al número de caracteres permitidos en el campo.

     ![Ancho](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **de campo de entrada incorrecto de ancho de control de campo de entrada: es improbable que el nombre sea largo.**

     ![Corregir](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") la **longitud correcta del campo de entrada del ancho del control de campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Cuadros combinados y listas desplegables
 Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para las listas](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)desplegables y los cuadros combinados.

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de la utilidad, no vuelva a crear la plantilla del control. Use el estilo básico intrínseco para el control.

- En la interfaz de usuario con la misma, los cuadros combinados y las listas desplegables siguen las áreas estándar de los controles.

#### <a name="layout"></a>Layout
 Los cuadros combinados y las listas desplegables deben ajustarse al contenido, no ajustarse al ancho de la ventana en la que se muestran ni coincidir arbitrariamente con la longitud de un campo largo, como una ruta de acceso.

 ![Diseño de Drop&#45;descendente incorrecto](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Longitud de campo incorrecta para un control desplegable**

 ![Corregir el diseño de la lista desplegable&#45;](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Longitud de campo correcta para un control desplegable**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Casillas
 Para un comportamiento de interacción típico, siga las [instrucciones del escritorio de Windows para las casillas](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de la utilidad, no vuelva a crear la plantilla del control. Use el estilo básico intrínseco para el control.

- En interfaz de usuario con la misma, las casillas siguen las áreas estándar de los controles.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- La interacción con una casilla nunca debe mostrar un cuadro de diálogo o desplazarse a otra área.

- Alinea las casillas con la línea de base de la primera línea de texto.

     Alineación incorrecta de la casilla ![alineación](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **incorrecta de la casilla: la casilla está centrada en el texto.**

     ![Corregir la alineación](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") de la casilla de verificación corrección de casilla **correcta: la casilla está alineada con la línea de base de la primera línea de texto.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Botones de radio
 Para un comportamiento de interacción típico, siga las [directrices del escritorio de Windows para los botones de radio](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo visual
 En los cuadros de diálogo de la utilidad, no aplicar estilo a los botones de radio. Use el estilo básico intrínseco para el control.

#### <a name="specialized-interactions"></a>Interacciones especializadas
 No es necesario usar un marco de grupo para incluir las opciones de radio.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Agrupar marcos
 Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para los marcos de grupo](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo visual
 En los cuadros de diálogo de la utilidad, no se estilo tramas de grupo. Use el estilo básico intrínseco para el control.

#### <a name="layout"></a>Layout

- No es necesario usar un marco de grupo para incluir las opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño estrecho.

- Nunca use un marco de grupo para un único control.

- A veces es aceptable usar una regla horizontal en lugar de un contenedor de tramas de grupo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Controles de texto

### <a name="labels"></a>Etiquetas

#### <a name="active-label-state"></a>Estado de etiqueta activa

##### <a name="utility-standard-dialogs"></a>Cuadros de diálogo de la utilidad (estándar))

- En general, siga las instrucciones del escritorio de Windows para las etiquetas de control.

- En los cuadros de diálogo de la utilidad, las etiquetas deben aparecer no en negrita, en la fuente del entorno estándar y en el color del texto. Vea [fuentes y formato para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Los puntos suspensivos siempre deben seguir las etiquetas.

##### <a name="signature-themed-dialogs"></a>Cuadros de diálogo de firma (con el mismo))
 Los controles de etiqueta pueden aparecer en negrita o en gris claro.

#### <a name="disabled-label-state"></a>Estado de etiqueta deshabilitado
 Las etiquetas deben reflejar la apariencia del control al que están asociadas. Por ejemplo, si el control asociado está deshabilitado, la etiqueta debe aparecer atenuada y deshabilitada. Normalmente, el sistema operativo lo controla y no requiere ningún tratamiento especial.

#### <a name="dynamic-labels"></a>Etiquetas dinámicas
 Las etiquetas dinámicas cambian en función de la selección actual. Siempre que sea posible, use etiquetas dinámicas en los diseños maestro y detalles para ayudar al usuario a comprender que la información mostrada es relevante para una selección específica y no información general.

 ![Etiqueta dinámica utilizada con contenido dinámico](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Ejemplo de una etiqueta dinámica utilizada con contenido dinámico**

#### <a name="instructional-text"></a>Texto informativo
 Algunos elementos de interfaz se benefician del texto informativo para ayudar al usuario a entender el propósito de la interfaz de usuario o para indicar qué acción debe realizar.

- El texto informativo es más común en la parte superior de los cuadros de diálogo, pero puede aparecer en otras áreas para dar instrucciones a una agrupación de controles complejos.

- El texto informativo no es interactivo, pero puede contener hipervínculos a temas de ayuda.

- Use el texto informativo con moderación y solo cuando sea necesario.

##### <a name="formatting"></a>Formato
 El texto informativo debe ser una fuente de entorno, el texto de control estándar (no es). Vea [fuentes y formato para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Para obtener más información sobre cómo escribir texto informativo, vea [texto y terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)de la interfaz de usuario.

 ![Formato de texto informativo](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Texto de instrucciones en un cuadro de diálogo de Visual Studio**

#### <a name="informational-text"></a>Texto informativo
 El texto informativo es texto que proporciona información adicional al usuario. Puede ser estático o dinámico, o usarse como una notificación. Siempre es de solo lectura, pero si es útil para el usuario tener la capacidad de copiar la información, el texto dinámico debe colocarse en un contenedor de controles como, por ejemplo, un campo de texto de solo lectura.

##### <a name="dynamic-context-specific-text"></a>Texto dinámico (específico del contexto)
 El texto de información dinámica cambia según el contexto, como cuando el usuario cambia el foco. A menudo, pero no siempre, el contenido dinámico se empareja con una etiqueta dinámica.

 ![Texto de información dinámica](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Cambios de texto informativo dinámicos en función del contexto.**

##### <a name="formatting"></a>Formato
 Hay dos maneras de mostrar campos de texto de solo lectura: directamente en la superficie de la interfaz de usuario (vea más arriba) o dentro de otro control, como un marco de grupo o un cuadro de texto. Puede ser correcto en función de la situación. Depende del diseñador de características determinar cómo presentar la información de solo lectura.

 El texto puede estar dentro de un cuadro de texto de solo lectura. Esto suele indicar que el contenido se puede seleccionar y copiar, aunque no se puede editar.

 ![Formato de texto informativo para los campos de solo&#45;lectura](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Formato de texto informativo para los campos de solo lectura**

#### <a name="watermarks"></a>Marcas de agua
 Aunque el texto puede ser el mismo, la diferencia entre las marcas de agua y el texto informativo es que las marcas de agua se reemplazan por el contenido cuando el control o la ventana no están vacíos y el texto de instrucciones permanece visible en todo momento.

 Las marcas de agua deben usarse cuando una ventana o un control están vacíos. Indican lo que hay que hacer para rellenar el área y pueden incluir vínculos de acción para abrir ventanas relevantes, como un origen de arrastre.

##### <a name="visual-style"></a>Estilo visual

- Las marcas de agua deben centrarse horizontalmente dentro de la ventana.

- Las marcas de agua deben estar alineadas en el centro, no alineadas a la izquierda.

- Las marcas de agua se pueden centrar o colocar verticalmente cerca de la parte superior del área. Si se encuentra cerca de la parte superior del área, debe haber suficiente espacio para que la marca de agua destaque.

- Use el `Environment.GrayText` token de color y la fuente del entorno estándar. Los hipervínculos deben usar los tokens compartidos de hipervínculo estándar: `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , `Environment.PanelHyperlinkPressed` y `Environment.PanelHyperlinkDisabled` .

- No se pueden seleccionar marcas de agua en el fondo

- Si es posible, incluya vínculos en la marca de agua para ayudar al usuario a empezar.

  ![Texto de marca de agua en una ventana del diseñador](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Texto de marca de agua en una ventana de herramientas](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Ejemplos de texto de marca de agua en Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos

### <a name="overview"></a>Información general
 Los botones y controles de vínculo (hipervínculos) deben seguir las [instrucciones básicas del escritorio de Windows en los hipervínculos](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) para el uso, el texto, el tamaño y el espaciado.

### <a name="choosing-between-buttons-and-links"></a>Elegir entre botones y vínculos
 Tradicionalmente, se han usado botones para acciones e hipervínculos se han reservado para la navegación. Los botones se pueden usar en todos los casos, pero el rol de los vínculos se ha expandido en Visual Studio para que los botones y los vínculos sean más intercambiables en algunas condiciones.

 Cuándo usar los botones de comando:

- Comandos principales

- Mostrar las ventanas que se usan para recopilar datos o elegir opciones, incluso si son comandos secundarios

- Acciones destructivas o irreversibles

- Botones de compromiso dentro de los asistentes y flujos de páginas

  Evite botones de comando en ventanas de herramientas o si necesita más de dos palabras para la etiqueta. Los vínculos pueden tener etiquetas más largas.

  Cuándo usar vínculos:

- Navegación a otra ventana, documento o página web

- Situaciones que requieren una etiqueta más larga o una frase corta para describir la intención de la acción

- Espacios estrechos en los que un botón desborda la interfaz de usuario, siempre que la acción no sea destructiva ni irreversible

- Quitar el resaltado de comandos secundarios en situaciones en las que hay muchos comandos

#### <a name="examples"></a>Ejemplos
 ![Vínculos de comandos de barra de información después de un mensaje de estado](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Vínculos de comandos usados en la barra de estado después de un mensaje de estado**

 ![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Vínculos que se usan en el menú emergente de CodeLens**

 ![Vínculos que se usan como comandos secundarios](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Vínculos usados para comandos secundarios en los que los botones atraerían demasiada atención**

### <a name="common-buttons"></a>Botones comunes

#### <a name="text"></a>Texto
 Siga las instrucciones de escritura de la [terminología y el texto](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)de la interfaz de usuario.

#### <a name="visual-style"></a>Estilo visual

##### <a name="standard-dialogs"></a>Cuadros de diálogo estándar
 La mayoría de los botones de Visual Studio aparecerán en los cuadros de diálogo estándar y no deben tener estilo. Deberían reflejar la apariencia estándar de los botones según lo dictado por el sistema operativo.

##### <a name="themed"></a>Temáticas
 En algunos casos, los botones se pueden usar dentro de la interfaz de usuario con estilo y estos botones deben tener el estilo adecuado. Vea [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles de los que se trata.

### <a name="special-buttons"></a>Botones especiales

#### <a name="browse-buttons"></a>Examinar... botones
 **[Examinar...]** los botones se usan en cuadrículas, cuadros de diálogo y ventanas de herramientas y otros elementos de interfaz de usuario no modales. Muestran un selector que ayuda al usuario a llenar un valor en un control. Hay dos variaciones de este botón: Long y Short.

 ![Botón de &#93; largo &#91;examinar...](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **El botón largo [examinar...]**

 ![Los puntos suspensivos cortos solo&#45;&#91;botón examinar... &#93;](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **El botón corto solo de puntos suspensivos [...]**

 Cuándo usar el botón corto solo de puntos suspensivos:

- Si hay más de un botón largo **[examinar...]** en un cuadro de diálogo, por ejemplo, cuando varios campos permiten la exploración. Use el botón **[...]** corto para que cada una de ellas Evite las claves de acceso confusas creadas en esta situación (**&examinar** y **B&filas** en el mismo cuadro de diálogo).

- En un cuadro de diálogo estrecho, o cuando no hay ningún lugar razonable para colocar el botón largo.

- Si el botón aparecerá en un control de cuadrícula.

  Instrucciones para usar el botón:

- No use una clave de acceso. Para tener acceso a ella mediante el teclado, el usuario debe hacer una tabulación desde el control adyacente. Asegúrese de que el orden de tabulación sea tal que cualquier botón de exploración esté inmediatamente después del campo que se va a rellenar. Nunca use un carácter de subrayado debajo del primer período.

- Establezca la propiedad **nombre** de Microsoft Active ACCESSIBILITY (MSAA) en **examinar...** (incluidos los puntos suspensivos) para que los lectores de pantalla lo lean como "examinar" y no como "punto-punto-punto" o "período-período". En el caso de los controles administrados, esto significa establecer la propiedad **AccessibleName** .

- Nunca use un botón de puntos suspensivos **[...]** para todo excepto una acción de exploración. Por ejemplo, si necesita un botón **[nuevo...]** pero no tiene espacio suficiente para el texto, es necesario volver a diseñar el cuadro de diálogo.

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
 ![Cambiar el tamaño de &#91;botones examinar... &#93;](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Ajustar el tamaño de los botones [examinar...]**

 ![Espaciado &#91;botones examinar... &#93;](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Botones de espaciado [examinar...]**

#### <a name="graphical-buttons"></a>Botones gráficos
 Algunos botones siempre deben usar una imagen gráfica y nunca incluir texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en los selectores de campos y en otras listas que se pueden ordenar.

> [!NOTE]
> Los usuarios tienen que tabular estos botones (no hay ninguna clave de acceso), por lo que se colocan en un orden razonable. Asigne la propiedad Name del botón a la acción que toma para que los lectores de pantalla interpreten correctamente la acción del botón.

|Nombre|Imagen|
|-|-|
|Sumar|![Botón gráfico "Agregar"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Remove|![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Agregar todo|![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Quitar todo|![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Subir|![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Bajar|![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Eliminar|![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
 El ajuste de tamaño de los botones gráficos es el mismo que el de la versión abreviada del botón **[examinar...]** (26x23 píxeles):

 ![Botón con y sin color transparente](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Apariencia de una imagen gráfica en el botón, con y sin color transparente que se muestra**

### <a name="hyperlinks"></a>Hipervínculos
 Los hipervínculos son idóneos para las acciones basadas en la navegación, como abrir un tema de ayuda, un cuadro de diálogo modal o un asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio visible y perceptible en la interfaz de usuario. En general, las acciones que se confirman en una acción (como guardar, cancelar y eliminar) se comunican mejor mediante un botón.

#### <a name="writing-style"></a>Estilo de escritura
 Siga las [instrucciones del escritorio de Windows para el texto de la interfaz de usuario](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). No use "obtener más información acerca de", "más información" o "obtener ayuda con esta". En su lugar, el texto del vínculo de la ayuda en términos de la pregunta principal respondida por el contenido de la ayuda. Por ejemplo, "**Cómo agregar un servidor al explorador de servidores?**"

#### <a name="visual-style"></a>Estilo visual

- Los hipervínculos siempre deben usar [el servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no tiene el estilo correcto, parpadea rojo cuando está activo o muestra un color diferente después de visitarlo.

- No incluya subrayados en el estado de reposo del control, a menos que el vínculo sea un fragmento de oración dentro de una frase completa, como en una marca de agua.

- Los subrayados no deben aparecer al mantener el mouse. En su lugar, los comentarios al usuario de que el vínculo está activo es un pequeño cambio de color y el cursor de vínculo adecuado.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Vistas de árbol

### <a name="overview"></a>Información general
 Las vistas de árbol proporcionan una manera de organizar listas complejas en grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer los grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento de una vista de árbol se puede seleccionar para proporcionar una acción adicional.

 En este tema se trata el uso aceptable, el diseño adecuado y la funcionalidad de las vistas de árbol.

#### <a name="in-this-topic"></a>En este tema

- [Estilo visual](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interacciones](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Estilo visual

#### <a name="expanders"></a>Expansores
 Los controles de vista de árbol deben ajustarse al diseño del expansor utilizado por Windows y Visual Studio. Cada nodo usa un control de expansor para mostrar u ocultar los elementos subyacentes. El uso de un control EXPANDER proporciona coherencia a los usuarios que pueden encontrar diferentes vistas de árbol en Windows y Visual Studio.

 ![Control de vista de árbol correcto](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correcto: estilo adecuado del nodo de vista de árbol mediante un control de expansor**

 ![Nodos de la vista de árbol incorrectos](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Incorrecto: estilo inadecuado del nodo de vista de árbol**

#### <a name="selection"></a>Selección
 Cuando se selecciona un nodo en la vista de árbol, el resaltado debe expandirse hasta el ancho completo del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Los colores de selección deben reflejar el tema actual de Visual Studio.

 ![Control de vista de árbol correcto](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correcto: el resaltado del nodo seleccionado se ajusta al ancho completo del control de vista de árbol.**

 ![Resaltado de la vista de árbol incorrecto](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Incorrecto: el resaltado del nodo seleccionado no cabe en todo el ancho del control de vista de árbol.**

#### <a name="icons"></a>Iconos
 Los iconos solo se deben usar en los controles de vista de árbol si ayudan a identificar visualmente las diferencias entre los elementos. En general, los iconos solo se deben usar en listas heterogéneas en las que los iconos llevan información para diferenciar los tipos de elementos. En una lista homogénea, el uso de iconos se puede considerar con frecuencia como ruido y debe evitarse. En ese caso, el icono de grupo (primario) puede transmitir el tipo de elementos que contiene. La excepción a esta regla sería si el icono es dinámico y se usa para indicar el estado.

#### <a name="scroll-bars"></a>Barras de desplazamiento
 Las barras de desplazamiento siempre se deben ocultar si el contenido cabe en el control de vista de árbol. Es aceptable que las barras de desplazamiento estén ocultas o semitransparentes en una ventana desplazable y aparezcan cuando la ventana que contiene la vista de árbol tiene el foco o al mantener el puntero sobre la propia vista de árbol.

 ![Vista de árbol con barras de desplazamiento](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Se muestran barras de desplazamiento verticales y horizontales porque el contenido ha superado los límites del control de vista de árbol.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a> Táctil

#### <a name="context-menus"></a>Menús contextuales
 Un nodo de vista de árbol puede revelar opciones de submenú en un menú contextual. Normalmente, esto sucede cuando un usuario ha hecho clic con el botón secundario en un elemento o ha presionado la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo obtenga el foco y esté seleccionado. Esto ayuda al usuario a identificar el elemento al que pertenece el submenú.

 ![Menú contextual y nodo de árbol seleccionados](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **El elemento que ha generado el menú contextual obtiene el foco para notificar al usuario qué elemento se ha seleccionado.**

#### <a name="keyboard"></a>Keyboard
 La vista de árbol debe proporcionar la capacidad de seleccionar elementos y de expandir o contraer los nodos con el teclado. Esto garantiza que la navegación cumple nuestros requisitos de accesibilidad.

##### <a name="tree-view-control"></a>Control de vista de árbol
 Los controles de árbol de Visual Studio deben seguir la navegación de teclado común:

- **Flecha arriba:** Seleccionar elementos al subir el árbol

- **Flecha abajo:** Seleccionar elementos desplazándose por el árbol

- **Flecha derecha:** Expandir un nodo en el árbol

- **Flecha izquierda:** Contraer un nodo en el árbol

- **Tecla entrar:** Iniciar, cargar, ejecutar elemento seleccionado

##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)
 Un control Trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar por el árbol debe respetar los mismos comandos de teclado que una vista de árbol, con las siguientes adiciones:

- **Flecha derecha:** Expanda un nodo. Después de expandir el nodo, debe continuar navegando a la columna más cercana de la derecha. La navegación debe detenerse al final de la fila.

- **Pestaña:** Navega a la celda más cercana de la derecha.  Al final de la fila, la navegación continúa hasta la siguiente fila.

- **Mayús + Tab:** Navega a la celda más cercana de la izquierda.  Al principio de la fila, la navegación continúa hasta la celda situada más a la derecha en la fila anterior.

  ![Control de TrID en Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Un control Trid en Visual Studio**
