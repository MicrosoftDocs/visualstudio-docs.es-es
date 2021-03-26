---
title: Patrones de control comunes para Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo los controles comunes de Visual Studio siguen las instrucciones de interacción del escritorio de Windows y sobre las situaciones especiales que amplían esas directrices.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e55bb5f4473971f99ce04f9e48b7e05ec13f94c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090114"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de control comunes para Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Controles comunes

### <a name="overview"></a>Información general
Los controles comunes componen la mayor parte de la interfaz de usuario en Visual Studio. Los controles más comunes que se usan en la interfaz de Visual Studio deben seguir las [directrices de interacción del escritorio de Windows](/windows/desktop/uxguide/controls). Este tema es específico de Visual Studio y cubre situaciones especiales o detalles que aumentan esas directrices de Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comunes en este tema

- [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Casillas](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Agrupar marcos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Estilo visual
Lo primero que hay que tener en cuenta al aplicar estilos a los controles es si los controles se van a utilizar en la interfaz de usuario con nombre. Los controles de la interfaz de usuario estándar son una interfaz de usuario no relacionada y deben seguir el [estilo normal del escritorio de Windows](/windows/desktop/uxguide/controls), lo que significa que no se vuelven a crear plantillas y deben aparecer en su apariencia de control predeterminada.

- **Cuadros de diálogo estándar (utilidad):** no se trata de ellos. No volver a crear plantillas. Usar valores predeterminados de estilo de control básico.

- **Ventanas de herramientas, editores de documentos, superficies de diseño y cuadros de diálogo:** Use la apariencia especializada con el servicio de color.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Barras de desplazamiento
 Las barras de desplazamiento deben seguir [patrones de interacción comunes para las barras de desplazamiento de Windows](/windows/desktop/Controls/about-scroll-bars) , a menos que se aumenten con información de contenido, como en el editor de código.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Campos de entrada
 Para un comportamiento de interacción típico, siga las [instrucciones del escritorio de Windows para los cuadros de texto](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Estilo visual

- Los campos de entrada no deben tener estilo en los cuadros de diálogo de la utilidad. Use el estilo básico intrínseco para el control.

- Los campos de entrada con datos solo se deben usar en cuadros de diálogo y ventanas de herramientas.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Los campos de solo lectura tendrán un fondo gris (deshabilitado) pero el primer plano predeterminado (activo).

- Los campos obligatorios deben tener **\<Required>** como marcas de agua dentro de ellos. No debe cambiar el color del fondo excepto en raras ocasiones.

- Validación de errores: ver [notificaciones y progreso de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Los campos de entrada deben cambiar de tamaño para ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para que coincidan arbitrariamente con la longitud de un campo largo, como una ruta de acceso. La longitud puede ser una indicación al usuario de las limitaciones en cuanto al número de caracteres permitidos en el campo.

     ![Longitud de campo de entrada incorrecta: es improbable que el nombre sea este largo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longitud de campo de entrada incorrecta: es improbable que el nombre sea este largo.

     ![Longitud correcta del campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Longitud correcta del campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Cuadros combinados y listas desplegables
Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para las listas](/windows/desktop/uxguide/ctrl-drop)desplegables y los cuadros combinados.

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de la utilidad, no vuelva a crear la plantilla del control. Use el estilo básico intrínseco para el control.

- En la interfaz de usuario con la misma, los cuadros combinados y las listas desplegables siguen las áreas estándar de los controles.

#### <a name="layout"></a>Layout
Los cuadros combinados y las listas desplegables deben ajustarse al contenido, no ajustarse al ancho de la ventana en la que se muestran ni coincidir arbitrariamente con la longitud de un campo largo, como una ruta de acceso.

![Incorrecto: el ancho desplegable es demasiado largo para el contenido que se va a mostrar.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrecto: el ancho desplegable es demasiado largo para el contenido que se va a mostrar.

![Correcto: el tamaño de la lista desplegable es permitir el crecimiento de la traducción, pero no es innecesariamente largo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correcto: el tamaño de la lista desplegable es permitir el crecimiento de la traducción, pero no es innecesariamente largo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Casillas
Para un comportamiento de interacción típico, siga las [instrucciones del escritorio de Windows para las casillas](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de la utilidad, no vuelva a crear la plantilla del control. Use el estilo básico intrínseco para el control.

- En interfaz de usuario con la misma, las casillas siguen las áreas estándar de los controles.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- La interacción con una casilla nunca debe mostrar un cuadro de diálogo o desplazarse a otra área.

- Alinea las casillas con la línea de base de la primera línea de texto.

     ![Incorrecto: la casilla está centrada en el texto.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrecto: la casilla está centrada en el texto.

     ![Correcto: la casilla está alineada con la primera línea del texto.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correcto: la casilla está alineada con la primera línea del texto.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Botones de radio
Para un comportamiento de interacción típico, siga las [directrices del escritorio de Windows para los botones de radio](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de la utilidad, no aplicar estilo a los botones de radio. Use el estilo básico intrínseco para el control.

#### <a name="specialized-interactions"></a>Interacciones especializadas
No es necesario usar un marco de grupo para incluir las opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño estrecho.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Agrupar marcos
Para un comportamiento de interacción típico, siga las [directrices de escritorio de Windows para los marcos de grupo](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de la utilidad, no se estilo tramas de grupo. Use el estilo básico intrínseco para el control.

#### <a name="layout"></a>Layout

- No es necesario usar un marco de grupo para incluir las opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño estrecho.

- Nunca use un marco de grupo para un único control.

- A veces es aceptable usar una regla horizontal en lugar de un contenedor de tramas de grupo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Controles de texto

### <a name="static-text-fields"></a>Campos de texto estáticos

Un campo de texto estático presenta información de solo lectura y el usuario no puede seleccionarla. Evite usarlo para cualquier texto que el usuario desee copiar en el portapapeles. Sin embargo, el texto estático de solo lectura puede cambiar para reflejar un cambio de estado. En el ejemplo siguiente, el texto estático nombre de salida bajo el grupo de información cambia para reflejar los cambios realizados en el cuadro de texto espacio de nombres raíz situado encima de él.

Hay dos maneras de Mostrar información de texto estático.

El texto estático puede ser propio en un cuadro de diálogo sin contención cuando no hay ningún conflicto de agrupación. Decida si las líneas adicionales de un cuadro son realmente necesarias. Un ejemplo es la presentación de una ruta de acceso de directorio en una sección creada por una línea de grupo, como se muestra a continuación:

![Información de texto estático en controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Información de texto estático en controles de texto

En un cuadro de diálogo en el que existen otras áreas agrupadas y la contención de la información ayudaría a facilitar la lectura, y cuando una sección se puede ocultar o mostrar (como en el panel Descripción de **ventana Propiedades** ) o desea ser coherente con una interfaz de usuario similar, coloque el texto estático dentro de un cuadro. Este cuadro de grupo debe ser una sola regla y estar coloreado con lo `ButtonShadow` siguiente:

![Texto estático en el ventana Propiedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático en el ventana Propiedades

### <a name="read-only-text-box"></a>Cuadro de texto de solo lectura

Esto permite al usuario seleccionar el texto dentro del campo, pero no editarlo. Estos cuadros de texto están rodeados por el cincel 3D normal con un `ButtonShadow` relleno.

Un cuadro de texto puede convertirse en activo (editable) cuando un usuario modifica un control asociado, como activar o desactivar una casilla o seleccionar o anular la selección de un botón de radio. Por ejemplo, en la **página &gt; Opciones de herramientas** que se muestra a continuación, el cuadro de texto **Página principal** se activa cuando la casilla **usar predeterminada** está desactivada.

![Cuadro de texto de solo lectura que muestra los Estados inactivo y activo](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Cuadro de texto de solo lectura que muestra los Estados inactivo y activo

### <a name="using-text-in-dialogs"></a>Usar texto en cuadros de diálogo

Directrices clave para el texto en los cuadros de diálogo:

- Las etiquetas de los cuadros de texto, cuadros de lista y marcos en cuadros de diálogo desadados comienzan con un verbo, tienen un capital inicial solo en la primera palabra y terminan con un signo de dos puntos.

    > Los controles de texto en los cuadros de diálogo con tema siguen las directrices de la [experiencia de usuario de escritorio de Windows](/windows/desktop/uxguide/top-violations) y no toman puntuación final, a excepción de los signos de interrogación de los vínculos de ayuda.

- Las etiquetas de las casillas y los botones de opción comienzan con un verbo, una letra mayúscula inicial solo en la primera palabra y no tienen ningún signo de puntuación final.

- Las etiquetas de los botones, menús, elementos de menú y pestañas tienen mayúsculas iniciales en cada palabra (caso de título).

- La terminología de etiqueta debe ser coherente con etiquetas similares en otros cuadros de diálogo.

- Si es posible, haga que un escritor o editor escriba o apruebe el texto antes de que pase al desarrollador para su implementación.

- Todos los controles deben tener etiquetas excepto en casos especiales en los que sea suficiente la tabulación.
Use el texto auxiliar cuando sea necesario.

### <a name="helper-text"></a>Texto auxiliar

Se incluye en los cuadros de diálogo para ayudar al usuario a comprender el propósito del cuadro de diálogo o para indicar qué acción debe realizar. El texto de la aplicación auxiliar solo debe usarse cuando sea necesario para evitar la acumulación de cuadros de diálogo sencillos. Las dos variaciones del texto del ayudante son cuadro de diálogo y marca de agua.

Siga las ubicaciones comunes del texto del ayudante y sea selectivo en la introducción de nuevas áreas. Los escenarios comunes para el texto de la aplicación auxiliar son:

- Texto auxiliar en los cuadros de diálogo, para proporcionar una dirección adicional sobre cómo interactuar con un cuadro de diálogo complejo.

- Texto de marca de agua en ventanas de herramientas o cuadros de diálogo vacíos para explicar por qué no hay contenido visible.

- Un panel de descripción, como en la parte inferior del **ventana Propiedades**.

- Texto de marca de agua en un editor vacío para explicar qué acción debe realizar el usuario para comenzar.

### <a name="dialog-helper-text"></a>Texto del asistente del cuadro de diálogo

Un diseñador de experiencia del usuario puede ayudar a determinar cuándo es adecuado el texto del ayudante. El diseñador puede definir dónde aparece el texto auxiliar, así como su contenido general. La asistencia al usuario puede escribir o editar el texto real.

### <a name="watermarks"></a>Marcas de agua

Los cuadros de diálogo se benefician de las instrucciones de marcas de agua ligeramente diferentes. Dado que un cuadro de diálogo puede aparecer ocupado con muchos elementos de la interfaz de usuario (etiquetas, texto de sugerencia, botones y otros controles de contenedor con texto), especialmente cuando aparecen en negro, las marcas de agua se destacan mejor en gris oscuro (VSColor: `ButtonShadow` ). Normalmente aparece una marca de agua dentro de un control como un cuadro de lista con un fondo blanco (VSColor: `Window` ).

- El texto aparece en gris oscuro (VSColor: `ButtonShadow` ). Sin embargo, si la marca de agua aparece en un fondo gris medio u otro color (VSColor: `ButtonFace` ) y hay preocupación sobre su legibilidad, vaya a texto negro (VSColor: `WindowText` ).

- Las marcas de agua se pueden centrar o alinear a la izquierda. Aplicar reglas de diseño estándar al tomar decisiones de alineación. No se puede seleccionar la marca de agua en el fondo.

![Ejemplo de texto de marca de agua](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Ejemplo de texto de marca de agua

### <a name="context-specific-dynamic-text"></a>Texto específico del contexto (dinámico)

El texto dinámico se puede usar de dos maneras en un cuadro de diálogo no modal, como una etiqueta dinámica o como contenido dinámico.

- Etiqueta dinámica: un uso común de texto dinámico está en paneles descriptivos que ofrecen más información para el elemento seleccionado, como en un cuadro de diálogo que contiene una lista de elementos y propiedades para los elementos mostrados en una cuadrícula de la derecha. La etiqueta de la cuadrícula de propiedades puede ser dinámica, por lo que cuando se selecciona un elemento a la izquierda, la cuadrícula de la derecha muestra información de ese elemento específico.

- Texto dinámico: puede ser útil en instancias en las que necesite Mostrar información específica y no información general de esta manera, pero debe tener cuidado de no usar.

Si desea que los usuarios tengan la capacidad de copiar la información, el texto dinámico debe estar en un campo de texto de solo lectura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos

### <a name="overview"></a>Información general
Los botones y controles de vínculo (hipervínculos) deben seguir las [instrucciones básicas del escritorio de Windows en los hipervínculos](/windows/desktop/uxguide/ctrl-links) para el uso, el texto, el tamaño y el espaciado.

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
![Vínculos de comandos usados en la barra de estado después de un mensaje de estado](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Vínculos de comandos usados en la barra de estado después de un mensaje de estado

![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Vínculos que se usan en el menú emergente de CodeLens

![Vínculos usados para comandos secundarios en los que los botones atraerían demasiada atención](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Vínculos usados para comandos secundarios en los que los botones atraerían demasiada atención

### <a name="common-buttons"></a>Botones comunes

#### <a name="text"></a>Texto
Siga las instrucciones de escritura de la [terminología y el texto](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)de la interfaz de usuario.

#### <a name="visual-style"></a>Estilo visual

##### <a name="standard-unthemed"></a>Estándar (desvinculado)
La mayoría de los botones de Visual Studio aparecerán en los cuadros de diálogo de la utilidad y no deben tener estilo. Deberían reflejar la apariencia estándar de los botones según lo dictado por el sistema operativo.

##### <a name="themed"></a>Temáticas
En algunos casos, los botones se pueden usar dentro de la interfaz de usuario con estilo y estos botones deben tener el estilo adecuado. Vea [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles de los que se trata.

### <a name="special-buttons"></a>Botones especiales

#### <a name="browse-buttons"></a>Examinar... situados
**[Examinar...]** los botones se usan en cuadrículas, cuadros de diálogo y ventanas de herramientas y otros elementos de interfaz de usuario no modales. Muestran un selector que ayuda al usuario a llenar un valor en un control. Hay dos variaciones de este botón: Long y Short.

![El botón largo [examinar...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />El botón largo [examinar...]

![El botón corto solo de puntos suspensivos [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />El botón corto solo de puntos suspensivos [...]

Cuándo usar el botón corto solo de puntos suspensivos:

- Si hay más de un botón largo **[examinar...]** en un cuadro de diálogo, como cuando varios campos permiten la exploración. Use el botón **[...]** corto para que cada una de ellas Evite las claves de acceso confusas creadas en esta situación (**&examinar** y **B&filas** en el mismo cuadro de diálogo).

- En un cuadro de diálogo estrecho, o cuando no hay ningún lugar razonable para colocar el botón largo.

- Si el botón aparecerá en un control de cuadrícula.

Instrucciones para usar el botón:

- No use una clave de acceso. Para tener acceso a ella mediante el teclado, el usuario debe hacer una tabulación desde el control adyacente. Asegúrese de que el orden de tabulación sea tal que cualquier botón de exploración esté inmediatamente después del campo que se va a rellenar. Nunca use un carácter de subrayado debajo del primer período.

- Establezca la propiedad **nombre** de Microsoft Active ACCESSIBILITY (MSAA) en **examinar...** (incluidos los puntos suspensivos) para que los lectores de pantalla lo lean como "examinar" y no como "punto-punto-punto" o "período-período". En el caso de los controles administrados, esto significa establecer la propiedad **AccessibleName** .

- Nunca use un botón de puntos suspensivos **[...]** para todo excepto una acción de exploración. Por ejemplo, si necesita un botón **[nuevo...]** pero no tiene espacio suficiente para el texto, es necesario volver a diseñar el cuadro de diálogo.

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
![Cambiar el tamaño de los botones [examinar...]: la versión estándar es 75x23 píxeles, la versión abreviada es 26x23 píxeles](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Tamaño de los botones [Examinar...]

![Espaciado [examinar...] botones: espaciado entre el control relacionado y el botón de exploración estándar 7 píxeles, espaciado entre el control relacionado y el botón de exploración breve 5 píxeles](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Espaciado de los botones [Examinar...]

#### <a name="graphical-buttons"></a>Botones gráficos
Algunos botones siempre deben usar una imagen gráfica y nunca incluir texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en los selectores de campos y en otras listas que se pueden ordenar.

> [!NOTE]
> Los usuarios tienen que tabular estos botones (no hay ninguna clave de acceso), por lo que se colocan en un orden razonable. Asigne la `name` propiedad del botón a la acción que toma para que los lectores de pantalla interpreten correctamente la acción del botón.

| Función | Botón |
| --- | --- |
| Sumar | ![Botón gráfico "Agregar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Agregar todo | ![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Quitar todo | ![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Subir | ![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Bajar | ![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Eliminar | ![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado
El ajuste de tamaño de los botones gráficos es el mismo que el de la versión abreviada del botón **[examinar...]** (26x23 píxeles):

![Apariencia de una imagen gráfica en el botón, con y sin color transparente que se muestra](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apariencia de una imagen gráfica en el botón, con y sin color transparente que se muestra

### <a name="hyperlinks"></a>Hipervínculos
Los hipervínculos son idóneos para acciones basadas en navegación, como abrir un tema de ayuda, un cuadro de diálogo modal o un asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio visible y perceptible en la interfaz de usuario. En general, las acciones que se confirman en una acción (como guardar, cancelar y eliminar) se comunican mejor mediante un botón.

#### <a name="writing-style"></a>Estilo de escritura
Siga las [instrucciones del escritorio de Windows para el texto de la interfaz de usuario](/windows/desktop/uxguide/text-ui). No use "obtener más información acerca de", "más información" o "obtener ayuda con esta". En su lugar, el texto del vínculo de la ayuda en términos de la pregunta principal respondida por el contenido de la ayuda. Por ejemplo, "**Cómo agregar un servidor al explorador de servidores?**"

#### <a name="visual-style"></a>Estilo visual

- Los hipervínculos siempre deben usar [el servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no tiene el estilo correcto, parpadea rojo cuando está activo o muestra un color diferente después de visitarlo.

- No incluya subrayados en el estado de reposo del control, a menos que el vínculo sea un fragmento de oración dentro de una frase completa, como en una marca de agua.

- Los subrayados no deben aparecer al mantener el mouse. En su lugar, los comentarios al usuario de que el vínculo está activo es un pequeño cambio de color y el cursor de vínculo adecuado.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Vistas de árbol

Las vistas de árbol proporcionan una manera de organizar listas complejas en grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer los grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento de una vista de árbol se puede seleccionar para proporcionar una acción adicional.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Estilo visual de la vista de árbol

#### <a name="expanders"></a>Expansores
Los controles de vista de árbol deben ajustarse al diseño del expansor utilizado por Windows y Visual Studio. Cada nodo usa un control de expansor para mostrar u ocultar los elementos subyacentes. El uso de un control EXPANDER proporciona coherencia a los usuarios que pueden encontrar diferentes vistas de árbol en Windows y Visual Studio.

![Correcto: estilo adecuado del nodo de vista de árbol mediante un control de expansor](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: estilo adecuado del nodo de vista de árbol mediante un control de expansor

![Incorrecto: estilo inadecuado del nodo de vista de árbol](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrecto: estilo inadecuado del nodo de vista de árbol

#### <a name="selection"></a>Selección
Cuando se selecciona un nodo en la vista de árbol, el resaltado debe expandirse hasta el ancho completo del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Los colores de selección deben reflejar el tema actual de Visual Studio.

![Correcto: el resaltado del nodo seleccionado se ajusta al ancho completo del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: el resaltado del nodo seleccionado se ajusta al ancho completo del control de vista de árbol.

![Incorrecto: el resaltado del nodo seleccionado no se ajusta al ancho completo del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrecto: el resaltado del nodo seleccionado no se ajusta al ancho completo del control de vista de árbol.

#### <a name="icons"></a>Iconos
Los iconos solo se deben usar en los controles de vista de árbol si ayudan a identificar visualmente las diferencias entre los elementos. En general, los iconos solo se deben usar en listas heterogéneas en las que los iconos llevan información para diferenciar los tipos de elementos. En una lista homogénea, el uso de iconos se puede considerar con frecuencia como ruido y debe evitarse. En ese caso, el icono de grupo (primario) puede transmitir el tipo de elementos que contiene. La excepción a esta regla sería si el icono es dinámico y se usa para indicar el estado.

#### <a name="scroll-bars"></a>Barras de desplazamiento
Las barras de desplazamiento siempre se deben ocultar si el contenido cabe en el control de vista de árbol. Es aceptable que las barras de desplazamiento estén ocultas o semitransparentes en una ventana desplazable y aparezcan cuando la ventana que contiene la vista de árbol tiene el foco o al mantener el puntero sobre la propia vista de árbol.

![Se muestran barras de desplazamiento verticales y horizontales porque el contenido ha superado los límites del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Se muestran barras de desplazamiento verticales y horizontales porque el contenido ha superado los límites del control de vista de árbol.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interacciones de la vista de árbol

#### <a name="context-menus"></a>Menús contextuales
Un nodo de vista de árbol puede revelar opciones de submenú en un menú contextual. Normalmente, esto sucede cuando un usuario ha hecho clic con el botón secundario en un elemento o ha presionado la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo obtenga el foco y esté seleccionado. Esto ayuda al usuario a identificar el elemento al que pertenece el submenú.

![El elemento que ha generado el menú contextual obtiene el foco para notificar al usuario qué elemento se ha seleccionado.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />El elemento que ha generado el menú contextual obtiene el foco para notificar al usuario qué elemento se ha seleccionado.

#### <a name="keyboard"></a>Teclado
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

![Un control Trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un control Trid en Visual Studio
