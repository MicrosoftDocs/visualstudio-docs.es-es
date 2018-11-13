---
title: Patrones de Control comunes para Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e10fdcea9819c34735f285c78a0e2ebb0650f64a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512322"
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de Control comunes para Visual Studio
##  <a name="BKMK_CommonControls"></a> Controles comunes  
  
### <a name="overview"></a>Información general  
Controles comunes constituyen la mayor parte de la interfaz de usuario en Visual Studio. Controles más comunes usados en la interfaz de Visual Studio deben seguir el [directrices de la interacción de escritorio de Windows](/windows/desktop/uxguide/controls). En este tema es específico de Visual Studio y se trata situaciones especiales o los detalles que aumentan las directrices de Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Controles comunes de este tema  
  
-   [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Los cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Casillas de verificación](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Marcos de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Estilo Visual  
Lo primero que debe considerar al aplicar un estilo a controles es si se usará los controles de interfaz de usuario con temas. Los controles de interfaz de usuario estándar son la interfaz de usuario que no sean temáticos y debe seguir [estilo normal de Windows Desktop](/windows/desktop/uxguide/controls), lo que significa que no son con plantilla re y debe aparecer en su apariencia del control de forma predeterminada.  
  
-   **Los cuadros de diálogo estándar (utilidad):** no temáticas. No re-template. Usar valores predeterminados de estilo de control básico.  
  
-   **Ventanas de herramientas, editores de documentos, superficies de diseño y los cuadros de diálogo con temas:** usar apariencia con temas especializado con el servicio de color.  
  
###  <a name="BKMK_Scrollbars"></a> Barras de desplazamiento  
 Deben seguir las barras de desplazamiento [barras de desplazamiento de los patrones comunes de interacción de Windows](/windows/desktop/Controls/about-scroll-bars) a menos que estén ampliadas con información de contenido, como en el editor de código.  
  
###  <a name="BKMK_InputFields"></a> Campos de entrada  
 Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los cuadros de texto](/windows/desktop/uxguide/ctrl-text-boxes).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Los campos de entrada no deben cambiar el estilo en los cuadros de diálogo de utilidad. Utilice el estilo básico intrínseco para el control.  
  
-   Los campos de entrada con temas solo deben usarse en los cuadros de diálogo con temas y las ventanas de herramientas.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
  
-   Campos de solo lectura tendrá un fondo gris (deshabilitado), pero el primer plano predeterminado (activa).  
  
-   Requiere los campos deben tener  **\<necesario >** como marcas de agua dentro de ellos. No debe cambiar el color de fondo, excepto en situaciones excepcionales.  
  
