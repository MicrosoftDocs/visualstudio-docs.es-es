---
title: "Dise&#241;o para Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Dise&#241;o para Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La mayoría de los cuadros de diálogo de Visual Studio son [Diseño del cuadro de diálogo Utilidad](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), que son el unthemed dicho estándar siga los cuadros de diálogo [principios de diseño del cuadro de diálogo de escritorio de Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Como Visual Studio se mueve al actualizar su interfaz de usuario, algunos de los cuadros de diálogo más destacados tienen un nuevo diseño que ellos establece experiencias como definición de producto. Estos [Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tienen un aspecto con temas.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Diseño del cuadro de diálogo Utilidad  
  
-   Todos los controles dentro de un cuadro de diálogo utilidad deben comenzar en la parte superior izquierda y fluyen hacia abajo.  
  
-   Nunca center controles en un cuadro de diálogo para rellenar un área de gran tamaño.  
  
-   Utilice la fuente del entorno para todo el texto de cuadro de diálogo. Al escribir una especificación visual, especificar la fuente del entorno en lugar de seleccionar una fuente concreta y el tamaño. Vea [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Espaciado de control coherente de uso y la ubicación para admitir el objetivo de la calidad de artesano.  
  
-   Cuadros de diálogo pueden ser más complejas de un mayor número de controles, un único juxtaposition de controles o ambos. Para estos casos complejos, permiten suficiente espacio entre las agrupaciones de control para proporcionar al usuario un flujo lógico para analizar.  
  
### Ejemplos de diseño del cuadro de diálogo Utilidad  
 Todas las dimensiones se expresan en píxeles.  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **Figura 08.01\-a: Espaciado directrices para los cuadros de diálogo de utilidad con etiquetas encima de los controles**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **Figura 08.01\-b: Espaciado directrices para los cuadros de diálogo de utilidad con etiquetas a la izquierda de los controles**  
  
### Diseño de detalles  
  
#### Márgenes  
  
-   Todos los cuadros de diálogo deben tener un borde de 12 píxeles alrededor de todos los bordes.  
  
-   Márgenes de un marco de grupo deben ser 9 píxeles desde el borde del marco.  
  
-   Los márgenes dentro de un control de ficha deben ser 6 píxeles desde el borde del control de ficha.  
  
#### Botones de comando  
  
-   Botones de comandos funcionan en el marco del cuadro de diálogo, no en el contenido. Se deben colocarse en la parte inferior derecha y debe tener suficiente espacio de variable anterior para establecer los botones de forma independiente.  
  
-   Si hay botones horizontales que funcionan en el cuadro de diálogo, la configuración del botón de comando alternativo es una pila vertical en la parte superior derecha. Consulte [Botones de comando interiores](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) a continuación.  
  
-   El espacio a la izquierda de los botones de comando \(parte inferior izquierda y central del cuadro de diálogo\) se considera parte de la "banda" de los controles de cuadro de diálogo operación. Lo único que debe interfieren en ese espacio es un vínculo de ayuda que corresponde a la tarea general o el cuadro de diálogo.  
  
-   Botones de comando deben ser 23 x 75 píxeles.  
  
-   Botones de comando deben ser 6 píxeles.  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **Figura 08.01\-c: Alineación de botón básica**  
  
#### Etiquetas  
  
-   Alinear a la izquierda todas las etiquetas.  
  
-   Para las etiquetas que se encuentran por encima de un control, debe alinear a la izquierda con precisión con el control debajo de ella y la parte inferior de la etiqueta debe ser 5 píxeles por encima de la parte superior del otro control \(por ejemplo, un cuadro combinado\).  
  
-   Para las etiquetas que se encuentran a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Debe establecerse una segunda columna implícita para alinear los cuadros de texto, cuadros combinados u otros controles.  
  
-   Las etiquetas son oración y seguidas de dos puntos. Vea [Estilo del texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### Distancia entre los controles  
 Controles de la pila es razonablemente. No hay ningún criterio absoluta para el espaciado entre controles apilados. El apriete entre los controles puede variar ligeramente entre los cuadros de diálogo. El espacio recomendado es 20 píxeles para los pares de etiqueta\/control vertical y 9 píxeles para los pares de etiqueta\/control horizontal. El espaciado mínimo de control para los pares horizontales es 6 píxeles.  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **Figura 08.01\-d: Recomendaciones para la distancia entre los controles**  
  
#### Control sangría  
 Cuando los controles están anidados, alinear controles internos horizontalmente con el borde izquierdo del control anterior, normalmente la etiqueta.  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **Figura 08.01\-e: La alineación del control Nested**  
  
#### Ancho del control  
 El ancho de un cuadro de texto u otros controles similares debe ser no supere la entrada promedio para el campo. La palabra inglesa promedio es de cinco caracteres. Por ejemplo, un cuadro de texto que requiere un nombre de ruta de acceso larga debe ser siempre que permite el diseño horizontal, mientras que una lista desplegable de nombres de plataforma que sólo deben tener una longitud que permite la entrada más larga.  
  
#### Texto de ayuda  
  
-   Un cuadro de diálogo puede mostrar texto de ayuda que proporciona más información sobre el propósito del cuadro de diálogo. Esto normalmente se encuentra en la parte superior y puede ser 1 o 2 frases.  
  
-   La longitud de la línea debe ser un ancho cómodo para un usuario analizar y leer. Un cuadro de diálogo medio debe ser no más de 550 píxeles de ancho.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Botones de comando interiores  
 En los cuadros de diálogo más complejas, un control interno puede tener sus propios botones relacionados, lo que podrían afectar a donde se encuentran los botones de confirmación del cuadro de diálogo.  
  
-   Utilice una alineación vertical \(columna\) de interior botones cuando **Aceptar**\/**Cancelar** se orienta horizontalmente en la esquina inferior derecha.  
  
-   Utilice una alineación horizontal \(fila\) del interior botones cuando **Aceptar**\/**Cancelar** se orientan verticalmente en la esquina superior derecha. Esta situación es menos común.  
  
-   Tamaño de botón interiores que debe dirigirse el tamaño de botón estándar de 23 x 75 píxeles, que coinciden con el tamaño de **Aceptar**\/**Cancelar** botones cuando sea posible. Si una etiqueta de botón hace que el botón superan el tamaño de botón estándar, los demás botones de ese conjunto deben alinearse con ese tamaño mayor.  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **Figura 08.01\-f: Botones Interior Vertical horizontal Aceptar o cancelar**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **Figura 08.01\-g: Botones de interiores Horizontal a vertical Aceptar o cancelar**  
  
#### \[Examinar...\] botón  
 **\[Examinar...\]** botones que siguen un cuadro de texto deben deletrear "Examinar..." en su totalidad, incluidos los puntos suspensivos. Si el espacio es reducido o hay varios **\[Examinar...\]** botones en la pantalla, el botón pueden reducirse a sólo los puntos suspensivos.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Diseño del cuadro de diálogo con temas  
 Cuadros de diálogo con temas en Visual Studio tienen un aspecto más claro y ofrecen más espacio en blanco. Tipografía proporciona mayor énfasis e interés, que ofrece más abierto interlineado y una variación de los tamaños de fuente y pesos. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. El diseño de estos cuadros de diálogo debe seguir este patrón básico:  
  
1.  El fondo del cuadro de diálogo es blanco.  
  
2.  Hay un borde de la regla de 1 píxel en un valor intermedio de gris.  
  
3.  El título del cuadro de diálogo ya no se encuentra en una barra de título, pero proporciona interés visual y énfasis de mayor tamaño de punto. \(Consulte la sección de tamaño de fuente en [Estilo del texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).\)  
  
4.  Etiquetas junto con texto adicional, como una descripción, deben ser **fuente del entorno \+ negrita**.  
  
5.  Interiores columnas están separadas por una regla de 1 píxel en gris claro.  
  
6.  Vínculos predeterminados no tienen ningún carácter de subrayado. Al mantener el mouse y los Estados presionados tienen un cambio de color más el carácter de subrayado.  
  
7.  Confirmar botones \(como **Aceptar**\/**Cancelar**\) están sentados en la esquina inferior derecha.  
  
### Ejemplos de diseño de diálogo con temas  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **Figura 08.01\-h: Cuadro de diálogo con temas**  
  
 ![Themed dialog dimensions](~/docs/extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **Figura 08.01\-i: Cuadro de diálogo con temas: dimensiones**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **Figura 08.01\-j: Cuadro de diálogo con temas: fuentes**  
  
 ![Themed dialog colors](~/docs/extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **Figura 08.01\-k: Cuadro de diálogo con temas: colores**  
  
## Vea también  
 [Patrones de aplicaciones de Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controles \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Cuadros de diálogo \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)