---
title: Diseño para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e82ed0f65a8546cc16decce84c3cca01237694d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898757"
---
# <a name="layout-for-visual-studio"></a>Diseño para Visual Studio
La mayoría de los cuadros de diálogo de Visual Studio son [diseño del cuadro de diálogo de utilidad](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), que son el unthemed dicho estándar de seguimiento de cuadros de diálogo [principios de diseño del cuadro de diálogo de Windows Desktop](/windows/desktop/uxguide/win-dialog-box). Cuando Visual Studio se desplaza al actualizar su interfaz de usuario, algunos de los cuadros de diálogo más destacados tienen un nuevo diseño que ellos establece experiencias como definición de producto. Estos [diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tienen un aspecto con temas.  
  
##  <a name="BKMK_UtilityDialogLayout"></a> Diseño del cuadro de diálogo de utilidad  
  
-   Todos los controles dentro de un cuadro de diálogo utilidad deben iniciar en la parte superior izquierda y fluyen hacia abajo.  
  
-   Nunca center controles en un cuadro de diálogo para rellenar un área de gran tamaño.  
  
-   Utilice la fuente del entorno para todo el texto de cuadro de diálogo. Al escribir una especificación visual, especifique la fuente del entorno en lugar de seleccionar una fuente concreta y el tamaño. Consulte [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Espaciado de control coherente de uso y la ubicación para admitir el objetivo de calidad de artesano.  
  
-   Los cuadros de diálogo pueden ser más complejas de un mayor número de controles, un único juxtaposition de controles o ambos. Para estos casos complejos, permitir suficiente espacio entre las agrupaciones de control para proporcionar al usuario un flujo lógico a analizar.  
  
### <a name="utility-dialog-layout-examples"></a>Ejemplos de diseño del cuadro de diálogo Utilidad  
 Todas las dimensiones se expresan como píxeles.  
  
 ![Espaciado de cuadro de diálogo para etiquetas encima de los controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **Figura 08.01-a: Directrices de espaciado para cuadros de diálogo de utilidad con etiquetas encima de los controles**  
  
 ![Espaciado de cuadro de diálogo para etiquetas a la izquierda de los controles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **Figura 08.01-b: Directrices de espaciado para cuadros de diálogo de utilidad con etiquetas a la izquierda de los controles**  
  
### <a name="layout-details"></a>Detalles de diseño  
  
#### <a name="margins"></a>Márgenes  
  
-   Todos los cuadros de diálogo deben tener un borde de 12 píxeles en torno a todos los bordes.  
  
-   Los márgenes dentro de un marco de grupo deben ser 9 píxeles desde el borde del marco.  
  
-   Los márgenes dentro de un control de ficha deben ser 6 píxeles desde el borde del control de ficha.  
  
#### <a name="command-buttons"></a>Botones de comando  
  
- Botones de comando funcionan en el marco de cuadro de diálogo, no en el contenido. Se debe colocarse en la parte inferior derecha y debe tener suficiente espacio de variables anterior para establecer los botones claramente separados.  
  
- Si hay botones horizontales que funcionen dentro del cuadro de diálogo, la configuración del botón de comando alternativo es una pila vertical en la esquina superior derecha. Consulte [botones de comando interiores](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) a continuación.  
  
- El espacio a la izquierda de los botones de comando (parte inferior izquierda/central del cuadro de diálogo) se considera parte de "banda" de los controles de la operación de cuadro de diálogo. Lo único que debe interfieren en la que el espacio es un vínculo de ayuda que es relevante para la tarea global o un cuadro de diálogo.  
  
- Botones de comando deben ser de 75 x 23 píxeles.  
  
- Botones de comando deben ser 6 píxeles.  
  
  ![Alineación de botón básica](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
  **Figura 08.01-c: Alineación de botón básica**  
  
#### <a name="labels"></a>Etiquetas  
  
-   Alinear a la izquierda todas las etiquetas.  
  
-   Para las etiquetas que se encuentran por encima de un control, debe alinear a la izquierda con precisión con el control debajo de él y la parte inferior de la etiqueta debe ser 5 píxeles por encima de la parte superior del otro control (por ejemplo, un cuadro combinado).  
  
-   Para las etiquetas que se encuentran a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Para alinear los cuadros de texto, cuadros combinados u otros controles, se debe establecer una segunda columna implícita.  
  
-   Las etiquetas distinguen mayúsculas de la frase y seguidas de dos puntos. Consulte [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distancia entre los controles  
 Pila controles razonablemente. No hay ningún criterio absoluta para el espaciado entre controles apilados. El apriete entre los controles puede variar ligeramente entre los cuadros de diálogo. El espacio recomendado es 20 píxeles para los pares de etiqueta/control vertical y 9 píxeles para los pares de etiqueta/control horizontal. El espaciado mínimo de control para los pares horizontales es 6 píxeles.  
  
 ![Recomienda la distancia entre los controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **Figura 08.01-d: Recomendaciones para la distancia entre los controles**  
  
#### <a name="control-indentation"></a>Sangría de control  
 Cuando se anidan los controles, alinear controles internos horizontalmente, con el borde izquierdo del control anterior, normalmente la etiqueta.  
  
 ![Anidar la alineación del control](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **Figura 08.01-e: Alineación de control anidadas**  
  
#### <a name="control-width"></a>Ancho del control  
 El ancho de un cuadro de texto u otros controles similares debe ser no supere la entrada promedio del campo. La palabra inglesa promedio es de cinco caracteres. Por ejemplo, un cuadro de texto que se requiere un nombre de ruta de acceso larga debe ser siempre y cuando el diseño horizontal permite, mientras que una lista desplegable de nombres de plataforma solo deben tener una longitud que permite la entrada más larga.  
  
#### <a name="helper-text"></a>Texto auxiliar  
  
-   Un cuadro de diálogo puede mostrar texto de aplicación auxiliar que proporciona más información sobre la finalidad del cuadro de diálogo. Esto normalmente se encuentra en la parte superior y puede ser 1 o 2 oraciones.  
  
-   La longitud de línea debe ser un ancho cómodo para un usuario analizar y leer. Un cuadro de diálogo medio debe ser no más de 550 píxeles de ancho.  
  
####  <a name="BKMK_InteriorCommandButtons"></a> Botones de comando interiores  
 En los cuadros de diálogo más complejos, un control interno podría tener sus propios botones relacionados, lo que podrían afectar donde se encuentran los botones de confirmación del cuadro de diálogo.  
  
- Use una alineación vertical (columna) de interior botones cuando **Aceptar**/**cancelar** se orienta horizontalmente en la esquina inferior derecha.  
  
- Use una alineación horizontal (fila) del interior botones cuando **Aceptar**/**cancelar** se orientan verticalmente en la esquina superior derecha. Esta situación es menos común.  
  
- Tamaño de botón interiores debe tener como destino el tamaño de botón estándar de píxeles de 75 x 23, que coinciden con el tamaño de **Aceptar**/**cancelar** botones cuando sea posible. Si una etiqueta de botón hace que el botón superan el tamaño de botón estándar, los demás botones de dicho conjunto deben alinearse con ese ancho deseado.  
  
  ![Botones horizontales Aceptar y cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
  **Figura 08.01-f: Botones verticales de interiores con horizontal Aceptar/Cancelar**  
  
  ![Botones verticales Aceptar y cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
  **Figura 08.01-g: Botones horizontales de interiores con vertical Aceptar/Cancelar**  
  
#### <a name="browse-button"></a>[Examinar...] botón  
 **[Examinar...]**  botones que siguen un cuadro de texto deben detallar "Examinar..." en su totalidad, incluidos los puntos suspensivos. Si el espacio es ajustado o hay varios **[Examinar...]**  botones en la pantalla, el botón se pueden reducir a solo los puntos suspensivos.  
  
##  <a name="BKMK_ThemedDialogLayout"></a> Diseño del cuadro de diálogo con temas  
 Los cuadros de diálogo con temas en Visual Studio tienen una apariencia más clara y ofrecen más espacio en blanco. Tipografía proporciona más énfasis e intereses, ofreciendo interlineado más abierto y una variación de ponderaciones y los tamaños de fuente. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. El diseño de estos cuadros de diálogo debe seguir este patrón básico:  
  
1.  El fondo del cuadro de diálogo es blanco.  
  
2.  Hay un borde de la regla 1 píxel en un valor intermedio color gris.  
  
3.  El título del cuadro de diálogo ya no se encuentra en una barra de título, pero proporciona énfasis en un tamaño mayor de punto e interés visual. (Vea la sección de tamaño de fuente en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Las etiquetas junto con texto adicional, como una descripción, deben ser **fuente del entorno + negrita**.  
  
5.  Interiores columnas se separan mediante una regla de 1 píxel en color gris claro.  
  
6.  Vínculos predeterminados no tengan ningún carácter de subrayado. Al mantener el mouse y los Estados presionados tienen un cambio de color más el carácter de subrayado.  
  
7.  Confirmar botones (como **Aceptar**/**cancelar**) se colocan en la esquina inferior derecha.  
  
### <a name="themed-dialog-layout-examples"></a>Ejemplos de diseño del cuadro de diálogo con temas  
 ![Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **Figura 08.01-h: Cuadro de diálogo con temas**  
  
 ![Las dimensiones del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **Figura 08.01-i: Cuadro de diálogo con temas - dimensiones**  
  
 ![Fuentes del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **Figura 08.01-j: Cuadro de diálogo con temas - fuentes**  
  
 ![Los colores del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **Figura 08.01-k: Cuadro de diálogo con temas - colores**  
  
## <a name="see-also"></a>Vea también  
 [Patrones de aplicación para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controles (Windows)](/windows/desktop/uxguide/controls)   
 [Cuadros de diálogo (Windows)](/windows/desktop/uxguide/win-dialog-box)