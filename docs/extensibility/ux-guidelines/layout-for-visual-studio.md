---
title: "Diseño para Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ef3c590a82fc3a7b89d21684ffe2e4b0f216ca98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="layout-for-visual-studio"></a>Diseño para Visual Studio
La mayoría de los cuadros de diálogo de Visual Studio están [diseño del cuadro de diálogo de utilidad](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), que son el unthemed dicho seguimiento estándar de cuadros de diálogo [principios de diseño del cuadro de diálogo de escritorio de Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx). Cuando Visual Studio se desplace a actualizar su interfaz de usuario, algunos de los cuadros de diálogo más importancia tienen un nuevo diseño que ellos establece experiencias como definición de producto. Estos [diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tienen un aspecto con temas.  
  
##  <a name="BKMK_UtilityDialogLayout"></a>Diseño del cuadro de diálogo de utilidad  
  
-   Todos los controles en un cuadro de diálogo de utilidad deben empezar en la parte superior izquierda y flujo hacia abajo.  
  
-   Nunca center controles en un cuadro de diálogo para rellenar una gran área.  
  
-   Usar la fuente del entorno de todo el texto de cuadro de diálogo. Al escribir una especificación visual, especifique la fuente del entorno en lugar de seleccionar una fuente concreta y el tamaño. Vea [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).  
  
-   Espaciado de control coherente de uso y la ubicación para admitir el objetivo de calidad de acabado.  
  
-   Los cuadros de diálogo pueden resultar más complejos de un mayor número de controles, un único juxtaposition de controles o ambos. Para estos casos complejos, deje suficiente espacio entre las agrupaciones de control para proporcionar al usuario un flujo lógico para analizar.  
  
### <a name="utility-dialog-layout-examples"></a>Ejemplos de diseño del cuadro de diálogo de utilidad  
 Todas las dimensiones se expresan como píxeles.  
  
 ![Espaciado de cuadro de diálogo para etiquetas encima de los controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "a_UtilitySpacingAbove 0801")  
  
 **Figura 08.01-a: Espaciado directrices para los cuadros de diálogo de utilidad con etiquetas encima de los controles**  
  
 ![Espaciado de cuadro de diálogo para etiquetas a la izquierda de los controles de](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "b_UtilitySpacingLeft 0801")  
  
 **Figura 08.01-b: Espaciado directrices para los cuadros de diálogo de utilidad con etiquetas a la izquierda de los controles**  
  
### <a name="layout-details"></a>Detalles de diseño  
  
#### <a name="margins"></a>Márgenes  
  
-   Todos los cuadros de diálogo deben tener un borde de 12-píxel alrededor de los bordes.  
  
-   Los márgenes dentro de un marco de grupo deben ser 9 píxeles desde el borde del marco.  
  
-   Los márgenes dentro de un control de ficha deben ser 6 píxeles desde el borde del control de ficha.  
  
#### <a name="command-buttons"></a>Botones de comando  
  
-   Botones de comando funcionan en el marco del cuadro de diálogo, no en el contenido. Se debe colocarse en la parte inferior derecha y debe tener suficiente espacio de variable anterior para establecer los botones claramente separados.  
  
-   Si hay botones horizontales que operan en el cuadro de diálogo, la configuración del botón de comando alternativo es una pila vertical en la esquina superior derecha. Vea [botones de comando interiores](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) a continuación.  
  
-   El espacio a la izquierda de los botones de comando (parte inferior izquierda y central del cuadro de diálogo) se considera parte de la banda de"" de los controles de cuadro de diálogo operación. Lo único que debe interfieren en ese espacio es un vínculo de ayuda que es relevante para la tarea global o el cuadro de diálogo.  
  
-   Botones de comando deben ser x 23 de 75 píxeles.  
  
-   Botones de comando deben ser 6 píxeles.  
  
 ![Alineación de botón básica](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "c_ButtonAlign 0801")  
  
 **Figura 08.01-c: Alineación de botón básica**  
  
#### <a name="labels"></a>Etiquetas  
  
-   Alinear a la izquierda todas las etiquetas.  
  
-   Para las etiquetas que se encuentran por encima de un control, debe alinear a la izquierda con precisión con el control por debajo de él y la parte inferior de la etiqueta debe ser 5 píxeles por encima de la parte superior del otro control (por ejemplo, un cuadro combinado).  
  
-   Para las etiquetas que se encuentran a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Para alinear los cuadros de texto, cuadros combinados u otros controles que se debe establecer una segunda columna implícita.  
  
-   Las etiquetas distinguen mayúsculas de la oración y seguidas de dos puntos. Vea [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
#### <a name="distance-between-controls"></a>Distancia entre los controles  
 Controles de la pila es razonablemente. No hay ninguna regla absoluta para el espaciado entre controles apilados. El apriete entre los controles puede variar ligeramente entre los cuadros de diálogo. El espacio recomendado es 20 píxeles para los pares de etiqueta/control vertical y 9 píxeles para los pares de horizontal o etiquetas de control. El espaciado mínimo de control para los pares horizontales es 6 píxeles.  
  
 ![Distancia entre los controles se recomienda](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "d_ControlDistance 0801")  
  
 **Figura 08.01-d: Recomendaciones para la distancia entre los controles**  
  
#### <a name="control-indentation"></a>Control sangría  
 Cuando los controles están anidados, alinear los controles internos horizontalmente con el borde izquierdo del control anterior, por lo general la etiqueta.  
  
 ![Anidar la alineación del control](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "e_ControlAlign 0801")  
  
 **Figura 08.01-e: La alineación del control Nested**  
  
#### <a name="control-width"></a>Ancho del control  
 El ancho de un cuadro de texto u otros controles similares debe ser no supere los datos proporcionados por el promedio para el campo. La palabra inglesa promedio es de cinco caracteres. Por ejemplo, un cuadro de texto que requiere un nombre de ruta de acceso larga duración debe ser igual que permite el diseño horizontal, mientras que una lista desplegable de nombres de plataforma solo deben tener una longitud que permite la entrada más larga.  
  
#### <a name="helper-text"></a>Texto auxiliar  
  
-   Un cuadro de diálogo puede mostrar texto de aplicación auxiliar que proporciona más información sobre la finalidad del cuadro de diálogo. Esto normalmente se encuentra en la parte superior y puede ser 1 o 2 frases.  
  
-   La longitud de línea debe ser un valor de ancho cómodo para un usuario analizar y leer. Un cuadro de diálogo intermedio debe ser no más de 550 píxeles de ancho.  
  
####  <a name="BKMK_InteriorCommandButtons"></a>Botones de comando interiores  
 En los cuadros de diálogo más complejos, un control interno podría tener sus propios botones relacionados, lo que podrían afectar a donde se encuentran los botones de confirmación del cuadro de diálogo.  
  
-   Use una alineación vertical (columna) del interior botones cuando **Aceptar**/**cancelar** se orienta horizontalmente en la esquina inferior derecha.  
  
-   Use una alineación horizontal (fila) del interior botones cuando **Aceptar**/**cancelar** se orientan verticalmente en la esquina superior derecha. Esta situación es menos común.  
  
-   Tamaño de los botones interior debe tener como destino el tamaño de los botones estándar de píxeles de 75 x 23, que coinciden con el tamaño de **Aceptar**/**cancelar** botones cuando sea posible. Si una etiqueta de botón hace que el botón superan el tamaño de los botones estándar, los demás botones de ese conjunto deben alinearse con ese tamaño más amplio.  
  
 ![Botones horizontales Aceptar y cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "f_HorizOKCan 0801")  
  
 **Figura 08.01-f: Botones de Vertical Interior con horizontal Aceptar/Cancelar**  
  
 ![Botones verticales Aceptar y cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "g_VertOKCan 0801")  
  
 **Figura 08.01-g: Botones de interiores Horizontal a vertical Aceptar o cancelar**  
  
#### <a name="browse-button"></a>[Examinar...] botón  
 **[Examinar...]**  botones que siguen un cuadro de texto deben deletrear "Examinar..." en su totalidad, incluidos los puntos suspensivos. Si hay una estrecha espacio o hay varios **[Examinar...]**  botones en la pantalla, el botón se pueden reducir a solo los puntos suspensivos.  
  
##  <a name="BKMK_ThemedDialogLayout"></a>Diseño del cuadro de diálogo con temas  
 Los cuadros de diálogo con temas en Visual Studio tienen un aspecto más claro y ofrecen más espacio en blanco. Tipografía proporciona más énfasis e interés, ya que proporcionan más abierto interlineado y una variedad de tamaños de fuente y pesos. Siempre que sea posible, barras de título y chrome se han reducido o eliminado. El diseño de estos cuadros de diálogo debe seguir este patrón básico:  
  
1.  El fondo del cuadro de diálogo es blanco.  
  
2.  Hay un borde de la regla 1 píxel en un valor intermedio gris.  
  
3.  El título del cuadro de diálogo ya no se encuentra en una barra de título, pero proporciona interés visual y énfasis de mayor tamaño de punto. (Vea la sección de tamaño de fuente en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)  
  
4.  Las etiquetas de acoplamiento con texto adicional, como una descripción, **fuente del entorno + negrita**.  
  
5.  Columnas interiores están separadas por una regla de 1 píxel en gris claro.  
  
6.  Los vínculos de forma predeterminada no tienen ningún carácter de subrayado. Al mantener el mouse y Estados presionados tienen un cambio de color más el carácter de subrayado.  
  
7.  Confirmar botones (como **Aceptar**/**cancelar**) se colocan en la esquina inferior derecha.  
  
### <a name="themed-dialog-layout-examples"></a>Ejemplos de diseño del cuadro de diálogo con temas  
 ![Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "h_ThemedDialog 0801")  
  
 **Figura 08.01-h: Cuadro de diálogo con temas**  
  
 ![Dimensiones del diálogo con temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "i_ThemedDialogDimensions 0801")  
  
 **Figura 08.01-i: Cuadro de diálogo con temas - dimensiones**  
  
 ![Las fuentes del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "j_ThemedDialogFonts 0801")  
  
 **Figura 08.01-j: Cuadro de diálogo con temas - fuentes**  
  
 ![Colores del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "k_ThemedDialogColors 0801")  
  
 **Figura 08.01-k: Cuadro de diálogo con temas - colores**  
  
## <a name="see-also"></a>Vea también  
 [Patrones de aplicación para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [Controles (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [Cuadros de diálogo (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)