---
title: Patrones de control comunes para Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio controles comunes siguen las directrices de interacción del escritorio de Windows y sobre situaciones especiales que aumentan esas directrices.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899308"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de control comunes para Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Controles comunes

### <a name="overview"></a>Información general
Los controles comunes son la mayoría de la interfaz de usuario de Visual Studio. Los controles más comunes que se usan en Visual Studio interfaz deben seguir las [directrices](/windows/desktop/uxguide/controls)de interacción del escritorio de Windows . Este tema es específico de Visual Studio y trata situaciones especiales o detalles que aumentan esas directrices de Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comunes de este tema

- [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Casillas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Marcos de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Estilo visual
Lo primero que se debe tener en cuenta al aplicar estilos a los controles es si los controles se usarán en la interfaz de usuario con tema. Los controles de la interfaz de usuario estándar no son de interfaz de usuario y deben seguir el estilo de escritorio de [Windows normal,](/windows/desktop/uxguide/controls)lo que significa que no se vuelve a crear una plantilla y debe aparecer en su apariencia de control predeterminada.

- **Cuadros de diálogo estándar (utilidad):** no son de tipo themed. No vuelva a crear la plantilla. Use los valores predeterminados de estilo de control básico.

- **Ventanas de herramientas, editores de documentos, superficies de diseño y cuadros de diálogo con información:** Use una apariencia tema especializada mediante el servicio de color.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Barras de desplazamiento
 Las barras de desplazamiento deben seguir [patrones de interacción](/windows/desktop/Controls/about-scroll-bars) comunes para las barras de desplazamiento de Windows a menos que se aumenten con información de contenido, como en el editor de código.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Campos de entrada
 Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para los cuadros de texto](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Estilo visual

- Los campos de entrada no deben tener estilo en los cuadros de diálogo de la utilidad. Use el estilo básico intrínseco al control.

- Los campos de entrada con formato solo se deben usar en cuadros de diálogos y ventanas de herramientas con formato.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Los campos de solo lectura tendrán un fondo gris (deshabilitado), pero un primer plano predeterminado (activo).

- Los campos obligatorios deben **\<Required>** tener como marcas de agua dentro de ellos. No debe cambiar el color del fondo, excepto en situaciones poco frecuentes.

- Validación de errores: consulte [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Los campos de entrada deben ajustarse al contenido, no ajustarse al ancho de la ventana en la que se muestran ni coincidir arbitrariamente con la longitud de un campo largo, como una ruta de acceso. La longitud puede ser una indicación para el usuario de limitaciones en cuanto a cuántos caracteres se permiten en el campo.

     ![Longitud de campo de entrada incorrecta: es poco probable que el nombre sea tan largo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longitud de campo de entrada incorrecta: es poco probable que el nombre sea tan largo.

     ![Longitud correcta del campo de entrada: el campo de entrada tiene un ancho razonable para el contenido esperado.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Longitud correcta del campo de entrada: el campo de entrada tiene un ancho razonable para el contenido esperado.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Cuadros combinados y listas desplegables
Para un comportamiento de interacción típico, siga las directrices de [Escritorio de Windows para listas desplegables y cuadros combinados.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>Estilo visual

- En los diálogos de utilidad, no vuelva a crear plantillas del control. Use el estilo básico intrínseco al control.

- En la interfaz de usuario themed, los cuadros combinados y los menús desplegables siguen el formato de los controles.

#### <a name="layout"></a>Layout
Los cuadros combinados y los menús desplegables deben ajustarse al contenido, no ajustarse al ancho de la ventana en la que se muestran ni coincidir arbitrariamente con la longitud de un campo largo, como una ruta de acceso.

![Incorrecto: el ancho de lista desplegable es demasiado largo para el contenido que se mostrará.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrecto: el ancho de lista desplegable es demasiado largo para el contenido que se mostrará.

![Correcto: el tamaño de la lista desplegable permite el crecimiento de la traducción, pero no innecesariamente largo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correcto: el tamaño de la lista desplegable permite el crecimiento de la traducción, pero no innecesariamente largo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Casillas
Para un comportamiento de interacción típico, siga las instrucciones [de escritorio de Windows para las casillas](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Estilo visual

- En los diálogos de utilidad, no vuelva a crear plantillas del control. Use el estilo básico intrínseco al control.

- En la interfaz de usuario con problemas, las casillas siguen el formato de los controles.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- La interacción con una casilla nunca debe abrir un cuadro de diálogo ni navegar a otra área.

- Alinee las casillas con la línea base de la primera línea de texto.

     ![Incorrecto: la casilla se centra en el texto.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrecto: la casilla se centra en el texto.

     ![Correcto: la casilla está alineada con la primera línea del texto.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correcto: la casilla está alineada con la primera línea del texto.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Botones de radio
Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para los botones de radio](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de la utilidad, no estilo botones de radio. Use el estilo básico intrínseco al control.

#### <a name="specialized-interactions"></a>Interacciones especializadas
No es necesario usar un marco de grupo para incluir opciones de radio, a menos que tenga que mantener la distinción de grupo en un diseño ajustado.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Marcos de grupo
Para el comportamiento de interacción típico, siga las [directrices de escritorio de Windows para los marcos de grupo](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de la utilidad, no estilo los marcos de grupo. Use el estilo básico intrínseco al control.

#### <a name="layout"></a>Layout

- No es necesario usar un marco de grupo para incluir opciones de radio, a menos que tenga que mantener la distinción de grupo en un diseño ajustado.

- Nunca use un marco de grupo para un solo control.

- A veces es aceptable usar una regla horizontal en lugar de un contenedor de marco de grupo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Controles de texto

### <a name="static-text-fields"></a>Campos de texto estáticos

Un campo de texto estático presenta información de solo lectura y el usuario no puede seleccionarlo. Evite usarlo para cualquier texto que el usuario quiera copiar en el Portapapeles. Sin embargo, el texto estático de solo lectura puede cambiar para reflejar un cambio de estado. En el ejemplo siguiente, el texto estático Nombre de salida del grupo Información cambia para reflejar los cambios realizados en el cuadro de texto Espacio de nombres raíz situado encima de él.

Hay dos maneras de mostrar información de texto estático.

El texto estático puede estar solo en un cuadro de diálogo sin ninguna contención cuando no hay ningún conflicto de agrupación. Decida si las líneas adicionales de un cuadro son realmente necesarias. Un ejemplo es la presentación de una ruta de acceso de directorio en una sección creada por una línea de grupo, como se muestra a continuación:

![Información de texto estático en controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Información de texto estático en controles de texto

En un cuadro de diálogo donde existen otras áreas agrupadas y la contención de la información podría ayudar a la legibilidad, y cuando una sección se puede ocultar o mostrar (como en el panel de descripción de **ventana Propiedades)** o desea ser coherente con una interfaz de usuario similar, coloque el texto estático dentro de un cuadro. Este cuadro de grupo debe ser una sola regla y coloreado con `ButtonShadow` :

![Texto estático en el ventana Propiedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático en el ventana Propiedades

### <a name="read-only-text-box"></a>Cuadro de texto de solo lectura

Esto permite al usuario seleccionar el texto dentro del campo, pero no editarlo. Estos cuadros de texto están bordeados por el ósel 3D habitual con un `ButtonShadow` relleno.

Un cuadro de texto puede activarse (editable) cuando un usuario modifica un control asociado, como activar o desactivar una casilla o seleccionar o anular la selección de un botón de radio. Por ejemplo, en la página Opciones  **&gt; de** herramientas que se  muestra a continuación, el cuadro de texto Página principal se activa cuando la casilla Usar predeterminado está desactivada.

![Cuadro de texto de solo lectura, que muestra los estados inactivos y activos](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Cuadro de texto de solo lectura, que muestra los estados inactivos y activos

### <a name="using-text-in-dialogs"></a>Uso de texto en diálogos

Directrices clave para el texto en los diálogos:

- Las etiquetas de los cuadros de texto, los cuadros de lista y los marcos de los diálogos no escritos comienzan con un verbo, tienen un mayúscula inicial solo en la primera palabra y terminan con dos puntos.

    > Los controles de texto de los diálogos con tema siguen las directrices de la experiencia de usuario de escritorio de [Windows](/windows/desktop/uxguide/top-violations) y no toman signos de puntuación finales, a excepción de los signos de interrogación en los vínculos de Ayuda.

- Las etiquetas de las casillas y los botones de opción comienzan con un verbo, un mayúscula inicial solo en la primera palabra y no tienen signos de puntuación finales.

- Las etiquetas de botones, menús, elementos de menú y pestañas tienen mayúsculas iniciales en cada palabra (mayúsculas de título).

- La terminología de etiquetas debe ser coherente con etiquetas similares en otros cuadros de diálogo.

- Si es posible, haga que un escritor o editor escriba o apruebe el texto antes de que vaya al desarrollador para su implementación.

- Todos los controles deben tener etiquetas, excepto en circunstancias especiales en las que la tabulación es suficiente.
Use el texto del asistente cuando corresponda.

### <a name="helper-text"></a>Texto del asistente

Se incluye en los diálogos para ayudar al usuario a comprender el propósito del diálogo o para indicar qué acción realizar. El texto del asistente solo se debe usar cuando sea necesario para evitar que se abarroten los diálogos simples. Las dos variaciones del texto auxiliar son diálogo y marca de agua.

Siga las ubicaciones comunes para el texto del asistente y sea selectivo en la introducción de nuevas áreas. Los escenarios comunes para el texto auxiliar son:

- Texto auxiliar en diálogos, para proporcionar una dirección adicional sobre cómo interactuar con un diálogo complejo.

- Texto de marca de agua en ventanas de herramientas o cuadros de diálogo vacíos, para explicar por qué no hay contenido visible.

- Panel de descripción, como en la parte inferior de la **ventana Propiedades**.

- Texto de marca de agua en un editor vacío para explicar qué acción debe realizar el usuario para empezar.

### <a name="dialog-helper-text"></a>Texto del asistente del cuadro de diálogo

Un diseñador de experiencia del usuario puede ayudar a determinar cuándo es adecuado el texto del asistente. El diseñador puede definir dónde aparece el texto auxiliar, así como su contenido general. La asistencia del usuario puede escribir o editar el texto real.

### <a name="watermarks"></a>Marcas de agua

Los diálogos se benefician de directrices de marca de agua ligeramente diferentes. Dado que un cuadro de diálogo puede aparecer ocupado con muchos elementos de la interfaz de usuario (etiquetas, texto de sugerencias, botones y otros controles de contenedor con texto), especialmente cuando aparecen en negro, las marcas de agua se destacan mejor en gris oscuro (VSColor: `ButtonShadow` ). Normalmente, una marca de agua aparece dentro de un control como un cuadro de lista con un fondo blanco (VSColor: `Window` ).

- El texto aparece en gris oscuro (VSColor: `ButtonShadow` ). Sin embargo, si la marca de agua aparece en un fondo gris medio u otro color (VSColor: ) y hay preocupación sobre su legibilidad, vaya con texto negro `ButtonFace` (VSColor: `WindowText` ).

- Las marcas de agua se pueden centrar o vaciar a la izquierda. Aplicar reglas de diseño estándar al tomar decisiones de alineación. La marca de agua no se puede seleccionar en segundo plano.

![Ejemplo de texto de marca de agua](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Ejemplo de texto de marca de agua

### <a name="context-specific-dynamic-text"></a>Texto específico del contexto (dinámico)

El texto dinámico se puede usar de dos maneras en un cuadro de diálogo o interfaz de usuario modelesa: como etiqueta dinámica o como contenido dinámico.

- Etiqueta dinámica: un uso común de texto dinámico se encuentra en paneles descriptivos que ofrecen más información para el elemento seleccionado, como en un cuadro de diálogo que contiene una lista de elementos y propiedades para esos elementos mostrados en una cuadrícula a la derecha. La etiqueta de la cuadrícula de propiedades puede ser dinámica para que, cuando se selecciona un elemento a la izquierda, la cuadrícula de la derecha muestre información para ese elemento específico.

- Texto dinámico: puede ser útil en instancias en las que es necesario mostrar información específica y no información general de esta manera, pero se debe tener cuidado para no sobrecargar.

Si desea que los usuarios tengan la capacidad de copiar la información, el texto dinámico debe estar en un campo de texto de solo lectura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos

### <a name="overview"></a>Información general
Los botones y los controles de vínculo (hipervínculos) deben seguir las instrucciones básicas de Escritorio de Windows sobre [hipervínculos](/windows/desktop/uxguide/ctrl-links) para el uso, las palabras, el tamaño y el espaciado.

### <a name="choosing-between-buttons-and-links"></a>Elección entre botones y vínculos
Tradicionalmente, los botones se han usado para las acciones y los hipervínculos se han reservado para la navegación. Los botones se pueden usar en todos los casos, pero el rol de los vínculos se ha expandido en Visual Studio para que los botones y vínculos sean más intercambiables en algunas condiciones.

Cuándo usar botones de comando:

- Comandos principales

- Mostrar ventanas usadas para recopilar entradas o tomar decisiones, incluso si son comandos secundarios

- Acciones destructivas o irreversibles

- Botones de compromiso dentro de asistentes y flujos de página

Evite los botones de comando en las ventanas de herramientas o si necesita más de dos palabras para la etiqueta. Los vínculos pueden tener etiquetas más largas.

 Cuándo usar vínculos:

- Navegación a otra ventana, documento o página web

- Situaciones que requieren una etiqueta más larga o una frase corta para describir la intención de la acción

- Espacios estrechos en los que un botón sobrecargaría la interfaz de usuario, siempre que la acción no sea destructiva o irreversible.

- Desasoción de comandos secundarios en situaciones en las que hay muchos comandos

#### <a name="examples"></a>Ejemplos
![Vínculos de comandos usados en la barra de información después de un mensaje de estado](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Vínculos de comandos usados en la barra de información después de un mensaje de estado

![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Vínculos que se usan en el menú emergente de CodeLens

![Vínculos usados para comandos secundarios donde los botones atraerían demasiada atención](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Vínculos usados para comandos secundarios en los que los botones atraerían demasiada atención

### <a name="common-buttons"></a>Botones comunes

#### <a name="text"></a>Texto
Siga las directrices de escritura en el texto [de la interfaz de usuario y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Estilo visual

##### <a name="standard-unthemed"></a>Estándar (sin ateso)
La mayoría de los Visual Studio aparecerán en los cuadros de diálogo de la utilidad y no deben tener estilo. Deben reflejar la apariencia estándar de los botones según lo dictado por el sistema operativo.

##### <a name="themed"></a>Temática
En algunos casos, los botones se pueden usar dentro de la interfaz de usuario con estilo y estos botones deben tener el estilo adecuado. Vea [Diálogos para](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) obtener información sobre los controles con formato.

### <a name="special-buttons"></a>Botones especiales

#### <a name="browse-buttons"></a>Navega... Botones
**[Examinar...]** Los botones se usan en cuadrículas, cuadros de diálogo, ventanas de herramientas y otros elementos de interfaz de usuario modelados. Muestran un selector que ayuda al usuario a rellenar un valor en un control. Hay dos variaciones de este botón, long y short.

![Botón largo [Examinar...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Botón largo [Examinar...]

![Botón corto solo de puntos suspensivos [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Botón corto solo de puntos suspensivos [...]

Cuándo usar el botón corto de solo puntos suspensivos:

- Si hay más de un botón **largo [Examinar...] en** un cuadro de diálogo, como cuando varios campos permiten examinar. Use el botón **corto [...]** para cada una de ellas para evitar las claves de acceso confusas creadas por esta situación **(&Examinar** y B&fila **en** el mismo cuadro de diálogo).

- En un cuadro de diálogo ajustado o cuando no hay ningún lugar razonable para colocar el botón largo.

- Si el botón aparecerá en un control de cuadrícula.

Directrices para usar el botón:

- No use una clave de acceso. Para acceder a él mediante el teclado, el usuario debe tabular desde el control adyacente. Asegúrese de que el orden de tabulación sea tal que cualquier botón Examinar se encuentre inmediatamente después del campo que rellenará. Nunca use un carácter de subrayado por debajo del primer período.

- Establezca la propiedad nombre Microsoft Active Accessibility  (MSAA) en **Examinar...** (incluidos los puntos suspensivos) para que los lectores de pantalla lo lean como "Examinar" y no como "punto-punto" o "punto-período-período". Para los controles administrados, esto significa establecer la **propiedad AccessibleName.**

- Nunca use un botón de puntos suspensivos **[...]** para nada excepto una acción de exploración. Por ejemplo, si necesita un **botón [Nuevo...]** pero no tiene suficiente espacio para el texto, el cuadro de diálogo debe rediseñarse.

##### <a name="sizing-and-spacing"></a>Tamaño y espaciado
![Botones de tamaño [Examinar...]: la versión estándar es de 75 x 23 píxeles, la versión corta es de 26 x 23 píxeles.](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Tamaño de los botones [Examinar...]

![Botones de espaciado [Examinar...]: espaciado entre el control relacionado y el botón Examinar estándar de 7 píxeles, espaciado entre el control relacionado y el botón Examinar corto de 5 píxeles](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Espaciado de los botones [Examinar...]

#### <a name="graphical-buttons"></a>Botones gráficos
Algunos botones siempre deben usar una imagen gráfica y nunca incluir texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en selectores de campos y otras listas que se pueden ordenar.

> [!NOTE]
> Los usuarios tienen que ir a estos botones (no hay claves de acceso), por lo que deben colocarlos en un orden razonable. Asigne la propiedad del botón a la acción que realiza para que los lectores de pantalla `name` interpreten correctamente la acción del botón.

| Función | Botón |
| --- | --- |
| Sumar | ![Botón gráfico "Agregar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Quitar | ![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Agregar todo | ![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Quitar todo | ![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Subir | ![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Bajar | ![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Eliminar | ![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Tamaño y espaciado
El tamaño de los botones gráficos es el mismo que para la versión corta del botón **[Examinar...]** (26 x 23 píxeles):

![Apariencia de una imagen gráfica en el botón, con y sin mostrar color transparente](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apariencia de una imagen gráfica en el botón, con y sin mostrar color transparente

### <a name="hyperlinks"></a>Hipervínculos
Los hipervínculos son adecuados para las acciones basadas en navegación, como abrir un tema de Ayuda, un diálogo modal o un asistente. Si se usa un hipervínculo para un comando, siempre debe mostrar un cambio visible y perceptible en la interfaz de usuario. En general, las acciones que se confirman en una acción (como Guardar, Cancelar y Eliminar) se comunican mejor mediante un botón.

#### <a name="writing-style"></a>Estilo de escritura
Siga las instrucciones [de escritorio de Windows para el texto de la interfaz de usuario](/windows/desktop/uxguide/text-ui). No use las expresiones "Más información sobre", "Cuénteme más información" o "Obtener ayuda con esto". En su lugar, la frase Ayuda vincula texto en términos de la pregunta principal que responde el contenido de ayuda. Por ejemplo,**"Cómo agregar un servidor al Explorador de servidores?"**

#### <a name="visual-style"></a>Estilo visual

- Los hipervínculos siempre deben [usar el servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no tiene el estilo correcto, parpadea en rojo cuando está activo o muestra un color diferente después de visitarlo.

- No incluya subrayados en el estado de reposo del control a menos que el vínculo sea un fragmento de oración dentro de una oración completa, como en una marca de agua.

- Los subrayados no deben aparecer al mantener el puntero. En su lugar, los comentarios al usuario de que el vínculo está activo son un pequeño cambio de color y el cursor de vínculo adecuado.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Vistas de árbol

Las vistas de árbol proporcionan una manera de organizar listas complejas en grupos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar elementos secundarios subyacentes. Se puede seleccionar cada elemento dentro de una vista de árbol para proporcionar una acción adicional.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Estilo visual de la vista de árbol

#### <a name="expanders"></a>Expansores
Los controles de vista de árbol deben ajustarse al diseño del expansor usado por Windows y Visual Studio. Cada nodo usa un control expander para mostrar u ocultar elementos subyacentes. El uso de un control expander proporciona coherencia a los usuarios que pueden encontrar diferentes vistas de árbol en Windows y Visual Studio.

![Correcto: estilo correcto del nodo de vista de árbol mediante un control de expansor](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: estilo correcto del nodo de vista de árbol mediante un control de expansor

![Incorrecto: estilo incorrecto del nodo de vista de árbol](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrecto: estilo incorrecto del nodo de vista de árbol

#### <a name="selection"></a>Selección
Cuando se selecciona un nodo dentro de la vista de árbol, el resaltado debe expandirse hasta el ancho completo del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento han seleccionado. Los colores de selección deben reflejar el tema Visual Studio actual.

![Correcto: el resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: el resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.

![Incorrecto: el resaltado del nodo seleccionado no se ajusta a todo el ancho del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrecto: el resaltado del nodo seleccionado no se ajusta a todo el ancho del control de vista de árbol.

#### <a name="icons"></a>Iconos
Los iconos solo se deben usar en los controles de vista de árbol si ayudan a identificar visualmente las diferencias entre los elementos. En general, los iconos solo se deben usar en listas heterogéneos en las que los iconos incluyen información para diferenciar los tipos de elementos. En una lista homogéneo, el uso de iconos se puede ver con frecuencia como ruido y debe evitarse. En ese caso, el icono de grupo (primario) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se usa para indicar el estado.

#### <a name="scroll-bars"></a>Barras de desplazamiento
Las barras de desplazamiento siempre deben estar ocultas si el contenido se ajusta al control de vista de árbol. Es aceptable que las barras de desplazamiento se ocultan o que sean semitransparentes en una ventana desplazable y aparezcan cuando la ventana que contiene la vista de árbol tenga el foco o al mantener el puntero sobre la propia vista de árbol.

![Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interacciones de la vista de árbol

#### <a name="context-menus"></a>Menús contextuales
Un nodo de vista de árbol puede mostrar opciones de submenú en un menú contextual. Normalmente, esto sucede cuando un usuario ha hecho clic con el botón derecho en un elemento o ha presionado la tecla Menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo se centre y esté seleccionado. Esto ayuda al usuario a identificar a qué elemento pertenece el submenú.

![El elemento que ha generado el menú contextual obtiene el foco para notificar al usuario qué elemento se ha seleccionado.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />El elemento que ha generado el menú contextual obtiene el foco para notificar al usuario qué elemento se ha seleccionado.

#### <a name="keyboard"></a>Teclado
La vista de árbol debe proporcionar la capacidad de seleccionar elementos y expandir o contraer nodos mediante el teclado. Esto garantiza que la navegación cumpla nuestros requisitos de accesibilidad.

##### <a name="tree-view-control"></a>Control de vista de árbol
Visual Studio los controles de árbol deben seguir la navegación con el teclado común:

- **Flecha arriba:** Selección de elementos moviendo el árbol hacia arriba

- **Flecha abajo:** Selección de elementos desplazando el árbol hacia abajo

- **Flecha derecha:** Expansión de un nodo en el árbol

- **Flecha izquierda:** Contraer un nodo en el árbol

- **Escriba la clave:** Iniciar, cargar y ejecutar el elemento seleccionado

##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)
Un control trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar por el árbol debe respetar los mismos comandos de teclado que una vista de árbol, con las siguientes adiciones:

- **Flecha derecha:** Expanda un nodo. Una vez expandido el nodo, debe continuar navegando a la columna más cercana de la derecha. La navegación debe detenerse al final de la fila.

- **Pestaña:** Navega a la celda más cercana de la derecha.  Al final de la fila, la navegación continúa hasta la siguiente fila.

- **Mayús + Pestaña:** Navega a la celda más cercana de la izquierda.  Al principio de la fila, la navegación continúa hasta la celda situada más a la derecha de la fila anterior.

![Un control trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un control trid en Visual Studio
