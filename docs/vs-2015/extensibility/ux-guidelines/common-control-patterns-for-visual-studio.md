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
ms.openlocfilehash: 9644aeed1df42aa3a73af7d2cd7d7fa81bd27684
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040836"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de Control comunes para Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_CommonControls"></a> Controles comunes

### <a name="overview"></a>Información general
 Controles comunes constituyen la mayor parte de la interfaz de usuario en Visual Studio. Controles más comunes usados en la interfaz de Visual Studio deben seguir el [directrices de la interacción de escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este documento es específica de Visual Studio y trata situaciones especiales o los detalles que aumentan las directrices de Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comunes de este tema

- [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Los cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Casillas de verificación](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Marcos de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Estilo Visual
 Lo primero que debe considerar al aplicar un estilo a controles es si se usará los controles de interfaz de usuario con temas. Los controles de interfaz de usuario estándar son la interfaz de usuario que no sean temáticos y debe seguir [estilo normal de Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), lo que significa que no son con plantilla re y debe aparecer en su apariencia del control de forma predeterminada.

- **Los cuadros de diálogo estándar (utilidad):** no temáticas. Hacer no re-template. Usar valores predeterminados de estilo de control básico.

- **Ventanas de herramientas, editores de documentos, superficies de diseño y los cuadros de diálogo con temas:** Utilice apariencia con temas especializado con el servicio de color.

### <a name="BKMK_Scrollbars"></a> Barras de desplazamiento
 Deben seguir las barras de desplazamiento [patrones comunes de interacción de las barras de desplazamiento de Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) a menos que se han aumentado con la información de contenido, como en el editor de código.

### <a name="BKMK_InputFields"></a> Campos de entrada
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los cuadros de texto](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo Visual

- Los campos de entrada no deben cambiar el estilo en los cuadros de diálogo de utilidad. Utilice el estilo básico intrínseco para el control.

- Los campos de entrada con temas solo deben usarse en los cuadros de diálogo con temas y las ventanas de herramientas.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Campos de solo lectura tendrá un fondo gris (deshabilitado), pero el primer plano predeterminado (activa).

- Requiere los campos deben tener  **\<necesario >** como marcas de agua dentro de ellos. No debe cambiar el color de fondo, excepto en situaciones excepcionales.

- Validación de errores: Consulte [notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Los campos de entrada deben ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para arbitrariamente que coincida con la longitud de un campo largo, como una ruta de acceso. Longitud podría ser una indicación al usuario de límite en cuanto a cuántos caracteres se permiten en el campo.

     ![Ancho del control de campo de entrada incorrecto](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl") **longitud de campo de entrada incorrecta: No es probable que el nombre será así de largos.**

     ![Corrija el ancho del control de campo de entrada](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl") **longitud de campo de entrada correcto: El campo de entrada es un ancho razonable para el contenido esperado.**

### <a name="BKMK_ComboBoxesAndDropDowns"></a> Los cuadros combinados y listas desplegables
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para las listas desplegables y cuadros combinados](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo Visual

- En los cuadros de diálogo de utilidad hacer no re-template del control. Utilice el estilo básico intrínseco para el control.

- En la interfaz de usuario con temas, desplegables y cuadros combinados siguen los temas para los controles estándar.

#### <a name="layout"></a>Diseño
 Desplegables y cuadros combinados deben ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para arbitrariamente que coincida con la longitud de un campo largo, como una ruta de acceso.

 ![Colocación incorrecta&#45;abajo diseño](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")

 **Longitud de campo incorrecta para un control de lista desplegable**

 ![Colocación correcta&#45;abajo diseño](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")

 **Longitud de campo correcto para un control de lista desplegable**

### <a name="BKMK_CheckBoxes"></a> Casillas de verificación
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para las casillas de verificación](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo Visual

- En los cuadros de diálogo de utilidad hacer no re-template del control. Utilice el estilo básico intrínseco para el control.

- En la interfaz de usuario con temas, las casillas de verificación siga los temas para los controles estándar.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Interacción con una casilla de verificación nunca debe aparecer un cuadro de diálogo o navegar a otra área.

- Alinear las casillas de verificación con la línea de base de la primera línea de texto.

     ![Alineación de la casilla de verificación incorrecto](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign") **alineación de la casilla de verificación incorrecto: Casilla de verificación se centra en el texto.**

     ![Corrija la alineación de la casilla de verificación](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign") **corregir la alineación de la casilla de verificación: Casilla de verificación se alinea con la línea de base de la primera línea de texto.**

### <a name="BKMK_RadioButtons"></a> Botones de radio
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los botones de radio](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo Visual
 En los cuadros de diálogo de utilidad hacer no los botones de opción de estilo. Utilice el estilo básico intrínseco para el control.

#### <a name="specialized-interactions"></a>Interacciones especializadas
 No es necesario usar un marco de grupo para incluir opciones de radio.

### <a name="BKMK_GroupFrames"></a> Marcos de grupo
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los marcos de grupo](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Estilo Visual
 En los cuadros de diálogo de utilidad hacer marcos no de grupo de estilo. Utilice el estilo básico intrínseco para el control.

#### <a name="layout"></a>Diseño

- No es necesario usar un marco de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño de una estrecha.

- Nunca use un marco de grupo para un único control.

- A veces es aceptable el uso de una regla horizontal en lugar de un contenedor de marco de grupo.

## <a name="BKMK_TextControls"></a> Controles de texto

### <a name="labels"></a>Etiquetas

#### <a name="active-label-state"></a>Estado de la etiqueta de activo

##### <a name="utility-standard-dialogs"></a>Utility (estándar de) los cuadros de diálogo)

- En general, siga las instrucciones de escritorio de Windows para las etiquetas de control.

- En los cuadros de diálogo de utilidad, las etiquetas deben aparecer sin negrita, en el color de fuente y texto de entorno estándar. Consulte [fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Botón de puntos suspensivos siempre debe seguir las etiquetas.

##### <a name="signature-themed-dialogs"></a>Firma (temáticos) los cuadros de diálogo)
 Controles de etiqueta pueden ser negrita o gris claro.

#### <a name="disabled-label-state"></a>Estado de la etiqueta deshabilitado
 Las etiquetas deben reflejar la apariencia del control que están asociados. Por ejemplo, si se deshabilita el control asociado, la etiqueta debe aparecen atenuados y deshabilitados. Esto se suele tratar con el sistema operativo y no requiere ningún tratamiento especial.

#### <a name="dynamic-labels"></a>Etiquetas dinámicas
 Cambio de etiquetas dinámica según la selección actual. Siempre que sea posible, utilice etiquetas dinámicas en los diseños de maestro y detalles para ayudar al usuario a comprender que la información mostrada es relevante para una selección específica y obtener información general no.

 ![Etiqueta dinámica utilizada con contenido dinámico](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **Ejemplo de una etiqueta dinámica utilizada con contenido dinámico**

#### <a name="instructional-text"></a>Texto informativo
 Algunos elementos de la interfaz se benefician texto informativo para ayudar al usuario a comprender el propósito de la interfaz de usuario o para indicar qué acción realizar.

- Texto informativo es muy habitual en la parte superior de los cuadros de diálogo, pero puede aparecer en otras áreas para dar instrucciones a una agrupación de control complejo.

- Texto informativo no es interactivo, pero puede contener hipervínculos a temas de ayuda.

- Use el texto informativo con moderación y únicamente cuando sea necesario.

##### <a name="formatting"></a>Formato
 Texto informativo debe ser la fuente del entorno, texto del control (no temáticos) estándar. Consulte [fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Para obtener más información sobre cómo escribir texto de instrucciones, consulte [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Texto informativo en un cuadro de diálogo de Visual Studio**

#### <a name="informational-text"></a>Texto informativo
 Texto informativo es texto que proporciona la información adicional del usuario. Puede ser estática o dinámica o utilizarse como una notificación. Siempre es de solo lectura, pero si resulta útil para el usuario tenga la capacidad de copiar la información, se debe colocar texto dinámico en un contenedor de control como un campo de texto de solo lectura.

##### <a name="dynamic-context-specific-text"></a>Texto (específico de contexto) dinámico
 Texto de información dinámica varía según el contexto, por ejemplo, cuando el usuario cambia el foco. A menudo, pero no siempre, contenido dinámico se empareja con una etiqueta dinámica.

 ![Texto de información dinámica](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **Texto informativo dinámico varía según el contexto.**

##### <a name="formatting"></a>Formato
 Hay dos maneras de mostrar los campos de texto de solo lectura: ya sea directamente en la interfaz de usuario de superficie (vea más arriba) o dentro de otro control, como un cuadro de texto o el marco de grupo. Cualquiera sea correcta según la situación. Es el Diseñador de características para determinar cómo presentar la información de solo lectura.

 Puede ser texto dentro de un cuadro de texto de solo lectura. Esto suele indica que el contenido se puede seleccionar y copiar, aunque no se pueden editar.

 ![Formato de lectura de texto informativo&#45;solo campos](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **Formato de los campos de solo lectura de texto informativo**

#### <a name="watermarks"></a>Marcas de agua
 Aunque el texto puede ser el mismo, la diferencia entre las marcas de agua y el texto informativo es que las marcas de agua se reemplazan con contenido cuando la ventana de control no está vacía y el texto informativo permanece visible en todo momento.

 Las marcas de agua se deben usar cuando una ventana o control está vacío. Se indican qué debe hacerse para rellenar el área y pueden incluir vínculos de acción para abrir windows relevantes, como un origen de arrastre.

##### <a name="visual-style"></a>Estilo Visual

- Las marcas de agua se deben Centrar horizontalmente dentro de la ventana.

- Las marcas de agua deben ser centrado, no alineado a la izquierda.

- Las marcas de agua puede que sea centrados verticalmente o situados cerca de la parte superior del área. Si se encuentra en la parte superior del área, debe haber suficiente espacio por encima para que destaque la marca de agua.

- Use el `Environment.GrayText` fuente del entorno estándar y tokens de color. Los hipervínculos deben usar los tokens de hipervínculo estándar compartido: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, y `Environment.PanelHyperlinkDisabled`.

- No se pueden seleccionar las marcas de agua en segundo plano

- Si es posible, incluir vínculos en la marca de agua para ayudar al usuario a empezar a trabajar.

  ![Marca de agua de texto en una ventana del diseñador](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![Marca de agua de texto en una ventana de herramientas](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **Ejemplos de texto de marca de agua en Visual Studio**

## <a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos

### <a name="overview"></a>Información general
 Controles de botones y link (hipervínculos) deben seguir [instrucciones básicas de escritorio de Windows en los hipervínculos](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) para el uso de redacción, ajustar el tamaño y espaciado.

### <a name="choosing-between-buttons-and-links"></a>Elegir entre los botones y vínculos
 Tradicionalmente, los botones se han usado para las acciones y los hipervínculos se han reservado para la navegación. Se pueden usar los botones en todos los casos, pero se ha ampliado el rol de vínculos en Visual Studio para que los botones y los vínculos son más intercambiables en ciertas condiciones.

 Cuándo utilizar los botones de comando:

- Principales comandos

- Mostrar ventanas que se usan para recopilar la entrada o tomar decisiones, incluso si son comandos secundarios

- Acciones destructivas o irreversibles

- Botones de compromiso dentro de los asistentes y flujos de página

  Evite los botones de comando de ventanas de herramientas, o si necesita más de dos palabras de la etiqueta. Vínculos pueden tener más etiquetas.

  Cuando se usan los vínculos:

- Navegación a otra ventana, documento o página web

- Situaciones que requieran una etiqueta más tiempo o una frase corta para describir el propósito de la acción

- Espacios reducidos donde podría sobrecargar un botón de la interfaz de usuario, siempre que la acción no es destructivo o irreversible

- Deserialización realce comandos secundarios en situaciones donde hay muchos comandos

#### <a name="examples"></a>Ejemplos
 ![Vínculos de comando de barra de información que sigue a un mensaje de estado](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **Comando vínculos que se usan en la barra de información que sigue a un mensaje de estado**

 ![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **Vínculos que se usan en el menú emergente de CodeLens**

 ![Vínculos que se usan como comandos secundarios](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **Vínculos que se usan para los comandos secundaria donde botones conllevaría demasiada atención**

### <a name="common-buttons"></a>Botones comunes

#### <a name="text"></a>Texto
 Siga las instrucciones de escritura de [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Estilo Visual

##### <a name="standard-dialogs"></a>Cuadros de diálogo estándar
 La mayoría de los botones en Visual Studio aparecerán en los cuadros de diálogo estándares y no deben cambiar el estilo. Debe reflejar el aspecto de botones estándar dictado por el sistema operativo.

##### <a name="themed"></a>Con temas
 En algunos casos, se pueden usar los botones dentro de la interfaz de usuario con estilo y deben cambiar el estilo adecuadamente estos botones. Consulte [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles con tema.

### <a name="special-buttons"></a>Botones especiales

#### <a name="browse-buttons"></a>Examinar... botones
 **[Examinar...]**  botones se utilizan en las cuadrículas, cuadros de diálogo y las ventanas de herramientas y otros elementos de interfaz de usuario no modales. Muestra un selector que ayuda al usuario en rellenar un valor en un control. Hay dos variaciones de este botón, largo y corto.

 ![Long &#91;Examinar... &#93; botón](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **El botón [Examinar...] largo**

 ![Botón de puntos suspensivos a corto&#45;solo &#91;Examinar... &#93; botón](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **El botón corto con solo puntos suspensivos […]**

 Cuándo se debe usar el botón corto con solo puntos suspensivos:

- Si hay más de un largo **[Examinar...]**  botón en un cuadro de diálogo, por ejemplo, al permitir que varios campos para la exploración. Utilice el breve **[...]**  cada uno evitar las claves de acceso confuso creadas esta situación (**& Examinar** y **e & xaminar** en el mismo cuadro de diálogo).

- En un cuadro de diálogo estrecha, o cuando no hay ningún lugar razonable para colocar el botón de largo.

- Si el botón aparecerá en un control de cuadrícula.

  Directrices para usar el botón:

- No utilice una clave de acceso. Para acceder a ella mediante el teclado, el usuario debe tabulaciones desde el control adyacente. Asegúrese de que el orden de tabulación es tal que se encuentra ningún botón de examinar inmediatamente después del campo que va a rellenar. Nunca use un carácter de subrayado debajo del primer período.

- Establecer Microsoft Active Accessibility (MSAA) **nombre** propiedad **Examinar...**  (incluidos los puntos suspensivos) para que la pantalla se leerá, como "Examinar" y no "dot-punto" o "período período período." Esto implica la configuración de controles administrados, el **AccessibleName** propiedad.

- Nunca use un botón de puntos suspensivos **[...]**  botón salvo para una acción de exploración. Por ejemplo, si necesita un **[nuevo...]**  botón pero no tiene suficiente espacio para el texto, a continuación, debe volver a diseñar el cuadro de diálogo.

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
 ![Ajuste de tamaño &#91;Examinar... &#93; botones](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **Ajustar el tamaño de los botones [Examinar...]**

 ![Espaciado &#91;Examinar... &#93; botones](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **Espaciado entre botones [Examinar...]**

#### <a name="graphical-buttons"></a>Botones gráficos
 Algunos de los botones deben utilizar siempre una imagen gráfica y nunca incluyen texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en otras listas que se puede ordenar y selectores de campo.

> [!NOTE]
>  Los usuarios tienen que tabulador para ir a estos botones (no hay ninguna clave de acceso), colóquelos en un orden significativo. Asignar la propiedad name del botón a la acción que realiza para que los lectores de pantalla interpretan correctamente la acción del botón.

|||
|-|-|
|Agregar|![Botón "Agregar" gráfico](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|
|Quitar|![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|
|Agregar todo|![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|Quitar todo|![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|
|Subir|![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|Bajar|![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|Eliminar|![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
 Cambiar el tamaño de botones gráficos es el mismo que para la versión abreviada de la **[Examinar...]**  botón (26 x 23 píxeles):

 ![Botón con y sin color transparente](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **Apariencia de una imagen gráfica en el botón, con y sin color transparente**

### <a name="hyperlinks"></a>Hipervínculos
 Los hipervínculos son adecuados para las acciones basadas en la navegación, como la apertura de un tema de ayuda, cuadro de diálogo modal o el asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio notable y visible para la interfaz de usuario. En general, las acciones que se compromete a una acción (por ejemplo, guardar, Cancelar y eliminar) se comunican mejor mediante un botón.

#### <a name="writing-style"></a>Estilo de escritura
 Siga el [orientación de escritorio de Windows para el texto de la interfaz de usuario](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). No use "Aprender más acerca de," "Saber más acerca de" o "Get help con este" frases. En su lugar, frase de texto del vínculo de ayuda en cuanto a la pregunta principal por el contenido de ayuda. Por ejemplo, "**cómo agregar un servidor en el Explorador de servidores?**"

#### <a name="visual-style"></a>Estilo Visual

- Siempre deben usar hipervínculos [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no se ha adaptado correctamente, parpadea en color rojo cuando está activo o se muestra un color diferente después de que se visita.

- No incluya un subrayado en el control sobre el estado situado a menos que el vínculo es un fragmento de frase dentro de una frase completa, como en una marca de agua.

- No debe aparecer un subrayado al mantener el mouse. En su lugar, los comentarios al usuario que el vínculo está activo son un cambio de color pequeñas y el cursor del vínculo apropiado.

## <a name="BKMK_TreeViews"></a> Vistas de árbol

### <a name="overview"></a>Información general
 Vistas de árbol proporcionan una manera de organizar complejos se muestra en grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento dentro de una vista de árbol puede seleccionarse para proporcionar más acciones.

 Este tema trata el uso aceptable, el diseño adecuado y la funcionalidad de vistas de árbol.

#### <a name="in-this-topic"></a>En este tema

- [Estilo Visual](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interacciones](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="BKMK_TreeViewVisualStyle"></a> Estilo Visual

#### <a name="expanders"></a>Controles de expansión
 El diseño de botón de expansión utilizado por Windows y Visual Studio deben cumplir los controles de vista de árbol. Cada nodo utiliza un control expander para mostrar u ocultar los elementos subyacentes. Uso de un control expander proporciona una coherencia para los usuarios que pueden surgir vistas de árbol diferentes dentro de Windows y Visual Studio.

 ![Corrija el control de vista de árbol](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Correcto: estilo correspondiente del nodo de vista de árbol mediante un control expander**

 ![Nodos de la vista de árbol incorrecta](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **Incorrecta: estilo incorrecto del nodo de la vista de árbol**

#### <a name="selection"></a>Selección
 Cuando se selecciona un nodo dentro de la vista de árbol, debe expandir el resaltado para todo el ancho del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Colores de selección deben reflejar el tema actual de Visual Studio.

 ![Corrija el control de vista de árbol](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Correcto: resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.**

 ![Resaltado de la vista de árbol incorrecta](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **Incorrecta: el resaltado del nodo seleccionado no cabe todo el ancho del control de vista de árbol.**

#### <a name="icons"></a>Iconos
 Si ayudar a identificar visualmente las diferencias entre los elementos de iconos solo deben usarse en controles de vista de árbol. En general, los iconos deben usarse solo en listas heterogéneas en el que los iconos de llevan información para diferenciar los tipos de elementos. En una lista homogénea mediante iconos, con frecuencia pueden considerarse como ruido y debe evitarse. En ese caso, el icono de grupo (principal) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se utiliza para indicar el estado.

#### <a name="scroll-bars"></a>Barras de desplazamiento
 Siempre deben estar oculta las barras de desplazamiento si el contenido se ajusta dentro del control de vista de árbol. Es aceptable para las barras de desplazamiento se oculta o semitransparente en una ventana desplazable y aparecen cuando la ventana que contiene la vista de árbol tiene el foco, o después al mantener el mouse del árbol ver propio.

 ![Con las barras de desplazamiento de la vista de árbol](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol.**

### <a name="BKMK_TreeViewInteractions"></a> Interacciones

#### <a name="context-menus"></a>Menús contextuales
 Un nodo de vista de árbol puede mostrar las opciones de submenú en un menú contextual. Normalmente, esto se produce cuando un usuario ha hecho un elemento o presionó la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo recibe el foco y está seleccionado. Esto ayuda al usuario a identificar qué elemento al que pertenece el submenú.

 ![Menú contextual y nodo de árbol seleccionado](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **El elemento que se generan el foco de ganancias del menú contextual para notificar al usuario qué elemento se ha seleccionado.**

#### <a name="keyboard"></a>Teclado
 La vista de árbol debe proporcionar la capacidad de expandir y contraer los nodos mediante el teclado y seleccionar elementos. Esto garantiza que navegación cumple con nuestros requisitos de accesibilidad.

##### <a name="tree-view-control"></a>Control de vista de árbol
 Controles de árbol Visual Studio deben seguir la navegación de teclado comunes:

- **Arriba:** Seleccionar elementos moviendo el árbol

- **Abajo:** Seleccione los elementos al mover hacia abajo en el árbol

- **Flecha derecha:** Expanda un nodo en el árbol

- **Flecha izquierda:** Contraer un nodo en el árbol

- **Escriba la clave:** Iniciar, cargar, ejecutar el elemento seleccionado

##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)
 Un control de trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar por el árbol deben respetar los mismos comandos de teclado que una vista de árbol, con las siguientes adiciones:

- **Flecha derecha:** Expanda un nodo. Después de que el nodo está expandido, debe continuar navegar a la columna más cercana a la derecha. Exploración debe detenerse al final de la fila.

- **Tab:** Navega a la celda más cercana a la derecha.  Al final de la fila, navegación sigue a la siguiente fila.

- **Mayús + Tab:** Navega a la celda más cercana a la izquierda.  Al principio de la fila, navegación sigue a la celda situada en la fila anterior.

  ![Control de Trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **Un control de trid en Visual Studio**
