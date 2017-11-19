---
title: Patrones de Control comunes para Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e06a3e89b69b2b69a97c4deb2d68d98913f6e03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Patrones de Control comunes para Visual Studio
##  <a name="BKMK_CommonControls"></a>Controles comunes  
  
### <a name="overview"></a>Información general  
Controles comunes constituyen la mayor parte de la interfaz de usuario en Visual Studio. Los controles más comunes usados en la interfaz de Visual Studio deben seguir la [directrices de la interacción de escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este tema es específico de Visual Studio y trata situaciones especiales o los detalles que aumentan esas directrices de Windows.  
  
#### <a name="common-controls-in-this-topic"></a>Controles comunes de este tema  
  
-   [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Casillas de verificación](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Marcos de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Estilo Visual  
Lo primero que debe considerar al aplicar estilos a controles es si se usará los controles de interfaz de usuario con temas. Controles de interfaz de usuario estándar son la interfaz de usuario no con temas y debe seguir [estilo normal de escritorio de Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), lo que significa que no tienen re plantillas y debe aparecer en su apariencia de los controles de forma predeterminada.  
  
-   **Los cuadros de diálogo estándar (utilidad):** no con temas. No re de plantilla. Usar valores predeterminados de estilo de control básico.  
  
-   **Ventanas de herramientas, editores de documento, superficies de diseño y los cuadros de diálogo con temas:** usar apariencia con temas especializado mediante el servicio de color.  
  
###  <a name="BKMK_Scrollbars"></a>Barras de desplazamiento  
 Barras de desplazamiento deben seguir [barras de desplazamiento de los patrones de interacción común para Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) a menos que está ampliadas con información de contenido, al igual que en el editor de código.  
  
###  <a name="BKMK_InputFields"></a>Campos de entrada  
 Para el comportamiento de interacción típica, siga el [directrices de escritorio de Windows para los cuadros de texto](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Campos de entrada no deben ser un estilo en los cuadros de diálogo de utilidad. Usar el estilo básico intrínseco al control.  
  
-   Campos de entrada con temas solo deben usarse en los cuadros de diálogo con temas y las ventanas de herramientas.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
  
-   Campos de solo lectura tendrá un fondo gris (deshabilitado) pero (active) predeterminado de primer plano.  
  
-   Requiere los campos deben tener  **\<necesario >** como marcas de agua dentro de ellos. No debe cambiar el color de fondo excepto en las situaciones excepcionales.  
  
-   Validación del error: consulte [notificaciones y el progreso de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Deben ajustar el tamaño de los campos de entrada para adaptarlos al contenido, no para ajustarse al ancho de la ventana en la que se muestran ni arbitrariamente coincide con la longitud de un campo largo, como una ruta de acceso. Longitud podría ser una indicación al usuario de limitaciones en cuanto a cuántos caracteres se permiten en el campo.  
  
     ![Longitud de campo de entrada incorrecto: no es probable que el nombre será este tiempo. ] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Longitud de campo de entrada incorrecto: no es probable que el nombre será este tiempo.
  
     ![Corregir la longitud de campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado. ] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Corregir la longitud de campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Cuadros combinados y listas desplegables  
Para el comportamiento de interacción típica, siga el [directrices de escritorio de Windows para listas desplegables y cuadros combinados](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   En los cuadros de diálogo de utilidad, no re plantilla del control. Usar el estilo básico intrínseco al control.  
  
-   En la interfaz de usuario con temas, cuadros combinados y listas desplegables siguen los temas para los controles estándar.  
  
#### <a name="layout"></a>Diseño  
Cuadros combinados y listas desplegables deben ajustarse para adaptarlos al contenido, no para ajustarse al ancho de la ventana en la que se muestran ni arbitrariamente coincide con la longitud de un campo largo, como una ruta de acceso.  
  
![Correcto: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará. ] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Correcto: el ancho de la lista desplegable es demasiado largo para el contenido que se mostrará.
  
![Correcto: la lista desplegable cambiará de tamaño para permitir el crecimiento de traducción, pero no innecesariamente largas. ] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Correcto: la lista desplegable cambiará de tamaño para permitir el crecimiento de traducción, pero no innecesariamente largas. 
  
###  <a name="BKMK_CheckBoxes"></a>Casillas de verificación  
Para el comportamiento de interacción típica, siga el [directrices de escritorio de Windows para casillas de verificación](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   En los cuadros de diálogo de utilidad, no re plantilla del control. Usar el estilo básico intrínseco al control.  
  
-   En la interfaz de usuario con temas, casillas de verificación siga los temas para los controles estándar.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
  
-   Interacción con una casilla de verificación nunca debe aparecer un cuadro de diálogo o navegar a otra área.  
  
-   Alinear las casillas de verificación con la línea de base de la primera línea de texto.  
  
     ![Incorrecto: la casilla de verificación se centra en el texto. ] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Incorrecto: la casilla de verificación se centra en el texto.
  
     ![Correcto: la casilla de verificación se alinea con la primera línea del texto. ] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Correcto: la casilla de verificación se alinea con la primera línea del texto.
  
###  <a name="BKMK_RadioButtons"></a>Botones de radio  
Para el comportamiento de interacción típica, siga el [directrices de escritorio de Windows de botones de opción](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
En los cuadros de diálogo de utilidad, haga lo no los botones de opción de estilo. Usar el estilo básico intrínseco al control.  
  
#### <a name="specialized-interactions"></a>Interacciones especializadas  
No es necesario utilizar un marco de grupo para incluir las opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño de una estrecha.  
  
###  <a name="BKMK_GroupFrames"></a>Marcos de grupo  
Para el comportamiento de interacción típica, siga el [directrices de escritorio de Windows para los marcos de grupo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Estilo Visual  
En los cuadros de diálogo de utilidad, no aplicar estilo a marcos de grupo. Usar el estilo básico intrínseco al control.  
  
#### <a name="layout"></a>Diseño  
  
-   No es necesario utilizar un marco de grupo para incluir las opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño de una estrecha.  
  
-   Nunca utilice un marco de grupo para un control único.  
  
-   A veces es aceptable utilizar una regla horizontal en lugar de un contenedor de marco de grupo.  
  
##  <a name="BKMK_TextControls"></a>Controles de texto

### <a name="static-text-fields"></a>Campos de texto estático

Un campo de texto estático presenta información de solo lectura y no se puede seleccionar por el usuario. Evite el uso de cualquier texto que el usuario desee copiar en el Portapapeles. Sin embargo, puede cambiar el texto estático de solo lectura para reflejar un cambio de estado. En el ejemplo siguiente, el texto estático de nombre de salida en los cambios del grupo de información para reflejar los cambios realizados en el cuadro de texto raíz Namespace por encima de él.

Hay dos formas para mostrar información de texto estático.

Puede ser texto estático en su propia en un cuadro de diálogo sin cualquier contención cuando no haya ningún conflicto de agrupación. Decidir si las líneas adicionales de un cuadro son realmente necesarias. Un ejemplo es la presentación de una ruta de acceso de directorio en una sección creada por una línea de grupo, tal y como se muestra a continuación:  

![Información de texto estático en los controles de texto](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Información de texto estático en los controles de texto

En un cuadro de diálogo donde existen otras áreas agrupadas y contención de la información contribuye a mejorar la legibilidad, y cuándo se puede ocultar o se muestra una sección (como en el **ventana propiedades** panel de descripción) o desea ser coherente con la interfaz de usuario similar, Coloque el texto estático dentro de un cuadro. Este cuadro de grupo debe ser una sola regla y coloreadas con el `ButtonShadow`:

![Texto estático en la ventana propiedades](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texto estático en la ventana Propiedades

### <a name="read-only-text-box"></a>Cuadro de texto de solo lectura

Esto permite al usuario seleccionar el texto dentro del campo, pero no editarlo. Estos cuadros de texto están rodeados por el habitual Cincel 3D con un `ButtonShadow` relleno.

Un cuadro de texto puede activarse (editable) cuando un usuario modifica un control asociado, como activando/desactivando una casilla de verificación o un botón de opción de seleccionar o deseleccionar. Por ejemplo, en la **herramientas &gt; opciones** página se muestra a continuación, el **página principal** cuadro de texto se convierte en activa cuando la **usar predeterminada** casilla de verificación está desactivada.

![Cuadro de texto de solo lectura, que muestra los Estados inactivos y activos](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Cuadro de texto de solo lectura, que muestra los Estados inactivos y activos

### <a name="using-text-in-dialogs"></a>Uso de texto en los cuadros de diálogo

Instrucciones clave para el texto en los cuadros de diálogo:

-   Las etiquetas de los cuadros de texto, cuadros de lista y marcos en los cuadros de diálogo unthemed empiezan con un verbo, tienen una inversión inicial en la primera palabra y terminan con un signo de dos puntos.

    > Controles de texto en los cuadros de diálogo con temas siguen [instrucciones UX de escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) y no toma puntuación final, con la excepción de los signos de interrogación en vínculos de ayuda.

-   Las etiquetas de las casillas de verificación y botones de opción empiezan con un verbo, inicial en mayúsculas en la primera palabra y no tienen puntuación final.

-   Las etiquetas de los botones, menús, elementos de menú y pestañas tienen mayúsculas iniciales en cada palabra (título).

-   Terminología de etiqueta debe ser coherente con etiquetas similares en otros cuadros de diálogo.

-   Si es posible, debe tener un sistema de escritura/editor de escribir o aprobar el texto antes de enviarlos al desarrollador de la implementación.

-   Todos los controles deben tener las etiquetas excepto en circunstancias especiales en qué tabulación es suficiente.
Usar texto de aplicación auxiliar cuando corresponda.

### <a name="helper-text"></a>Texto auxiliar

Se incluyen en los cuadros de diálogo para ayudar al usuario a comprender el propósito del cuadro de diálogo o para indicar qué acción se debe realizar. Texto auxiliar debe usarse solo cuando sea necesario para no colapsar los cuadros de diálogo simples. Variantes de texto auxiliar son el cuadro de diálogo y marca de agua.

Siga las ubicaciones comunes para el texto de la aplicación auxiliar y sea selectivo con la introducción de nuevas áreas. Escenarios comunes para el texto de la aplicación auxiliar son:

-   Texto de ayuda en cuadros de diálogo, asigne una dirección adicional acerca de cómo interactuar con un cuadro de diálogo complejo.

-   Texto de marca de agua en las ventanas de herramientas vacía o en los cuadros de diálogo para explicar por qué no hay contenido está visible.

-   Un panel de descripción, al igual que en la parte inferior de la **ventana propiedades**.

-   Límite del texto en un editor vacío, para explicar qué medidas debe tomar el usuario para empezar a trabajar.
  
### <a name="dialog-helper-text"></a>Texto auxiliar del cuadro de diálogo

Un diseñador de la experiencia de usuario puede ayudar a determinar cuándo es apropiado el texto de la aplicación auxiliar. El diseñador puede definir dónde aparece el texto de la aplicación auxiliar, así como su contenido general. Asistencia al usuario puede escribir o editar el texto real.

### <a name="watermarks"></a>Marcas de agua

Los cuadros de diálogo beneficiarán de las directrices de marca de agua ligeramente diferente. Dado que un cuadro de diálogo puede aparecer ocupado con muchos elementos de interfaz de usuario (las etiquetas, texto de la sugerencia, botones y otros controles de contenedor con texto), especialmente cuando los que aparecen en negro, marcas de agua se resaltan mejor en color gris oscuro (VSColor: `ButtonShadow`). Aparece una marca de agua normalmente dentro de un control como un cuadro de lista con un fondo blanco (VSColor: `Window`).

-   El texto aparece en gris oscuro (VSColor: `ButtonShadow`). Sin embargo, si aparece la marca de agua en un gris medio o en otros colores (VSColor: `ButtonFace`) en segundo plano y no hay conciernen sobre su legibilidad, vaya con texto negro (VSColor: `WindowText`).

-   Marcas de agua se centra o alineación a la izquierda. Al tomar decisiones de alineación se aplican las reglas de diseño estándar. No se puede seleccionar la marca de agua en el fondo.

![Ejemplo de texto de marca de agua](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Ejemplo de texto de marca de agua

### <a name="context-specific-dynamic-text"></a>Texto de específicas del contexto (dinámico)

Texto dinámico puede ser utilizan una de estas dos formas en un cuadro de diálogo o la interfaz de usuario no modal: como una etiqueta dinámica o como contenido dinámico.

-   Etiqueta dinámica: es un uso común de texto dinámico en paneles descriptivos que ofrecen más información para el elemento seleccionado, como en un cuadro de diálogo que contiene una lista de elementos y las propiedades de los elementos que se muestran en una cuadrícula a la derecha. La etiqueta de la cuadrícula de propiedades puede ser dinámica para que cuando se selecciona un elemento de la izquierda, la cuadrícula a la derecha muestra información para ese elemento específico.

-   Texto dinámico: puede ser útil en casos donde se necesitan para mostrar información específica y la información general de esta manera, pero debe tener cuidado para no un uso excesivo.

Si desea que los usuarios tengan la capacidad de copiar la información, debe ser texto dinámico en un campo de texto de solo lectura.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>Botones e hipervínculos  
  
### <a name="overview"></a>Información general  
Controles de botones y link (hipervínculos) deben seguir [guía básica de escritorio de Windows en hipervínculos](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) para el uso, nombres, ajustar el tamaño y espaciado.  
  
### <a name="choosing-between-buttons-and-links"></a>Elegir entre los botones y vínculos  
Tradicionalmente, botones que se usaron para las acciones y los hipervínculos se han reservado para la navegación. Botones pueden utilizarse en todos los casos, pero se ha ampliado el rol de vínculos en Visual Studio para que sean más intercambiables en algunas condiciones de botones y vínculos.  
  
Cuándo se debe utilizar botones de comando:  
  
-   Comandos principales  
  
-   Mostrar ventanas que se usan para recopilar la entrada o tomar decisiones, incluso si son comandos secundarios  
  
-   Acciones destructivas o irreversible.  
  
-   Botones de compromiso en asistentes y flujos de página  
  
Evite los botones de comando de ventanas de herramientas, o si necesita más de dos o más palabras de la etiqueta. Vínculos pueden tener las etiquetas más largas.  
  
 Cuando se usan los vínculos:  
  
-   Navegación a otra ventana, documento o página web  
  
-   Situaciones que requieren una etiqueta más larga o frase corta para describir el propósito de la acción  
  
-   Espacios reducidos donde un botón podría saturar la interfaz de usuario, siempre que la acción no es destructiva o irreversible.  
  
-   Eliminación realce comandos secundarios en situaciones donde hay muchos comandos  
  
#### <a name="examples"></a>Ejemplos  
![Vínculos que se usan en la barra de información que sigue a un mensaje de estado del comando](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Comando vínculos que se usan en la barra de información que sigue a un mensaje de estado
  
![Vínculos que se usan en la ventana emergente de CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Vínculos que se usan en el menú emergente de CodeLens
  
![Vínculos que se usan para los comandos secundarias donde botones conllevaría demasiada atención](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Vínculos que se usan para los comandos secundarias donde botones conllevaría demasiada atención
  
### <a name="common-buttons"></a>Botones comunes  
  
#### <a name="text"></a>Texto  
Siga las instrucciones de escritura de [UI texto y la terminología](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Estilo Visual  
  
##### <a name="standard-unthemed"></a>Estándar (unthemed)  
Mayoría de los botones en Visual Studio se mostrará en los cuadros de diálogo de utilidad y no debe ser un estilo. Debe reflejar la apariencia de los botones estándar según lo dictado por el sistema operativo.  
  
##### <a name="themed"></a>Con temas  
En algunos casos, pueden usarse los botones dentro de la interfaz de usuario con estilo y estos botones deben ser un estilo adecuadamente. Vea [cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles con temas.  
  
### <a name="special-buttons"></a>Botones especiales  
  
#### <a name="browse-buttons"></a>Botones de navegación por...  
**[Examinar...]**  botones se utilizan en las cuadrículas, cuadros de diálogo y las ventanas de herramientas y otros elementos de interfaz de usuario no modales. Muestra un selector que ayuda al usuario a rellenar un valor en un control. Hay dos variaciones de este botón, larga y corta.  
  
![El botón [Examinar...] largo](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />El botón [Examinar...] largo
  
![El botón corto con solo puntos suspensivos […]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />El botón corto con solo puntos suspensivos […]
  
Cuándo se debe usar el botón corto con solo puntos suspensivos:  
  
-   Si hay más de una larga **[Examinar...]**  botón en un cuadro de diálogo, como cuando se permiten varios campos para examinar. Usar corto **[...]**  botón para cada uno de ellos evitar que las claves de acceso confuso creadas por esta situación (**& Examinar** y **B & r** en el mismo cuadro de diálogo).  
  
-   En un cuadro de diálogo estrecha, o cuando no hay ningún lugar razonable para colocar el botón de largo.  
  
-   Si el botón aparecerá en un control de cuadrícula.  
  
Directrices para usar el botón:  
  
-   No use una clave de acceso. Para acceder a ella mediante el teclado, el usuario debe tabulador desde el control adyacente. Asegúrese de que el orden de tabulación es tal que cualquier botón Examinar que se encuentra inmediatamente después del campo que va a rellenar. Nunca use un subrayado debajo del primer período.  
  
-   Establecer Microsoft Active Accessibility (MSAA) **nombre** propiedad **Examinar...**  (incluidos los puntos suspensivos) para que la pantalla se leerá, como "Buscar" y no "punto-guión-punto-" o "período período período." Esto implica la configuración de controles administrados, el **AccessibleName** propiedad.  
  
-   Nunca utilice puntos suspensivos **[...]**  botón para todo excepto una acción de exploración. Por ejemplo, si necesita un **[nuevo...]**  botón pero no tiene suficiente espacio para el texto, debe volver a diseñar el cuadro de diálogo.  
  
##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y el espaciado  
![Botones [Examinar...] de ajuste de tamaño: versión estándar es 75 x 23 píxeles, versión abreviada es píxeles de 26 x 23](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Tamaño de los botones [Examinar...]
  
![Botones [Examinar...] de espaciado: espaciado entre control relacionado y píxeles de botón 7 examinar estándares, espaciado entre control relacionado y examinar corto botón 5 píxeles](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Espaciado de los botones [Examinar...]
  
#### <a name="graphical-buttons"></a>Botones gráficos  
Algunos botones deben siempre utilizar una imagen gráfica y no incluya nunca texto para ahorrar espacio y evitar problemas de localización. A menudo se utilizan en otras listas que se puede ordenar y selectores de campo.  
  
> **Nota:** los usuarios tengan que tabulador para ir a estos botones (no hay ninguna clave de acceso), por lo que los coloque en un orden significativo. Mapa del `name` propiedad del botón en la acción que realiza para que los lectores de pantalla interpretan correctamente la acción del botón.  
  
| Función | Botón |  
| --- | --- |  
| Add | ![Botón gráfico de "Agregar"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| Quitar | ![Botón gráfico "Quitar"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Agregar todo | ![Botón gráfico "Agregar todo"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Quitar todos los | ![Botón gráfico "Quitar todo"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Subir | ![Botón gráfico "Subir"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Bajar | ![Botón gráfico "Bajar"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Eliminar | ![Botón gráfico "Eliminar"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Ajuste de tamaño y el espaciado  
Ajustar el tamaño de botones gráficos es el mismo que para la versión abreviada de la **[Examinar...]**  botón (26 x 23 píxeles):  
  
![Impresión de una imagen gráfica en el botón, con y sin color transparente](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Impresión de una imagen gráfica en el botón, con y sin color transparente
  
### <a name="hyperlinks"></a>Hipervínculos  
Los hipervínculos se adaptan perfectamente a acciones de navegación, como abrir un tema de ayuda, el cuadro de diálogo modal o el asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio notable y visible para la interfaz de usuario. En general, las acciones que se compromete a una acción (como guardar, Cancelar y eliminar) se comunican mejor con un botón.  
  
#### <a name="writing-style"></a>Estilo de escritura  
Siga el [instrucciones de escritorio de Windows para el texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). No utilice "Aprender más acerca de," "Saber más acerca de" o "Obtener ayuda con este" frases. En su lugar, frase de texto de vínculo de ayuda en cuanto a la pregunta principal respondida por el contenido de ayuda. Por ejemplo, "**cómo agregar un servidor en el Explorador de servidores?**"  
  
#### <a name="visual-style"></a>Estilo Visual  
  
-   Siempre deben utilizar hipervínculos [el servicio de VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hipervínculo no se ha adaptado correctamente, parpadeará en rojo cuando están activas o muestra un color diferente después de que se está visitando.  
  
-   No incluya un subrayado en el control deja el estado a menos que el vínculo es un fragmento de frase dentro de una frase completa, al igual que en una marca de agua.  
  
-   Un subrayado no debe aparecer al mantener el mouse. En su lugar, los comentarios al usuario que el vínculo está activo son un cambio de color ligeras y el cursor de vínculo adecuado.  
  
##  <a name="BKMK_TreeViews"></a>Vistas de árbol  
  
Vistas de árbol proporcionan una manera de organizar complejos se enumera en grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento dentro de una vista de árbol puede seleccionarse para proporcionar más acciones.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Estilo visual de la vista de árbol  
  
#### <a name="expanders"></a>Controles de expansión  
Controles de vista de árbol deben cumplir el diseño de botón de expansión utilizado por Windows y Visual Studio. Cada nodo utiliza un control de botón de expansión para mostrar u ocultar los elementos subyacentes. Usar un control de botón de expansión, proporciona una coherencia para los usuarios que pueden surgir vistas de árbol diferentes dentro de Windows y Visual Studio.  
  
![Correcto: estilo correspondiente del nodo de vista de árbol con un control de botón de expansión](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Correcto: estilo correspondiente del nodo de vista de árbol con un control de botón de expansión
  
![Incorrecta: estilo incorrecto del nodo de la vista de árbol](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Incorrecta: estilo incorrecto del nodo de la vista de árbol
  
#### <a name="selection"></a>Selección  
Cuando se selecciona un nodo dentro de la vista de árbol, debe expandir el resaltado para todo el ancho del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Colores de selección deben reflejar el tema actual de Visual Studio.  
  
![Correcto: resaltado del nodo seleccionado se adapta a todo el ancho del control de vista de árbol. ] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Correcto: resaltado del nodo seleccionado se adapta a todo el ancho del control de vista de árbol.
  
![Incorrecta: resaltado del nodo seleccionado no ajusta todo el ancho del control de vista de árbol. ] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Incorrecta: resaltado del nodo seleccionado no ajusta todo el ancho del control de vista de árbol.
  
#### <a name="icons"></a>Iconos  
Iconos sólo deben usarse en los controles de vista de árbol si sirven de ayuda para identificar visualmente las diferencias entre los elementos. En general, los iconos deben usarse solo en las listas heterogéneas en los que los iconos proporcionan información para diferenciar los tipos de elementos. En una lista homogénea con iconos, con frecuencia se puede considerar como ruido y debe evitarse. En ese caso, el icono de grupo (primario) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se usa para indicar el estado.  
  
#### <a name="scroll-bars"></a>Barras de desplazamiento  
Barras de desplazamiento siempre deben estar oculta si el contenido se ajusta dentro del control de vista de árbol. Es aceptable para las barras de desplazamiento estar ocultas o semitransparentes en una ventana desplazable y aparecen cuando la ventana que contiene la vista de árbol tiene el foco o al mantener el mouse del árbol ver propio.  
  
![Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol. ] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Se muestran las barras de desplazamiento vertical y horizontal porque el contenido ha superado los límites del control de vista de árbol.
  
###  <a name="BKMK_TreeViewInteractions"></a>Interacciones de vista de árbol  
  
#### <a name="context-menus"></a>Menús contextuales  
Un nodo de vista de árbol puede mostrar opciones de submenú en un menú contextual. Normalmente, esto se produce cuando un usuario tiene un elemento con el botón secundario o se presiona la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo recibe el foco y se selecciona. Esto ayuda al usuario a identificar qué elemento al que pertenece el submenú.  
  
![El elemento que se generan el foco de mejoras en el menú contextual para notificar al usuario qué elemento se ha seleccionado. ] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />El elemento que se generan el foco de mejoras en el menú contextual para notificar al usuario qué elemento se ha seleccionado.
  
#### <a name="keyboard"></a>Teclado  
La vista de árbol debe proporcionar la capacidad de seleccionar los elementos y expandir o contraer nodos mediante el teclado. Esto garantiza que la navegación cumple los requisitos de accesibilidad.  
  
##### <a name="tree-view-control"></a>Control de vista de árbol  
Controles de árbol de Visual Studio deben seguir la navegación mediante el teclado comunes:  
  
-   **Flecha arriba:** seleccionar elementos moviendo el árbol  
  
-   **Flecha hacia abajo:** bajando el árbol para seleccionar elementos  
  
-   **Flecha derecha:** expandir un nodo en el árbol  
  
-   **Flecha izquierda:** contraer un nodo en el árbol  
  
-   **Escriba la clave:** iniciar, cargar, ejecutar el elemento seleccionado  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (vista de árbol y vista de cuadrícula)  
Un control de trid es un control complejo que contiene una vista de árbol en una cuadrícula. Expandir, contraer y navegar por el árbol deben respetar los mismos comandos de teclado como una vista de árbol, con las siguientes adiciones:  
  
-   **Flecha derecha:** expandir un nodo. Después de expandirse el nodo, debe continuar navegando a la columna más cercana a la derecha. Debe detener la navegación al final de la fila.  
  
-   **Pestaña:** va a la celda más cercana a la derecha.  Al final de la fila, navegación continúa a la siguiente fila.  
  
-   **MAYÚS + Tabulador:** va a la celda más cercana a la izquierda.  Al principio de la fila, navegación continúa a la celda situada en la fila anterior.  
  
![Un control de trid en Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Un control de trid en Visual Studio