---
title: Patrones de control comunes para Visual Studio ? Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698711"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de control comunes para Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Controles comunes

### <a name="overview"></a>Información general
Los controles comunes conforman la mayoría de la interfaz de usuario en Visual Studio. Los controles más comunes utilizados en la interfaz de Visual Studio deben seguir las directrices de interacción de escritorio de [Windows.](/windows/desktop/uxguide/controls) Este tema es específico de Visual Studio y cubre situaciones especiales o detalles que aumentan esas directrices de Windows.

#### <a name="common-controls-in-this-topic"></a>Controles comunes en este tema

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
Lo primero que hay que tener en cuenta al aplicar estilos a los controles es si los controles se usarán en la interfaz de usuario temática. Los controles de la interfaz de usuario estándar no son de interfaz de usuario y deben seguir el estilo normal de escritorio de [Windows,](/windows/desktop/uxguide/controls)lo que significa que no se vuelven a crear plantillas y deben aparecer en su apariencia de control predeterminada.

- **Diálogos estándar (utilidad):** no temáticos. No vuelvas a plantillar. Utilice los valores predeterminados de estilo de control básico.

- **Ventanas de herramientas, editores de documentos, superficies** de diseño y cuadros de diálogo temáticos: Utilice la apariencia temática especializada utilizando el servicio de color.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Barras de desplazamiento
 Las barras de desplazamiento deben seguir patrones de [interacción comunes para las barras](/windows/desktop/Controls/about-scroll-bars) de desplazamiento de Windows a menos que se aumenten con información de contenido, como en el editor de código.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Campos de entrada
 Para el comportamiento de interacción típico, siga las directrices de escritorio de [Windows para cuadros](/windows/desktop/uxguide/ctrl-text-boxes)de texto.

#### <a name="visual-style"></a>Estilo visual

- Los campos de entrada no deben aplicar estilo en los cuadros de diálogo de utilidad. Utilice el estilo básico intrínseco al control.

- Los campos de entrada temáticos solo deben utilizarse en cuadros de diálogo temáticos y ventanas de herramientas.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- Los campos de solo lectura tendrán un fondo gris (deshabilitado) pero un primer plano predeterminado (activo).

- Los campos obligatorios deben tener ** \<>obligatorios** como marcas de agua dentro de ellos. No debe cambiar el color del fondo excepto en situaciones raras.

