---
title: Diseño para Visual Studio ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698402"
---
# <a name="layout-for-visual-studio"></a>Diseño para Visual Studio
La mayoría de los cuadros de diálogo de Visual Studio son Diseño de cuadro de [diálogo Utilidad](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), que son los cuadros de diálogo sin tema que siguen los principios de diseño de cuadro de diálogo estándar de Windows [Desktop.](/windows/desktop/uxguide/win-dialog-box) A medida que Visual Studio se mueve para actualizar su interfaz de usuario, algunos de los cuadros de diálogo más destacados tienen un nuevo diseño que los establece como experiencias de definición de productos. Estos diseños de cuadro de [diálogo temáticos](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tienen una apariencia temática.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Diseño del cuadro de diálogo de la utilidad

- Todos los controles dentro de un cuadro de diálogo de utilidad deben comenzar en la parte superior /izquierda y fluir hacia abajo.

- Nunca centre los controles en un cuadro de diálogo para rellenar un área grande.

- Utilice la fuente de entorno para todo el texto del cuadro de diálogo. Al escribir una especificación visual, especifique la fuente del entorno en lugar de seleccionar una fuente y un tamaño determinados. Consulte [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utilice un espaciado de control y una colocación uniformes para apoyar el objetivo de calidad en la artesanía.

- Los cuadros de diálogo pueden volverse más complejos a partir de un mayor número de controles, una yuxtaposición única de controles o ambos. Para esas situaciones complejas, permita un espacio adecuado entre las agrupaciones de control para proporcionar al usuario un flujo lógico para analizar.

### <a name="utility-dialog-layout-examples"></a>Ejemplos de diseño de cuadro de diálogo de utilidad
 Todas las dimensiones se expresan como píxeles.

 ![Espaciado de cuadro de diálogo para etiquetas por encima de los controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08.01-a: Directrices de espaciado para cuadros de diálogo de utilidades con etiquetas por encima de los controles**

 ![Espaciado de cuadro de diálogo para etiquetas a la izquierda de los controles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08.01-b: Directrices de espaciado para diálogos de utilidades con etiquetas a la izquierda de los controles**

### <a name="layout-details"></a>Detalles del diseño

#### <a name="margins"></a>Márgenes

- Todos los cuadros de diálogo deben tener un borde de 12 píxeles alrededor de todos los bordes.

- Los márgenes dentro de un marco de grupo deben estar a 9 píxeles del borde del marco.

- Los márgenes dentro de un control de ficha deben estar a 6 píxeles del borde del control de ficha.

#### <a name="command-buttons"></a>Botones de comando

- Los botones de comando funcionan en el marco de diálogo, no en el contenido. Deben colocarse en la parte inferior derecha y deben tener suficiente espacio variable arriba para establecer los botones claramente separados.

- Si hay botones horizontales que funcionan dentro del cuadro de diálogo, la configuración del botón de comando alternativo es una pila vertical en la parte superior derecha. Consulte los [botones](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) de comando Interior a continuación.

- El espacio a la izquierda de los botones de comando (inferior izquierda/centro del cuadro de diálogo) se considera parte de la "banda" de los controles de operación del cuadro de diálogo. Lo único que debe inmiscuirse en ese espacio es un vínculo de Ayuda que sea relevante para la tarea o el cuadro de diálogo general.

- Los botones de comando deben ser de 75x23 píxeles.

- Los botones de comando deben estar separados por 6 píxeles.

  ![Alineación de botón básica](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08.01-c: Alineación básica de botones**

#### <a name="labels"></a>Etiquetas

- Alinee a la izquierda todas las etiquetas.

- Para las etiquetas que se encuentran encima de un control, deben alinearse a la izquierda con precisión con el control debajo de él y la parte inferior de la etiqueta debe estar 5 píxeles por encima de la parte superior del otro control (por ejemplo, un cuadro combinado).

- Para las etiquetas que se sentan a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Se debe establecer una segunda columna implícita para alinear los cuadros de texto, cuadros combinados u otros controles.

- Las etiquetas son mayúsculas y minúsculas y van seguidas de dos puntos. Consulte [Estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distancia entre los controles
 Controles de pila razonablemente. No hay ninguna directriz absoluta para el espaciado entre los controles apilados. La tensión entre los controles puede variar ligeramente entre los cuadros de diálogo. El espaciado recomendado es de 20 píxeles para los pares verticales de control/etiqueta y de 9 píxeles para los pares horizontales de control/etiqueta. El espaciado de control mínimo para los pares horizontales es de 6 píxeles.

 ![Distancia recomendada entre controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08.01-d: Recomendaciones para la distancia entre los controles**

#### <a name="control-indentation"></a>Sangría de control
 Cuando los controles están anidados, alinee los controles internos horizontalmente con el borde izquierdo del control anterior, normalmente la etiqueta.

 ![Alineación de control anidado](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08.01-e: Alineación de control anidado**

#### <a name="control-width"></a>Ancho de control
 El ancho de un cuadro de texto u otros controles similares no debe ser mayor que la entrada promedio para el campo. La palabra en inglés promedio es de cinco caracteres. Por ejemplo, un cuadro de texto que requiere un nombre de ruta de acceso largo debe ser siempre y cuando el diseño horizontal lo permita, mientras que una lista desplegable para los nombres de plataforma solo debe ser una longitud que permita la entrada más larga.

#### <a name="helper-text"></a>Texto auxiliar

- Un cuadro de diálogo puede mostrar texto auxiliar que proporciona más información sobre el propósito del cuadro de diálogo. Esto normalmente se sienta en la parte superior y puede ser 1-2 oraciones.

- La longitud de la línea debe ser un ancho cómodo para que un usuario la analice y lea. Un cuadro de diálogo medio no debe tener más de 550 píxeles de ancho.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Botones de comando interiores
 En cuadros de diálogo más complejos, un control interno puede tener sus propios botones relacionados, que pueden afectar a dónde se encuentran los botones de confirmación del cuadro de diálogo.

- Utilice una alineación vertical (columna) de botones interiores cuando **OK**/**Cancel** estén orientados horizontalmente en la esquina inferior derecha.

- Utilice una alineación horizontal (fila) de botones interiores cuando **OK**/**Cancel** estén orientados verticalmente en la esquina superior derecha. Esta situación es menos común.

- El tamaño del botón interior debe tener como objetivo el tamaño estándar del botón de 75x23 píxeles, que coincida con el tamaño de los botones **Ok**/**Cancel** cuando sea posible. Si una etiqueta de botón hace que el botón supere el tamaño del botón estándar, los demás botones de ese conjunto deben alinearse con ese tamaño más amplio.

  ![Botones horizontales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08.01-f: Botones interiores verticales con OK/Cancelar horizontal**

  ![Botones verticales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08.01-g: Botones interiores horizontales con OK/Cancelar vertical**

#### <a name="browse-button"></a>[Examinar...] Botón
 **[Examinar...]** botones que siguen a un cuadro de texto deben deletrear "Examinar..." en su totalidad, incluyendo los puntos suspensivos. Si el espacio es reducido o hay varios botones **[Examinar...]** en la pantalla, el botón se puede reducir a solo los puntos suspensivos.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Diseño de cuadro de diálogo temático
 Los cuadros de diálogo temáticos de Visual Studio tienen un aspecto más claro y ofrecen más espacio en blanco. La tipografía proporciona más énfasis e interés, ofreciendo un espaciado de línea más abierto y una variación de tamaños y pesos de fuente. Siempre que sea posible, las barras de cromo y título se han reducido o eliminado. El diseño de estos cuadros de diálogo debe seguir este patrón básico:

1. El fondo del cuadro de diálogo es blanco.

2. Hay un borde de regla de 1 píxel en un gris de valor medio.

3. El título del cuadro de diálogo ya no se encuentra en una barra de título, pero proporciona interés visual y énfasis en un tamaño de punto más grande. (Consulte la sección de tamaño de fuente en Estilo de [texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Las etiquetas junto con texto adicional, como una descripción, deben ser Fuente de entorno **+ Negrita**.

5. Las columnas interiores están separadas por una regla de 1 píxel en gris claro.

6. Los vínculos predeterminados no tienen guiones bajos. Los estados de desplazamiento y presionado tienen un cambio de color más subrayado.

7. Los botones de confirmación (como **Ok**/**Cancel)** se establecen en la esquina inferior derecha.

### <a name="themed-dialog-layout-examples"></a>Ejemplos de diseño de cuadro de diálogo temático
 ![Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08.01-h: Diálogo temático**

 ![Dimensiones del diálogo con temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08.01-i: Diálogo temático - Dimensiones**

 ![Fuentes del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08.01-j: Diálogo temático - Fuentes**

 ![Colores del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08.01-k: Diálogo temático - Colores**

## <a name="see-also"></a>Vea también
- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controles (Windows)](/windows/desktop/uxguide/controls)
- [Cuadros de diálogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