-   Validación de errores: consulte [notificaciones y progreso para Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Los campos de entrada deben ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para arbitrariamente que coincida con la longitud de un campo largo, como una ruta de acceso. Longitud podría ser una indicación al usuario de límite en cuanto a cuántos caracteres se permiten en el campo.  
  
     ![Longitud de campo de entrada incorrecta: no es probable que el nombre será así de largos. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Longitud de campo de entrada incorrecta: no es probable que el nombre será así de largos.
  
     ![Corrija la longitud de campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Corrija la longitud de campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Los cuadros combinados y listas desplegables  
Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para las listas desplegables y cuadros combinados](/windows/desktop/uxguide/ctrl-drop).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   En los cuadros de diálogo de utilidad no re-template del control. Utilice el estilo básico intrínseco para el control.  
  
-   En la interfaz de usuario con temas, desplegables y cuadros combinados siguen los temas para los controles estándar.  
  
#### <a name="layout"></a>Diseño  
Desplegables y cuadros combinados deben ajustarse al contenido, no para ajustarse al ancho de la ventana en la que se muestran, ni para arbitrariamente que coincida con la longitud de un campo largo, como una ruta de acceso.  
  
![Incorrecto: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Incorrecto: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará.
  
![Correcto: la lista desplegable tiene el tamaño para permitir el crecimiento de traducción, pero no innecesariamente largas. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Correcto: la lista desplegable tiene el tamaño para permitir el crecimiento de traducción, pero no innecesariamente largas. 
  
###  <a name="BKMK_CheckBoxes"></a> Casillas de verificación  
Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para las casillas de verificación](/windows/desktop/uxguide/ctrl-check-boxes).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   En los cuadros de diálogo de utilidad no re-template del control. Utilice el estilo básico intrínseco para el control.  
  
-   En la interfaz de usuario con temas, las casillas de verificación siga los temas para los controles estándar.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
  
-   Interacción con una casilla de verificación nunca debe aparecer un cuadro de diálogo o navegar a otra área.  
  
-   Alinear las casillas de verificación con la línea de base de la primera línea de texto.  
  
     ![Incorrecto: la casilla de verificación se centra en el texto. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Incorrecto: la casilla de verificación se centra en el texto.
  
     ![Correcto: la casilla de verificación se alinea con la primera línea del texto. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Correcto: la casilla de verificación se alinea con la primera línea del texto.
  
###  <a name="BKMK_RadioButtons"></a> Botones de radio  
Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los botones de radio](/windows/desktop/uxguide/ctrl-radio-buttons).  
  
#### <a name="visual-style"></a>Estilo Visual  
En los cuadros de diálogo de utilidad hacer no los botones de opción de estilo. Utilice el estilo básico intrínseco para el control.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
No es necesario usar un marco de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño de una estrecha.  
  
###  <a name="BKMK_GroupFrames"></a> Marcos de grupo  
Para el comportamiento de una interacción típica, siga el [directrices de escritorio de Windows para los marcos de grupo](/windows/desktop/uxguide/ctrl-group-boxes).  
  
#### <a name="visual-style"></a>Estilo Visual  
En los cuadros de diálogo de utilidad no aplicar estilo a los marcos de grupo. Utilice el estilo básico intrínseco para el control.  
  
#### <a name="layout"></a>Diseño  
  
-   No es necesario usar un marco de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño de una estrecha.  
  
-   Nunca use un marco de grupo para un único control.  
  
-   A veces es aceptable el uso de una regla horizontal en lugar de un contenedor de marco de grupo.  
  
##  <a name="BKMK_TextControls"></a> Controles de texto

### <a name="static-text-fields"></a>Campos de texto estático

Un campo de texto estático presenta información de solo lectura y no se puede seleccionar el usuario. No lo use para cualquier texto que el usuario podría desear copiar al Portapapeles. Sin embargo, puede cambiar el texto estático de solo lectura para reflejar un cambio de estado. En el ejemplo siguiente, el texto estático del nombre de salida en los cambios de grupo de información para reflejar los cambios realizados en el cuadro de texto raíz Namespace por encima de él.

Hay dos maneras de mostrar información de texto estático.

Puede ser texto estático en su propio en un cuadro de diálogo sin ningún contención cuando no hay ningún conflicto de agrupación. Decidir si las líneas adicionales de un cuadro son realmente necesarias. Un ejemplo es la presentación de una ruta de acceso de directorio en una sección creada por una línea de grupo, tal como se muestra a continuación:  

![Información de texto estático en los controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Información de texto estático en los controles de texto

En un cuadro de diálogo donde existen otras áreas agrupadas y contención de la información ayudaría a mejorar la legibilidad, y cuando puede ocultar o se muestra una sección (como en el **ventana propiedades** panel Descripción) o desea que sean coherentes con la interfaz de usuario similar Coloque el texto estático dentro de un cuadro. Este cuadro de grupo debe ser una sola regla y coloreado con el `ButtonShadow`:

![Texto estático en la ventana propiedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático en la ventana Propiedades

### <a name="read-only-text-box"></a>Cuadro de texto de solo lectura

Esto permite al usuario seleccionar el texto dentro del campo, pero no editarlo. Estos cuadros de texto están rodeados por lo usual Cincel 3D con un `ButtonShadow` relleno.

Un cuadro de texto puede activarse (editable) cuando un usuario modifica un control asociado, como activar y desactivar una casilla o un botón de opción de seleccionar o deseleccionar. Por ejemplo, en el **herramientas &gt; opciones** página se muestra a continuación, el **página principal** cuadro de texto está activo cuando el **usar predeterminado** casilla de verificación está desactivada.

![Cuadro de texto de solo lectura, que muestra los Estados inactivos y activos](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Cuadro de texto de solo lectura, que muestra los Estados inactivos y activos

### <a name="using-text-in-dialogs"></a>Uso de texto en los cuadros de diálogo

Directrices clave de texto en cuadros de diálogo:

-   Las etiquetas de los cuadros de texto, cuadros de lista y los marcos en los cuadros de diálogo unthemed empiezan con un verbo, dispone de una mayúscula inicial en la primera palabra y terminan con un signo de dos puntos.

    > Los controles de texto en cuadros de diálogo con temas siguen [directrices de experiencia de usuario de escritorio de Windows](/windows/desktop/uxguide/top-violations) y no hacen que la puntuación final, a excepción de signos de interrogación en vínculos de ayuda.

-   Las etiquetas de las casillas y botones de opción empiezan con un verbo, una mayúscula inicial en la primera palabra únicamente y no tienen puntuación final.

-   Las etiquetas de los botones, menús, elementos de menú y las fichas tienen mayúsculas iniciales en todas las palabras (título).

-   Terminología de etiqueta debe ser coherente con las etiquetas similares en otros cuadros de diálogo.

-   Si es posible, debe tener un sistema de escritura/editor de escribir o aprobar el texto antes de enviarlos al desarrollador para la implementación.

-   Todos los controles deben tener etiquetas, excepto en circunstancias especiales en qué tabulación es suficiente.
Use texto de aplicación auxiliar cuando corresponda.

### <a name="helper-text"></a>Texto auxiliar

Se incluyen en los cuadros de diálogo para ayudar al usuario a comprender el propósito del cuadro de diálogo o para indicar qué acción realizar. Texto auxiliar debe usarse solo cuando sea necesario para no colapsar los cuadros de diálogo simple. Las variantes de texto auxiliares son cuadro de diálogo y marca de agua.

Siga las ubicaciones comunes para el texto de la aplicación auxiliar y sea selectivo con la introducción de nuevas áreas. Escenarios comunes para el texto de la aplicación auxiliar son:

-   Texto auxiliar en los cuadros de diálogo, para proporcionar una dirección adicional acerca de cómo interactuar con un cuadro de diálogo complejo.

-   Texto de marca de agua en las ventanas de herramientas vacía o cuadros de diálogo para explicar por qué no hay contenido está visible.

-   Un panel de descripción, al igual que en la parte inferior de la **ventana propiedades**.

-   Marca de agua texto en un editor vacío, explicar qué acción debe realizar el usuario para empezar a trabajar.
  
### <a name="dialog-helper-text"></a>Texto auxiliar del cuadro de diálogo

Un diseñador de la experiencia de usuario puede ayudar a determinar cuándo es apropiado el texto de la aplicación auxiliar. El diseñador puede definir donde aparece el texto de la aplicación auxiliar, así como su contenido general. Asistencia al usuario puede escribir o editar el texto real.

### <a name="watermarks"></a>Marcas de agua

Cuadros de diálogo de beneficiarán de las directrices de marca de agua ligeramente diferente. Dado que un cuadro de diálogo puede aparecer ocupado con muchos elementos de interfaz de usuario (etiquetas, texto de sugerencia, botones y otros controles de contenedor con texto), especialmente cuando los que aparecen en negro, las marcas de agua destaquen más en color gris oscuro (VSColor: `ButtonShadow`). Normalmente, aparece una marca de agua dentro de un control como un cuadro de lista con un fondo blanco (VSColor: `Window`).

-   El texto aparece en gris oscuro (VSColor: `ButtonShadow`). Sin embargo, si aparece la marca de agua en un gris medio o en otro color (VSColor: `ButtonFace`) en segundo plano y no hay se refieren a sobre su legibilidad, vaya con texto negro (VSColor: `WindowText`).

-   Las marcas de agua se centra o alineación a la izquierda. Aplicar reglas de diseño estándar al tomar decisiones de alineación. No se puede seleccionar la marca de agua en segundo plano.

![Ejemplo de texto de marca de agua](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Ejemplo de texto de marca de agua

### <a name="context-specific-dynamic-text"></a>Texto (dinámica) específicos del contexto

Texto dinámico puede ser utilizado de dos formas en un cuadro de diálogo o la interfaz de usuario no modal: como una etiqueta dinámica o como contenido dinámico.

-   Etiqueta dinámica: es un uso común de texto dinámico en paneles descriptivos que ofrecen más información para el elemento seleccionado, como un cuadro de diálogo que contiene una lista de elementos y propiedades para los elementos que se muestran en una cuadrícula a la derecha. La etiqueta de la cuadrícula de propiedades puede ser dinámica para que cuando se selecciona un elemento de la izquierda, la cuadrícula a la derecha muestra información de ese elemento específico.

-   Texto dinámico: puede ser útil en casos donde debe mostrar información específica y obtener información general de esta manera, pero debe tener cuidado para no abusar.

Si desea que los usuarios tengan la capacidad de copiar la información, debe ser texto dinámico en un campo de texto de solo lectura.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos  
  
### <a name="overview"></a>Información general  
Controles de botones y link (hipervínculos) deben seguir [instrucciones básicas de escritorio de Windows en los hipervínculos](/windows/desktop/uxguide/ctrl-links) para el uso de redacción, ajustar el tamaño y espaciado.  
  
### <a name="choosing-between-buttons-and-links"></a>Elegir entre los botones y vínculos  
Tradicionalmente, los botones se han usado para las acciones y los hipervínculos se han reservado para la navegación. Se pueden usar los botones en todos los casos, pero se ha ampliado el rol de vínculos en Visual Studio para que los botones y los vínculos son más intercambiables en ciertas condiciones.  
  
Cuándo utilizar los botones de comando:  
  
-   Principales comandos  
  
-   Mostrar ventanas que se usan para recopilar la entrada o tomar decisiones, incluso si son comandos secundarios  
  
-   Acciones destructivas o irreversibles  
  
-   Botones de compromiso dentro de los asistentes y flujos de página  
  
Evite los botones de comando de ventanas de herramientas, o si necesita más de dos palabras de la etiqueta. Vínculos pueden tener más etiquetas.  
  
 Cuando se usan los vínculos:  
  
-   Navegación a otra ventana, documento o página web  
  
-   Situaciones que requieran una etiqueta más tiempo o una frase corta para describir el propósito de la acción  
  
-   Espacios reducidos donde podría sobrecargar un botón de la interfaz de usuario, siempre que la acción no es destructivo o irreversible  
  
-   Deserialización realce comandos secundarios en situaciones donde hay muchos comandos  
  
#### <a name="examples"></a>Ejemplos  
![Vínculos que se usan en la barra de información que sigue a un mensaje de estado del comando](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Comando vínculos que se usan en la barra de información que sigue a un mensaje de estado
  
![Vínculos que se usan en el menú emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Vínculos que se usan en el menú emergente de CodeLens
  
![Vínculos que se usan para los comandos secundaria donde botones conllevaría demasiada atención](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Vínculos que se usan para los comandos secundaria donde botones conllevaría demasiada atención
  
### <a name="common-buttons"></a>Botones comunes  
  
#### <a name="text"></a>Texto  
Siga las instrucciones de escritura de [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
##### <a name="standard-unthemed"></a>Estándar (unthemed)  
La mayoría de los botones en Visual Studio aparecerán en los cuadros de diálogo de utilidad y no deben cambiar el estilo. Debe reflejar el aspecto de botones estándar dictado por el sistema operativo.  
  
##### <a name="themed"></a>Con temas  
En algunos casos, se pueden usar los botones dentro de la interfaz de usuario con estilo y deben cambiar el estilo adecuadamente estos botones. Consulte [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles con tema.  
  
### <a name="special-buttons"></a>Botones especiales  
  
#### <a name="browse-buttons"></a>Botones para examinar...  
**[Examinar...]**  botones se utilizan en las cuadrículas, cuadros de diálogo y las ventanas de herramientas y otros elementos de interfaz de usuario no modales. Muestra un selector que ayuda al usuario en rellenar un valor en un control. Hay dos variaciones de este botón, largo y corto.  
  
![El botón [Examinar...] largo](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />El botón [Examinar...] largo
  
![El botón corto con solo puntos suspensivos […]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />El botón corto con solo puntos suspensivos […]
  
Cuándo se debe usar el botón corto con solo puntos suspensivos:  
  
-   Si hay más de un largo **[Examinar...]**  botón en un cuadro de diálogo, como cuando se permiten varios campos para la exploración. Utilice el breve **[...]**  cada uno evitar las claves de acceso confuso creadas esta situación (**& Examinar** y **e & xaminar** en el mismo cuadro de diálogo).  
  
-   En un cuadro de diálogo estrecha, o cuando no hay ningún lugar razonable para colocar el botón de largo.  
  
-   Si el botón aparecerá en un control de cuadrícula.  
  
Directrices para usar el botón:  
  
-   No use una clave de acceso. Para acceder a ella mediante el teclado, el usuario debe tabulaciones desde el control adyacente. Asegúrese de que el orden de tabulación es tal que se encuentra ningún botón de examinar inmediatamente después del campo que va a rellenar. Nunca use un carácter de subrayado debajo del primer período.  
  
-   Establecer Microsoft Active Accessibility (MSAA) **nombre** propiedad **Examinar...**  (incluidos los puntos suspensivos) para que la pantalla se leerá, como "Examinar" y no "dot-punto" o "período período período." Esto implica la configuración de controles administrados, el **AccessibleName** propiedad.  
  
-   Nunca use un botón de puntos suspensivos **[...]**  botón salvo para una acción de exploración. Por ejemplo, si necesita un **[nuevo...]**  botón pero no tiene suficiente espacio para el texto, a continuación, debe volver a diseñar el cuadro de diálogo.  
  
##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado  
![Botones [Examinar...] de ajuste de tamaño: versión standard es 75 x 23 píxeles, versión corta es 26 x 23 píxeles](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Tamaño de los botones [Examinar...]
  
![Botones [Examinar...] de espaciado: espaciado entre control relacionado y píxeles de 7 de botón estándares de exploración, el espaciado entre el control relacionado y examinar corto botón 5 píxeles](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Espaciado de los botones [Examinar...]
  
#### <a name="graphical-buttons"></a>Botones gráficos  
Algunos de los botones deben utilizar siempre una imagen gráfica y nunca incluyen texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en otras listas que se puede ordenar y selectores de campo.  
  
> **Nota:** los usuarios tienen que tabulador para ir a estos botones (no hay ninguna clave de acceso), colóquelos en un orden significativo. Mapa del `name` propiedad del botón a la acción que se tarda para que los lectores de pantalla interpretan correctamente la acción del botón.  
  
| Función | Botón |  
| --- | --- |  
| Add | ![Botón "Agregar" gráfico](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Quitar | ![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Agregar todo | ![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Quitar todo | ![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Subir | ![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Bajar | ![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Eliminar | ![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y espaciado  
Cambiar el tamaño de botones gráficos es el mismo que para la versión abreviada de la **[Examinar...]**  botón (26 x 23 píxeles):  
  
![Apariencia de una imagen gráfica en el botón, con y sin color transparente](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Apariencia de una imagen gráfica en el botón, con y sin color transparente
  
### <a name="hyperlinks"></a>Hipervínculos  
Los hipervínculos son adecuados para las acciones basadas en la navegación, como abrir un tema de ayuda, cuadro de diálogo modal o el asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio notable y visible para la interfaz de usuario. En general, las acciones que se compromete a una acción (por ejemplo, guardar, Cancelar y eliminar) se comunican mejor mediante un botón.  
  
#### <a name="writing-style"></a>Estilo de escritura  
Siga el [orientación de escritorio de Windows para el texto de la interfaz de usuario](/windows/desktop/uxguide/text-ui). No use "Aprender más acerca de," "Saber más acerca de" o "Get help con este" frases. En su lugar, frase de texto del vínculo de ayuda en cuanto a la pregunta principal por el contenido de ayuda. Por ejemplo, "**cómo agregar un servidor en el Explorador de servidores?**"  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Siempre deben usar hipervínculos [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no se ha adaptado correctamente, parpadea en color rojo cuando está activo o se muestra un color diferente después de que se visita.  
  
-   No incluya un subrayado en el control sobre el estado situado a menos que el vínculo es un fragmento de frase dentro de una frase completa, como en una marca de agua.  
  
-   No deberían aparecen subrayados al mantener el mouse. En su lugar, los comentarios al usuario que el vínculo está activo son un cambio de color pequeñas y el cursor del vínculo apropiado.  
  
##  <a name="BKMK_TreeViews"></a> Vistas de árbol  
  
Vistas de árbol proporcionan una manera de organizar complejos se muestra en grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento dentro de una vista de árbol puede seleccionarse para proporcionar más acciones.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Estilo visual de la vista de árbol  
  
#### <a name="expanders"></a>Controles de expansión  
El diseño de botón de expansión utilizado por Windows y Visual Studio deben cumplir los controles de vista de árbol. Cada nodo utiliza un control expander para mostrar u ocultar los elementos subyacentes. Uso de un control expander proporciona una coherencia para los usuarios que pueden surgir vistas de árbol diferentes dentro de Windows y Visual Studio.  
  
![Correcto: estilo correspondiente del nodo de vista de árbol mediante un control expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Correcto: estilo correspondiente del nodo de vista de árbol mediante un control expander
  
![Incorrecta: estilo incorrecto del nodo de la vista de árbol](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Incorrecta: estilo incorrecto del nodo de la vista de árbol
  
#### <a name="selection"></a>Selección  
Cuando se selecciona un nodo dentro de la vista de árbol, debe expandir el resaltado para todo el ancho del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Colores de selección deben reflejar el tema actual de Visual Studio.  
  
![Correcto: resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Correcto: resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.
  
![Incorrecta: el resaltado del nodo seleccionado no cabe todo el ancho del control de vista de árbol. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Incorrecta: el resaltado del nodo seleccionado no cabe todo el ancho del control de vista de árbol.
  
#### <a name="icons"></a>Iconos  
Si ayudar a identificar visualmente las diferencias entre los elementos de iconos solo deben usarse en controles de vista de árbol. En general, los iconos deben usarse solo en listas heterogéneas en el que los iconos de llevan información para diferenciar los tipos de elementos. En una lista homogénea mediante iconos, con frecuencia pueden considerarse como ruido y debe evitarse. En ese caso, el icono de grupo (principal) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se utiliza para indicar el estado.  
  
#### <a name="scroll-bars"></a>Barras de desplazamiento  
Siempre deben estar oculta las barras de desplazamiento si el contenido se ajusta dentro del control de vista de árbol. Es aceptable para las barras de desplazamiento se oculta o semitransparente en una ventana desplazable y aparecen cuando la ventana que contiene la vista de árbol tiene el foco, o después al mantener el mouse del árbol ver propio.  
  
![Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol.
  
###  <a name="BKMK_TreeViewInteractions"></a> Interacciones de la vista de árbol  
  
#### <a name="context-menus"></a>Menús contextuales  
Un nodo de vista de árbol puede mostrar las opciones de submenú en un menú contextual. Normalmente, esto se produce cuando un usuario ha hecho un elemento o presionó la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo recibe el foco y está seleccionado. Esto ayuda al usuario a identificar qué elemento al que pertenece el submenú.  
  
![El elemento que se generan el foco de ganancias del menú contextual para notificar al usuario qué elemento se ha seleccionado. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />El elemento que se generan el foco de ganancias del menú contextual para notificar al usuario qué elemento se ha seleccionado.
  
#### <a name="keyboard"></a>Teclado  
La vista de árbol debe proporcionar la capacidad de expandir y contraer los nodos mediante el teclado y seleccionar elementos. Esto garantiza que navegación cumple con nuestros requisitos de accesibilidad.  
  
##### <a name="tree-view-control"></a>Control de vista de árbol  
Controles de árbol Visual Studio deben seguir la navegación de teclado comunes:  
  
-   **Flecha arriba:** seleccionar elementos moviendo el árbol  
  
-   **Flecha abajo:** seleccionar bajando el árbol de elementos  
  
-   **Flecha derecha:** expandir un nodo en el árbol  
  
-   **Flecha izquierda:** contraer un nodo en el árbol  
  
-   **Escriba la clave:** iniciar, cargar, ejecutar el elemento seleccionado  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)  
Un control de trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar por el árbol deben respetar los mismos comandos de teclado que una vista de árbol, con las siguientes adiciones:  
  
-   **Flecha derecha:** expandir un nodo. Después de que el nodo está expandido, debe continuar navegar a la columna más cercana a la derecha. Exploración debe detenerse al final de la fila.  
  
-   **Ficha:** va a la celda más cercana a la derecha.  Al final de la fila, navegación sigue a la siguiente fila.  
  
-   **Mayús + Tab:** va a la celda más cercana a la izquierda.  Al principio de la fila, navegación sigue a la celda situada en la fila anterior.  
  
![Un control de trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Un control de trid en Visual Studio