- Validación de errores: consulte [Notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Los campos de entrada deben tener un tamaño que se ajuste al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para que coincidan arbitrariamente con la longitud de un campo largo, como una ruta de acceso. La longitud puede ser una indicación para el usuario de las limitaciones en cuanto a cuántos caracteres se permiten en el campo.

     ![Longitud de campo de entrada incorrecta: es poco probable que el nombre sea tan largo.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longitud de campo de entrada incorrecta: es poco probable que el nombre sea tan largo.

     ![Longitud correcta del campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Longitud correcta del campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Cuadros combinados y listas desplegables
Para el comportamiento de interacción típico, siga las directrices de escritorio de [Windows para listas desplegables y cuadros combinados.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de utilidad, no vuelva a crear una plantilla del control. Utilice el estilo básico intrínseco al control.

- En la interfaz de usuario temática, los cuadros combinados y los menús desplegables siguen el tema estándar de los controles.

#### <a name="layout"></a>Diseño
Los cuadros combinados y los menús desplegables deben tener un tamaño que se ajuste al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para que coincidan arbitrariamente con la longitud de un campo largo, como una ruta de acceso.

![Error: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Error: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará.

![Correcto: el tamaño de la lista desplegable permite el crecimiento de la traducción, pero no es innecesariamente largo.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correcto: el tamaño de la lista desplegable permite el crecimiento de la traducción, pero no es innecesariamente largo.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Casillas de verificación
Para el comportamiento de interacción típico, siga las directrices de escritorio de [Windows para las casillas](/windows/desktop/uxguide/ctrl-check-boxes)de verificación .

#### <a name="visual-style"></a>Estilo visual

- En los cuadros de diálogo de utilidad, no vuelva a crear una plantilla del control. Utilice el estilo básico intrínseco al control.

- En la interfaz de usuario temática, las casillas de verificación siguen el tema estándar para los controles.

#### <a name="specialized-interactions"></a>Interacciones especializadas

- La interacción con una casilla de verificación nunca debe abrir un cuadro de diálogo ni navegar a otra área.

- Alinee las casillas de verificación con la línea base de la primera línea de texto.

     ![Error: la casilla de verificación se centra en el texto.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Error: la casilla de verificación se centra en el texto.

     ![Correcto: la casilla de verificación está alineada con la primera línea del texto.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correcto: la casilla de verificación está alineada con la primera línea del texto.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Botones de radio
Para el comportamiento de interacción típico, siga las directrices de escritorio de [Windows para botones](/windows/desktop/uxguide/ctrl-radio-buttons)de opción.

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de utilidad, no aplicar estilo a los botones de opción. Utilice el estilo básico intrínseco al control.

#### <a name="specialized-interactions"></a>Interacciones especializadas
No es necesario utilizar una trama de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño ajustado.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Marcos de grupo
Para el comportamiento de interacción típico, siga las [directrices de escritorio](/windows/desktop/uxguide/ctrl-group-boxes)de Windows para marcos de grupo.

#### <a name="visual-style"></a>Estilo visual
En los cuadros de diálogo de utilidad, no estilizar marcos de grupo. Utilice el estilo básico intrínseco al control.

#### <a name="layout"></a>Diseño

- No es necesario utilizar una trama de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño ajustado.

- Nunca utilice un marco de grupo para un solo control.

- A veces es aceptable usar una regla horizontal en lugar de un contenedor de marco de grupo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Controles de texto

### <a name="static-text-fields"></a>Campos de texto estático

Un campo de texto estático presenta información de solo lectura y el usuario no puede seleccionarla. Evite usarlo para cualquier texto que el usuario desee copiar en el portapapeles. Sin embargo, el texto estático de solo lectura puede cambiar para reflejar un cambio de estado. En el ejemplo siguiente, el texto estático Nombre de salida en el grupo Información cambia para reflejar los cambios realizados en el cuadro de texto Espacio de nombres raíz situado encima de él.

Hay dos maneras de mostrar información de texto estático.

El texto estático puede estar solo en un cuadro de diálogo sin ninguna contención cuando no hay conflicto de agrupación. Decida si las líneas adicionales de una caja son realmente necesarias. Un ejemplo es la visualización de una ruta de directorio bajo una sección creada por una línea de grupo, como se muestra a continuación:

![Información de texto estático en controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Información de texto estático en controles de texto

En un cuadro de diálogo donde existen otras áreas agrupadas y la contención de la información ayudaría a la legibilidad, y cuando una sección se puede ocultar o mostrar (como en el panel de descripción de la **ventana Propiedades)** o desea ser coherente con una interfaz de usuario similar, coloque el texto estático dentro de un cuadro. Este cuadro de grupo debe ser `ButtonShadow`una sola regla y coloreado con:

![Texto estático en la ventana Propiedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático en la ventana Propiedades

### <a name="read-only-text-box"></a>Cuadro de texto de solo lectura

Esto permite al usuario seleccionar el texto dentro del campo pero no editarlo. Estos cuadros de texto están bordeados por `ButtonShadow` el cincel 3D habitual con un relleno.

Un cuadro de texto puede activarse (editable) cuando un usuario modifica un control asociado, como activar/desmarcar una casilla de verificación o seleccionar o anular la selección de un botón de opción. Por ejemplo, en la página ** &gt; Opciones** de herramientas que se muestra a continuación, el cuadro de texto **Página principal** se activa cuando la casilla Usar **predeterminado** está desactivada.

![Cuadro de texto de solo lectura, que muestra los estados inactivos y activos](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Cuadro de texto de solo lectura, que muestra los estados inactivos y activos

### <a name="using-text-in-dialogs"></a>Uso de texto en cuadros de diálogo

Directrices clave para el texto en los cuadros de diálogo:

- Las etiquetas de cuadros de texto, cuadros de lista y marcos en cuadros de diálogo sin tema comienzan con un verbo, tienen un mayúscula inicial solo en la primera palabra y terminan con dos puntos.

    > Los controles de texto de los cuadros de diálogo temáticos siguen [las directrices](/windows/desktop/uxguide/top-violations) de la experiencia de usuario de escritorio de Windows y no toman la puntuación final, con la excepción de los signos de interrogación en los vínculos de ayuda.

- Las etiquetas para las casillas de verificación y los botones de opción comienzan con un verbo, un mayúscula inicial solo en la primera palabra y no tienen puntuación final.

- Las etiquetas de botones, menús, elementos de menú y pestañas tienen mayúsculas iniciales en cada palabra (caso de título).

- La terminología de etiquetas debe ser coherente con etiquetas similares en otros cuadros de diálogo.

- Si es posible, pida a un escritor/editor que escriba o apruebe el texto antes de que vaya al desarrollador para su implementación.

- Todos los controles deben tener etiquetas, excepto en circunstancias especiales en las que la tabulación sea suficiente.
Utilice texto auxiliar cuando sea apropiado.

### <a name="helper-text"></a>Texto auxiliar

Incluido en los cuadros de diálogo para ayudar al usuario a entender el propósito del cuadro de diálogo o para indicar qué acción realizar. El texto auxiliar solo se debe usar cuando sea necesario para evitar el desorden de los cuadros de diálogo simples. Las dos variaciones del texto auxiliar son diálogo y marca de agua.

Siga las ubicaciones comunes para el texto auxiliar y sea selectivo en la introducción de nuevas áreas. Los escenarios comunes para el texto auxiliar son:

- Texto auxiliar en los cuadros de diálogo, para dar instrucciones adicionales sobre cómo interactuar con un cuadro de diálogo complejo.

- Texto de marca de agua en ventanas de herramientas o cuadros de diálogo vacíos, para explicar por qué no hay contenido visible.

- Un panel de descripción, como en la parte inferior de la **ventana Propiedades**.

- Texto de marca de agua en un editor vacío, para explicar qué acción debe realizar el usuario para empezar.

### <a name="dialog-helper-text"></a>Texto del asistente del cuadro de diálogo

Un diseñador de experiencia de usuario puede ayudar a determinar cuándo el texto auxiliar es adecuado. El diseñador puede definir dónde aparece el texto auxiliar, así como su contenido general. La asistencia del usuario puede escribir/editar el texto real.

### <a name="watermarks"></a>Marcas de agua

Los diálogos se benefician de pautas de marca de agua ligeramente diferentes. Dado que un cuadro de diálogo puede aparecer ocupado con muchos elementos de la interfaz de usuario (etiquetas, texto de `ButtonShadow`sugerencia, botones y otros controles de contenedor con texto), especialmente cuando aparecen en negro, las marcas de agua se destacan mejor en gris oscuro (VSColor: ). Normalmente, una marca de agua aparece dentro de un `Window`control como un cuadro de lista con un fondo blanco (VSColor: ).

- El texto aparece en gris `ButtonShadow`oscuro (VSColor: ). Sin embargo, si la marca de agua aparece `ButtonFace`en un fondo gris medio u otro color (VSColor: ) y hay preocupación sobre su legibilidad, vaya con texto negro (VSColor: `WindowText`).

- Las marcas de agua se pueden centrar o a la izquierda. Aplique reglas de diseño estándar al tomar decisiones de alineación. La marca de agua no se puede seleccionar en el fondo.

![Ejemplo de texto de marca de agua](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Ejemplo de texto de marca de agua

### <a name="context-specific-dynamic-text"></a>Texto específico del contexto (dinámico)

El texto dinámico se puede utilizar de dos maneras en un cuadro de diálogo o una interfaz de usuario no modificada: como una etiqueta dinámica o como contenido dinámico.

- Etiqueta dinámica: un uso común del texto dinámico se encuentra en paneles descriptivos que ofrecen más información para el elemento seleccionado, como en un cuadro de diálogo que contiene una lista de elementos y propiedades para los elementos que se muestran en una cuadrícula a la derecha. La etiqueta de la cuadrícula de propiedades puede ser dinámica para que cuando se selecciona un elemento a la izquierda, la cuadrícula de la derecha muestre información para ese elemento específico.

- Texto dinámico: puede ser útil en casos en los que necesita mostrar información específica y no información general de esta manera, pero se debe tener cuidado de no hacer uso excesivo.

Si desea que los usuarios tengan la capacidad de copiar la información, el texto dinámico debe estar en un campo de texto de solo lectura.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Botones e hipervínculos

### <a name="overview"></a>Información general
Los botones y controles de vínculo (hipervínculos) deben seguir las instrucciones básicas de Escritorio de [Windows sobre hipervínculos](/windows/desktop/uxguide/ctrl-links) para el uso, la redacción, el tamaño y el espaciado.

### <a name="choosing-between-buttons-and-links"></a>Elegir entre botones y enlaces
Tradicionalmente, los botones se han utilizado para acciones y los hipervínculos se han reservado para la navegación. Los botones se pueden usar en todos los casos, pero el rol de vínculos se ha expandido en Visual Studio para que los botones y vínculos sean más intercambiables en algunas condiciones.

Cuándo utilizar los botones de comando:

- Comandos primarios

- Visualización de ventanas utilizadas para recopilar entradas o tomar decisiones, incluso si son comandos secundarios

- Acciones destructivas o irreversibles

- Botones de compromiso dentro de los asistentes y flujos de página

Evite los botones de comando en las ventanas de herramientas o si necesita más de dos palabras para la etiqueta. Los vínculos pueden tener etiquetas más largas.

 Cuándo utilizar enlaces:

- Navegación a otra ventana, documento o página web

- Situaciones que requieren una etiqueta más larga o una frase corta para describir la intención de la acción

- Espacios estrechos donde un botón abrumaría a la interfaz de usuario, siempre que la acción no sea destructiva o irreversible

- Desenfatizar los comandos secundarios en situaciones en las que hay muchos comandos

#### <a name="examples"></a>Ejemplos
![Enlaces de comandos utilizados en la barra de información después de un mensaje de estado](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Enlaces de comandos utilizados en la barra de información después de un mensaje de estado

![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Vínculos que se usan en el menú emergente de CodeLens

![Enlaces utilizados para comandos secundarios donde los botones atraerían demasiada atención](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Enlaces utilizados para comandos secundarios donde los botones atraerían demasiada atención

### <a name="common-buttons"></a>Botones comunes

#### <a name="text"></a>Texto
Siga las directrices de escritura en el texto y la terminología de la interfaz de [usuario.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="visual-style"></a>Estilo visual

##### <a name="standard-unthemed"></a>Estándar (sin tema)
La mayoría de los botones de Visual Studio aparecerán en los cuadros de diálogo de la utilidad y no se deben aplicar estilos. Deben reflejar la apariencia estándar de los botones según lo dictado por el sistema operativo.

##### <a name="themed"></a>Temática
En algunos casos, los botones se pueden usar dentro de la interfaz de usuario con estilo y estos botones deben tener un estilo adecuado. Consulte [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles temáticos.

### <a name="special-buttons"></a>Botones especiales

#### <a name="browse-buttons"></a>Navega... Botones
**[Examinar...]** botones se utilizan en cuadrículas, cuadros de diálogo y ventanas de herramientas y otros elementos de interfaz de usuario no esmimoso. Muestran un selector que ayuda al usuario a rellenar un valor en un control. Hay dos variaciones de este botón, largo y corto.

![El botón largo [Examinar...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />El botón largo [Examinar...]

![El botón corto de puntos suspensivos [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />El botón corto de puntos suspensivos [...]

Cuándo utilizar el botón corto de solo puntos suspensivos:

- Si hay más de un botón largo **[Examinar...]** en un cuadro de diálogo, como cuando varios campos permiten la navegación. Utilice el botón corto **[...]** para cada uno para evitar las claves de acceso confusas creadas por esta situación** (&Examinar** y **B&rowse** en el mismo cuadro de diálogo).

- En un diálogo apretado, o cuando no hay un lugar razonable para colocar el botón largo.

- Si el botón aparecerá en un control de cuadrícula.

Directrices para el uso del botón:

- No utilice una clave de acceso. Para acceder a él mediante el teclado, el usuario debe tabular desde el control adyacente. Asegúrese de que el orden de tabulación es tal que cualquier botón de exploración cae inmediatamente después del campo que se rellenará. Nunca utilice un carácter de subrayado por debajo del primer período.

- Establezca la propiedad **Nombre** de microsoft Active Accessibility (MSAA) en **Examinar...** (incluidos los puntos suspensivos) para que los lectores de pantalla la lean como "Examinar" y no "punto-punto-punto" o "período-período-período." Para los controles administrados, esto significa establecer el **AccessibleName** propiedad.

- Nunca utilice un botón de puntos suspensivos **[...]** para nada excepto una acción de exploración. Por ejemplo, si necesita un botón **[Nuevo...]** pero no tiene suficiente espacio para el texto, el cuadro de diálogo debe rediseñarse.

##### <a name="sizing-and-spacing"></a>Tamaño y espaciado
![Botones de tamaño [Examinar...]: la versión estándar es de 75x23 píxeles, la versión corta es de 26x23 píxeles](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Tamaño de los botones [Examinar...]

![Espaciado [Examinar...]Botones: espaciado entre el control relacionado y el botón estándar Examinar 7 píxeles, espaciado entre el control relacionado y el botón corto Examinar 5 píxeles](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Espaciado de los botones [Examinar...]

#### <a name="graphical-buttons"></a>Botones gráficos
Algunos botones siempre deben usar una imagen gráfica y nunca incluir texto para ahorrar espacio y evitar problemas de localización. Estos se utilizan a menudo en selectores de campo y otras listas que se pueden ordenar.

> [!NOTE]
> Los usuarios tienen que tabular estos botones (no hay claves de acceso), así que colóquelos en un orden razonable. Asigne `name` la propiedad del botón a la acción que realiza para que los lectores de pantalla interpreten correctamente la acción del botón.

| Función | Botón |
| --- | --- |
| Sumar | ![Botón gráfico "Agregar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Agregar todo | ![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Quitar todo | ![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Subir | ![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Bajar | ![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Eliminar | ![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Tamaño y espaciado
El tamaño de los botones gráficos es el mismo que para la versión corta del botón **[Examinar...]** (26x23 píxeles):

![Apariencia de una imagen gráfica en el botón, con y sin color transparente que se muestra](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apariencia de una imagen gráfica en el botón, con y sin color transparente que se muestra

### <a name="hyperlinks"></a>Hipervínculos
Los hipervínculos son adecuados para acciones basadas en navegación, como abrir un tema de Ayuda, un cuadro de diálogo modal o un asistente. Si se utiliza un hipervínculo para un comando, siempre debe mostrar un cambio visible y notable en la interfaz de usuario. En general, las acciones que se confirman en una acción (como Guardar, Cancelar y Eliminar) se comunican mejor mediante un botón.

#### <a name="writing-style"></a>Estilo de escritura
Siga las instrucciones de escritorio de Windows para el texto de la interfaz de [usuario.](/windows/desktop/uxguide/text-ui) No uses frases sobre "Más información", "Cuéntame más" o "Obtén ayuda con esto". En su lugar, frase Ayuda vincular texto en términos de la pregunta principal respondida por el contenido de la Ayuda. Por ejemplo,**"¿Cómo agrego un servidor al Explorador**de servidores? "

#### <a name="visual-style"></a>Estilo visual

- Los hipervínculos siempre deben usar [el servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no tiene un estilo correcto, parpadea en rojo cuando está activo o muestra un color diferente después de ser visitado.

- No incluya subrayados en el estado de reposo del control a menos que el vínculo sea un fragmento de oración dentro de una oración completa, como en una marca de agua.

- Los subrayados no deben aparecer al pasar el ratón. En su lugar, los comentarios al usuario de que el vínculo está activo es un ligero cambio de color y el cursor de vínculo adecuado.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Vistas a los árboles

Las vistas de árbol proporcionan una manera de organizar listas complejas en grupos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento de una vista de árbol se puede seleccionar para proporcionar más acción.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Estilo visual de vista de árbol

#### <a name="expanders"></a>Expansores
Los controles de vista de árbol deben ajustarse al diseño del expansor utilizado por Windows y Visual Studio. Cada nodo utiliza un control de expansión para mostrar u ocultar los elementos subyacentes. El uso de un control de expansión proporciona coherencia a los usuarios que pueden encontrar diferentes vistas de árbol dentro de Windows y Visual Studio.

![Correcto: estilo adecuado del nodo de vista de árbol mediante un control de expansión](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: estilo adecuado del nodo de vista de árbol mediante un control de expansión

![Error: estilo incorrecto del nodo de vista de árbol](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Error: estilo incorrecto del nodo de vista de árbol

#### <a name="selection"></a>Número de selección
Cuando se selecciona un nodo dentro de la vista de árbol, el resaltado debe expandirse al ancho completo del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento han seleccionado. Los colores de selección deben reflejar el tema actual de Visual Studio.

![Correcto: el resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correcto: el resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.

![Error: el resaltado del nodo seleccionado no se ajusta a todo el ancho del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Error: el resaltado del nodo seleccionado no se ajusta a todo el ancho del control de vista de árbol.

#### <a name="icons"></a>Iconos
Los iconos solo se deben usar en los controles de vista de árbol si ayudan a identificar visualmente las diferencias entre los elementos. En general, los iconos deben utilizarse únicamente en listas heterogéneas en las que los iconos llevan información para diferenciar los tipos de elementos. En una lista homogénea el uso de iconos se puede ver con frecuencia como ruido y debe evitarse. En ese caso, el icono de grupo (principal) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se utiliza para indicar el estado.

#### <a name="scroll-bars"></a>Barras de desplazamiento
Las barras de desplazamiento siempre deben estar ocultas si el contenido se ajusta al control de vista de árbol. Es aceptable que las barras de desplazamiento estén ocultas o semitransparentes en una ventana desplazable y aparezcan cuando la ventana que contiene la vista de árbol tenga el foco o al pasar el cursor por la propia vista de árbol.

![Las barras de desplazamiento verticales y horizontales se muestran porque el contenido ha superado los límites del control de vista de árbol.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Las barras de desplazamiento verticales y horizontales se muestran porque el contenido ha superado los límites del control de vista de árbol.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interacciones con la vista de árbol

#### <a name="context-menus"></a>Menús contextuales
Un nodo de vista de árbol puede mostrar opciones de submenú en un menú contextual. Normalmente, esto ocurre cuando un usuario ha hecho clic con el botón derecho en un elemento o ha presionado la tecla Menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo gane el foco y esté seleccionado. Esto ayuda al usuario a identificar a qué elemento pertenece el submenú.

![El elemento que ha generado el menú contextual gana el foco para notificar al usuario qué elemento se ha seleccionado.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />El elemento que ha generado el menú contextual gana el foco para notificar al usuario qué elemento se ha seleccionado.

#### <a name="keyboard"></a>Teclado
La vista de árbol debe proporcionar la capacidad de seleccionar elementos y expandir o contraer nodos con el teclado. Esto garantiza que la navegación cumpla con nuestros requisitos de accesibilidad.

##### <a name="tree-view-control"></a>Control de vista de árbol
Los controles de árbol de Visual Studio deben seguir la navegación de teclado común:

- **Flecha arriba:** Seleccione elementos subiendo el árbol

- **Flecha abajo:** Seleccione elementos bajando el árbol

- **Flecha derecha:** Expandir un nodo en el árbol

- **Flecha izquierda:** Contraer un nodo en el árbol

- **Introduzca la clave:** Iniciar, cargar, ejecutar el elemento seleccionado

##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)
Un control trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar por el árbol debe respetar los mismos comandos de teclado que una vista de árbol, con las siguientes adiciones:

- **Flecha derecha:** Expanda un nodo. Después de expandir el nodo, debe continuar navegando a la columna más cercana a la derecha. La navegación debe detenerse al final de la fila.

- **Pestaña:** Navega a la celda más cercana a la derecha.  Al final de la fila, la navegación continúa a la siguiente fila.

- **Mayús + Tabulador:** Navega a la celda más cercana a la izquierda.  Al principio de la fila, la navegación continúa a la celda más a la derecha de la fila anterior.

![Un control trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un control trid en Visual Studio
