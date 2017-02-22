---
title: "Patrones de Control comunes para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Patrones de Control comunes para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Controles comunes  
  
### Información general  
 Controles comunes constituyen la mayor parte de la interfaz de usuario en Visual Studio. Los controles más comunes utilizados en la interfaz de Visual Studio deben seguir la [directrices de la interacción de escritorio de Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Este documento es específico de Visual Studio y trata situaciones especiales o detalles que aumentan las directrices de Windows.  
  
#### Controles comunes de este tema  
  
-   [Barras de desplazamiento](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Campos de entrada](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Cuadros combinados y listas desplegables](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Casillas de verificación](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Botones de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Marcos de grupo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Botones e hipervínculos](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Vistas de árbol](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### Estilo Visual  
 Lo primero que hay tener en cuenta al aplicar estilos a controles es si los controles se utilizará en la interfaz de usuario con temas. Controles de interfaz de usuario estándar son no temáticas de interfaz de usuario y debe seguir [estilo normal de escritorio de Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), lo que significa que no están re plantilla y debe aparecer en su aspecto de control predeterminado.  
  
-   **Los cuadros de diálogo estándar \(utilidad\):** no con temas. Hacer no re\-plantilla. Usar valores predeterminados de estilo de control básico.  
  
-   **Ventanas de herramientas, editores de documentos, superficies de diseño y los cuadros de diálogo con temas:** usar especializada Apariencia temática mediante el servicio de color.  
  
###  <a name="BKMK_Scrollbars"></a> Barras de desplazamiento  
 Deben seguir las barras de desplazamiento [patrones comunes de interacción para las barras de desplazamiento de Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) a menos que se manejan con información sobre el contenido, como en el editor de código.  
  
###  <a name="BKMK_InputFields"></a> Campos de entrada  
 Para el comportamiento de interacción típica, siga la [directrices de escritorio de Windows para los cuadros de texto](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### Estilo Visual  
  
-   Campos de entrada no deben aplicarles estilo en los cuadros de diálogo de la utilidad. Utilice el estilo básico intrínseco al control.  
  
-   Campos de entrada con temas sólo deben utilizarse en los cuadros de diálogo con temas y ventanas de herramientas.  
  
#### Interacciones especializadas  
  
-   Campos de solo lectura tendrá un fondo gris \(deshabilitado\) pero \(active\) predeterminado de primer plano.  
  
-   Requiere los campos deben tener **\< necesario \>** como marcas de agua dentro de ellos. No debe cambiar el color de fondo excepto en situaciones excepcionales.  
  
-   Validación de error: vea [Las notificaciones y el progreso de Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Campos de entrada deben ajustarse para adaptarlos al contenido, no para ajustarse al ancho de la ventana en la que se muestran ni arbitrariamente coincida con la longitud de un campo largo, como una ruta de acceso. Longitud podría ser una indicación al usuario de limitaciones en cuanto a cuántos caracteres se permiten en el campo.  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **Longitud de campo de entrada incorrecto: no es probable que el nombre será así de largos.**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **Corregir la longitud del campo de entrada: el campo de entrada es un ancho razonable para el contenido esperado.**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Cuadros combinados y listas desplegables  
 Para el comportamiento de interacción típica, siga la [directrices de escritorio de Windows para las listas desplegables y cuadros combinados](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### Estilo Visual  
  
-   En los cuadros de diálogo de utilidad hacer no re\-plantilla del control. Utilice el estilo básico intrínseco al control.  
  
-   En los temas de interfaz de usuario, cuadros combinados y listas desplegables siga los temas de los controles estándar.  
  
#### Diseño  
 Cuadros combinados y listas desplegables deben ajustarse para adaptarlos al contenido, no para ajustarse al ancho de la ventana en la que se muestran ni arbitrariamente coincida con la longitud de un campo largo, como una ruta de acceso.  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **Longitud de campo incorrecta para un control de lista desplegable**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **Longitud de campo correcto para un control de lista desplegable**  
  
###  <a name="BKMK_CheckBoxes"></a> Casillas de verificación  
 Para el comportamiento de interacción típica, siga la [directrices de escritorio de Windows para las casillas](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### Estilo Visual  
  
-   En los cuadros de diálogo de utilidad hacer no re\-plantilla del control. Utilice el estilo básico intrínseco al control.  
  
-   Interfaz de usuario con temas, casillas de verificación siga los temas de los controles estándar.  
  
#### Interacciones especializadas  
  
-   Interacción con una casilla de verificación nunca debe aparecer un cuadro de diálogo o navegar a otra área.  
  
-   Alinear las casillas de verificación con la línea de base de la primera línea de texto.  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **Alineación de la casilla de verificación incorrecta: casilla de verificación se centra en el texto.**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **Alineación de la casilla de verificación de corregir: casilla de verificación está alineada con la línea de base de la primera línea de texto.**  
  
###  <a name="BKMK_RadioButtons"></a> Botones de radio  
 Para el comportamiento de interacción típica, siga la [directrices de escritorio de Windows para los botones de radio](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### Estilo Visual  
 En los cuadros de diálogo de utilidad hacer no los botones de opción de estilo. Utilice el estilo básico intrínseco al control.  
  
#### Interacciones especializadas  
 No es necesario utilizar un marco de grupo para incluir opciones de radio.  
  
###  <a name="BKMK_GroupFrames"></a> Marcos de grupo  
 Para el comportamiento de interacción típica, siga la [directrices de escritorio de Windows para los marcos de grupo](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### Estilo Visual  
 En los cuadros de diálogo de utilidad hacer no marcos de grupo de estilo. Utilice el estilo básico intrínseco al control.  
  
#### Diseño  
  
-   No es necesario utilizar un marco de grupo para incluir opciones de radio, a menos que necesite mantener la distinción de grupo en un diseño estrecha.  
  
-   Nunca use un marco de grupo para un único control.  
  
-   A veces es aceptable usar una regla horizontal en lugar de un contenedor de marco de grupo.  
  
##  <a name="BKMK_TextControls"></a> Controles de texto  
  
### Etiquetas  
  
#### Estado de la etiqueta de activo  
  
##### Utilidad de cuadros de diálogo \(estándar\)\)  
  
-   En general, siga las instrucciones de escritorio de Windows para las etiquetas de control.  
  
-   En cuadros de diálogo de utilidad, las etiquetas deben aparecer sin negrita, en el color de fuente y texto de entorno estándar. Vea [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Puntos suspensivos siempre deben seguir las etiquetas.  
  
##### Firma \(temáticas de\) los cuadros de diálogo\)  
 Controles de etiqueta pueden ser negrita o gris claro.  
  
#### Estado de la etiqueta no disponible  
 Las etiquetas deben reflejar la apariencia del control que están asociados. Por ejemplo, si se deshabilita el control asociado, la etiqueta debe aparecer gris y deshabilitadas. Esto se suele tratar con el sistema operativo y no requiere ningún tratamiento especial.  
  
#### Etiquetas dinámicas  
 Cambio de etiquetas dinámica basándose en la selección actual. Siempre que sea posible, utilice etiquetas dinámicas en los diseños de maestro y detalles para ayudar al usuario a comprender que la información mostrada es pertinente a una selección específica y la información general.  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **Ejemplo de una etiqueta dinámica utilizada con contenido dinámico**  
  
#### Texto informativo  
 Algunos elementos de la interfaz se benefician de texto informativo para ayudar al usuario a comprender el propósito de la interfaz de usuario o para indicar qué acción se debe realizar.  
  
-   Texto informativo es más común en la parte superior de los cuadros de diálogo, pero puede aparecer en otras áreas para dar instrucciones a una agrupación de control complejo.  
  
-   Texto informativo no es interactivo, pero puede contener hipervínculos a temas de ayuda.  
  
-   Usar texto informativo con moderación y sólo cuando sea necesario.  
  
##### Formato  
 Texto informativo debe ser la fuente del entorno, el texto de control \(no temáticas\) estándar. Vea [Fuentes y formato de Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Para obtener más información sobre cómo escribir texto de instrucciones, consulte [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Texto informativo en un cuadro de diálogo de Visual Studio**  
  
#### Texto informativo  
 Texto informativo es texto que proporciona la información adicional del usuario. Puede ser estática o dinámica o se utilizan como una notificación. Siempre es de sólo lectura, pero si es útil para el usuario debe tener la capacidad de copiar la información, se debe colocar texto dinámico en un contenedor de control como un campo de texto de sólo lectura.  
  
##### Texto \(específico de contexto\) dinámico  
 Texto de información dinámica varía según el contexto, por ejemplo, cuando el usuario cambia el foco. A menudo, pero no siempre, contenido dinámico se empareja con una etiqueta dinámica.  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **Texto informativo dinámico varía según el contexto.**  
  
##### Formato  
 Hay dos maneras de mostrar los campos de texto de sólo lectura: ya sea directamente en la interfaz de usuario de superficie \(vea arriba\) o dentro de otro control, como un cuadro de texto o el marco de grupo. Cualquiera sea correcta según la situación. Es el Diseñador de características para determinar cómo presentar la información de solo lectura.  
  
 Puede ser texto dentro de un cuadro de texto de sólo lectura. Esto suele indica que el contenido puede ser seleccionado y copiado, aunque no se puede editar.  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **Formato de texto informativo para los campos de solo lectura**  
  
#### Marcas de agua  
 Aunque el texto puede ser el mismo, la diferencia entre las marcas de agua y el texto informativo es que las marcas de agua se reemplazan con contenido cuando la ventana de control no está vacía y el texto informativo permanece visible en todo momento.  
  
 Marcas de agua deben usarse cuando una ventana o control está vacío. Que indican qué debe hacerse para rellenar el área y pueden incluir vínculos de acción para abrir windows relevantes, como un origen de arrastre.  
  
##### Estilo Visual  
  
-   Marcas de agua se deben Centrar horizontalmente dentro de la ventana.  
  
-   Marcas de agua deben ser centrado, alineado a la izquierda no.  
  
-   Marcas de agua pueden centrados verticalmente o se situado cerca de la parte superior del área. Si se encuentra en la parte superior del área, debe haber suficiente espacio anterior para que destaque la marca de agua.  
  
-   Utilice la `Environment.GrayText` fuente de entorno estándar y token de color. Hipervínculos deben utilizar los tokens de hipervínculo estándar compartido: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, y `Environment.PanelHyperlinkDisabled`.  
  
-   No se pueden seleccionar las marcas de agua en el fondo  
  
-   Si es posible, incluir vínculos en la marca de agua para ayudar al usuario a empezar a trabajar.  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **Ejemplos de texto de marca de agua en Visual Studio**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Botones e hipervínculos  
  
### Información general  
 Controles de botones y link \(hipervínculos\) deben seguir [instrucciones básicas de escritorio de Windows en hipervínculos](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) para el uso, texto, tamaño y espaciado.  
  
### Elegir entre los botones y vínculos  
 Tradicionalmente, se han utilizado los botones para las acciones y los hipervínculos se han reservado para la navegación. Botones pueden utilizarse en todos los casos, pero se ha ampliado el rol de vínculos en Visual Studio para que sean más intercambiables en algunas condiciones de botones y vínculos.  
  
 Cuándo utilizar los botones de comando:  
  
-   Comandos principales  
  
-   Mostrar ventanas que se usan para recopilar la entrada o tomar decisiones, incluso si son comandos secundarios  
  
-   Acciones destructivas o irreversibles  
  
-   Botones de compromiso de asistentes y flujos de página  
  
 Evite los botones de comando de ventanas de herramientas, o si necesita más de dos palabras de la etiqueta. Vínculos pueden tener más etiquetas.  
  
 Cuándo utilizar vínculos:  
  
-   Navegación a otra ventana, documento o página web  
  
-   Situaciones que requieren una etiqueta más larga o una frase corta para describir el propósito de la acción  
  
-   Espacios reducidos donde un botón podría saturar la interfaz de usuario, siempre que la acción no es destructiva o irreversible  
  
-   Realce anular comandos secundarios en situaciones donde hay muchos comandos  
  
#### Ejemplos  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **Comando vínculos que se usan en la barra de información después de un mensaje de estado**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **Vínculos que se usan en el menú emergente de CodeLens**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **Vínculos que se usan para comandos secundarios donde botones conllevaría demasiada atención**  
  
### Botones comunes  
  
#### Texto  
 Siga las instrucciones de escritura de [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### Estilo Visual  
  
##### Cuadros de diálogo estándar  
 Mayoría de los botones en Visual Studio aparecerá en los cuadros de diálogo estándares y no debe ser el estilo. Debe reflejar el aspecto de botones estándar dictado por el sistema operativo.  
  
##### Aplicar un tema  
 En algunos casos, pueden utilizar botones dentro de la interfaz de usuario de estilo y deben ser el estilo adecuadamente estos botones. Consulte [Cuadros de diálogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) para obtener información sobre los controles con temas.  
  
### Botones especiales  
  
#### Examinar... botones  
 **\[Examinar...\]** botones se utilizan en las cuadrículas, cuadros de diálogo y ventanas de herramientas y otros elementos de interfaz de usuario no modales. Se muestra un selector que ayuda al usuario a rellenar un valor en un control. Existen dos variantes de este botón, largo y corto.  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **Long \[Examinar...\] botón**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **El botón corto con solo puntos suspensivos \[...\]**  
  
 Cuándo utilizar el botón corto con solo puntos suspensivos:  
  
-   Si hay más de una larga **\[Examinar...\]** botón en un cuadro de diálogo, como cuando se permiten varios campos para la exploración. Utilice el breve **\[...\]** cada uno evitar las claves de acceso confuso creadas por esta situación \(**& Examinar** y **B & r** en el mismo cuadro de diálogo\).  
  
-   En un cuadro de diálogo estrecha o cuando no hay ningún lugar para colocar el botón de tiempo razonable.  
  
-   Si el botón aparece en un control de cuadrícula.  
  
 Directrices para usar el botón:  
  
-   No utilice una tecla de acceso. Para tener acceso mediante el teclado, el usuario debe ficha del control adyacentes. Asegúrese de que el orden de tabulación es tal que cualquier botón de examinar inmediatamente después del campo que va a rellenar. Nunca use un carácter de subrayado debajo del primer período.  
  
-   Configurar Microsoft Active Accessibility \(MSAA\) **nombre** propiedad **Examinar...** \(incluidos los puntos suspensivos\) para que la pantalla se leerá lo como "Examinar" y no "punto\-punto" o "período período período." Esto implica la configuración de controles administrados, el **AccessibleName** propiedad.  
  
-   Nunca utilice puntos suspensivos **\[...\]** botón para nada excepto una acción de exploración. Por ejemplo, si necesita un **\[nuevo...\]** botón pero no tiene suficiente espacio para el texto, a continuación, debe volver a diseñar el cuadro de diálogo.  
  
##### Ajuste de tamaño y espaciado  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **Tamaño \[Examinar...\] botones**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **Espaciado \[Examinar...\] botones**  
  
#### Botones gráficos  
 Algunos botones deben utilizar siempre una imagen gráfica y nunca incluyen texto para ahorrar espacio y evitar problemas de localización. A menudo se usan en otras listas que se puede ordenar y selectores de campo.  
  
> [!NOTE]
>  Los usuarios tienen a la pestaña para estos botones \(no hay ninguna clave de acceso\), colóquelos en un orden sensato. Asignar la propiedad de nombre del botón a la acción que realiza para que los lectores de pantalla interpreten correctamente la acción del botón.  
  
|||  
|-|-|  
|Add|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|Quitar|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|Agregar todo|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|Quitar todo|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|Subir|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|Bajar|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|Eliminar|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### Ajuste de tamaño y espaciado  
 Cambiar el tamaño de botones gráficos es el mismo que para la versión abreviada de la **\[Examinar...\]** botón \(26 x 23 píxeles\):  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **Apariencia de una imagen gráfica en el botón, con y sin color transparente**  
  
### Hipervínculos  
 Los hipervínculos se adaptan perfectamente a acciones de navegación, como abrir un tema de ayuda, el cuadro de diálogo modal o el asistente. Si se usa un hipervínculo para un comando, siempre debería mostrar un cambio notable y visible para la interfaz de usuario. En general, las acciones que se compromete a una acción \(como guardar, Cancelar y eliminar\) se comunican mejor con un botón.  
  
#### Estilo de escritura  
 Siga el [orientación de escritorio de Windows para el texto de la interfaz de usuario](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). No utilice "Aprender más acerca de," "Saber más acerca de" o "Obtener ayuda con este" frases. En su lugar, frase de texto de vínculo de ayuda en cuanto a la pregunta principal respondida por el contenido de ayuda. Por ejemplo, "**cómo agregar un servidor en el Explorador de servidores?**"  
  
#### Estilo Visual  
  
-   Siempre deben usar hipervínculos [El servicio VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si no contiene ningún estilo correctamente un hipervínculo, parpadea rojo cuando está activo o se muestra un color diferente después de que se está visitando.  
  
-   No incluya un subrayado en el control que se sitúe el estado a menos que el vínculo es un fragmento de frase dentro de una frase completa, como en una marca de agua.  
  
-   Subrayado no debe aparecer al mantener el mouse. En su lugar, los comentarios al usuario que el vínculo está activo son un cambio de color ligera y el cursor de vínculo adecuado.  
  
##  <a name="BKMK_TreeViews"></a> Vistas de árbol  
  
### Información general  
 Vistas de árbol proporcionan una forma de organizar complejos se enumera en los grupos de elementos primarios y secundarios. Un usuario puede expandir o contraer grupos primarios para mostrar u ocultar los elementos secundarios subyacentes. Cada elemento de una vista de árbol puede seleccionarse para proporcionar más acciones.  
  
 Este tema trata el uso aceptable, el diseño adecuado y la funcionalidad de vistas de árbol.  
  
#### En este tema  
  
-   [Estilo Visual](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interacciones](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Estilo Visual  
  
#### Controles de expansión  
 Controles de vista de árbol deben cumplir el diseño de botón de expansión utilizado por Windows y Visual Studio. Cada nodo utiliza un control de botón de expansión para mostrar u ocultar los elementos subyacentes. Uso de un control expander proporciona coherencia para los usuarios que pueden aparecer vistas de árbol diferentes en Windows y Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Correcto: estilo correspondiente del nodo de vista de árbol mediante un control expander**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **Incorrecta: estilo incorrecto del nodo de la vista de árbol**  
  
#### Selección  
 Cuando se selecciona un nodo en la vista de árbol, debe expandir el resaltado a todo el ancho del control de vista de árbol. Esto ayuda a los usuarios a identificar claramente qué elemento ha seleccionado. Colores de selección deben reflejar el tema actual de Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Correcto: resaltado del nodo seleccionado se ajusta a todo el ancho del control de vista de árbol.**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **Incorrecta: resaltado del nodo seleccionado no ajusta a todo el ancho del control de vista de árbol.**  
  
#### Iconos  
 Iconos sólo deben usarse en los controles de vista de árbol si sirven de ayuda para identificar visualmente las diferencias entre los elementos. En general, los iconos deben usarse sólo en listas heterogéneos en los que los iconos proporcionan información para diferenciar los tipos de elementos. En una lista homogénea mediante iconos, con frecuencia se puede considerar como ruido y debe evitarse. En ese caso, el icono de grupo \(primario\) puede transmitir el tipo de elementos dentro de él. La excepción a esta regla sería si el icono es dinámico y se utiliza para indicar el estado.  
  
#### Barras de desplazamiento  
 Siempre deben estar oculta las barras de desplazamiento si el contenido se ajusta dentro del control de vista de árbol. Es aceptable para las barras de desplazamiento estar ocultas o semitransparente en una ventana desplazable y aparecen cuando la ventana que contiene la vista de árbol tiene el foco o tras la activación del árbol ver propio.  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **Porque el contenido ha superado los límites del control de vista de árbol, se muestran las barras de desplazamiento horizontal y vertical.**  
  
###  <a name="BKMK_TreeViewInteractions"></a> Interacciones  
  
#### Menús contextuales  
 Un nodo de vista de árbol puede revelar opciones de submenú en un menú contextual. Normalmente, esto se produce cuando un usuario tiene un elemento con el botón secundario o se presiona la tecla de menú en un teclado de Windows con el elemento seleccionado. Es importante que el nodo recibe el foco y se selecciona. Esto ayuda al usuario a identificar qué elemento pertenece el submenú.  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **El elemento que se genere el enfoque de mejoras en el menú contextual para notificar al usuario qué elemento se ha seleccionado.**  
  
#### Teclado  
 La vista de árbol debe proporcionar la capacidad de seleccionar los elementos y expandir o contraer los nodos mediante el teclado. Esto garantiza que la navegación cumple los requisitos de accesibilidad.  
  
##### Control de vista de árbol  
 Controles de árbol Visual Studio deben seguir la navegación de teclado comunes:  
  
-   **Flecha arriba:** seleccionar elementos moviendo el árbol  
  
-   **Flecha abajo:** bajando el árbol para seleccionar elementos  
  
-   **Flecha derecha:** expandir un nodo en el árbol  
  
-   **Flecha izquierda:** contraer un nodo en el árbol  
  
-   **Tecla ENTRAR:** iniciar, cargar, ejecutar el elemento seleccionado  
  
##### Trid \(vista de árbol y vista de cuadrícula\)  
 Un control de trid es un control complejo que contiene una vista de árbol dentro de una cuadrícula. Expandir, contraer y navegar en el árbol deben respetar los mismos comandos de teclado como una vista de árbol, con las siguientes excepciones:  
  
-   **Flecha derecha:** expandir un nodo. Después de que el nodo está expandido, debería continuar navegando hasta la columna más cercana a la derecha. Exploración debe detenerse al final de la fila.  
  
-   **Ficha:** va a la celda más cercana a la derecha.  Al final de la fila de navegación sigue a la fila siguiente.  
  
-   **Mayús \+ Tab:** va a la celda más cercana a la izquierda.  Al principio de la fila, navegación continúa en la celda situada en la fila anterior.  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **Un control de trid en Visual Studio**