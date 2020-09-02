---
title: Diseño para Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698402"
---
# <a name="layout-for-visual-studio"></a>Diseño para Visual Studio
La mayoría de los cuadros de diálogo de Visual Studio son el [diseño del cuadro de diálogo](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)de la utilidad, que son los cuadros de diálogo desvinculados que siguen los principios de diseño de diálogo estándar del escritorio de [Windows](/windows/desktop/uxguide/win-dialog-box). A medida que Visual Studio se mueve para actualizar su interfaz de usuario, algunos de los cuadros de diálogo más destacados tienen un nuevo diseño que los establece como experiencias de definición del producto. Estos [diseños de cuadro de diálogo](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) tienen una apariencia de los mismos.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Diseño del cuadro de diálogo de la utilidad

- Todos los controles de un cuadro de diálogo de la utilidad deben comenzar en la parte superior o izquierda y en el flujo hacia abajo.

- No Centre nunca los controles en un cuadro de diálogo para rellenar un área grande.

- Use la fuente del entorno para todo el texto del cuadro de diálogo. Al escribir una especificación visual, especifique la fuente del entorno en lugar de seleccionar una fuente y un tamaño determinados. Vea [la fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utilice el espaciado y la ubicación de los controles coherentes para respaldar el objetivo de la calidad en el artesano.

- Los cuadros de diálogo pueden ser más complejos desde un número mayor de controles, un juxtaposition único de controles o ambos. Para esas situaciones complejas, permita un espacio adecuado entre las agrupaciones de controles para proporcionar al usuario un flujo lógico para analizar.

### <a name="utility-dialog-layout-examples"></a>Ejemplos de diseño de cuadro de diálogo de utilidad
 Todas las dimensiones se expresan como píxeles.

 ![Espaciado de cuadro de diálogo para etiquetas por encima de los controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08,01-a: instrucciones de espaciado para cuadros de diálogo de la utilidad con etiquetas por encima de los controles**

 ![Espaciado de cuadro de diálogo para etiquetas a la izquierda de los controles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08,01-b: instrucciones de espaciado para cuadros de diálogo de la utilidad con etiquetas a la izquierda de los controles**

### <a name="layout-details"></a>Detalles de diseño

#### <a name="margins"></a>Márgenes

- Todos los cuadros de diálogo deben tener un borde de 12 píxeles alrededor de todos los bordes.

- Los márgenes dentro de un marco de grupo deben ser de 9 píxeles desde el borde del marco.

- Los márgenes de un control de ficha deben ser de 6 píxeles desde el borde del control de pestaña.

#### <a name="command-buttons"></a>Botones de comando

- Los botones de comando operan en el marco del cuadro de diálogo, no en el contenido. Deben colocarse en la parte inferior derecha y deben tener suficiente espacio variable antes para establecer los botones de forma distinta.

- Si hay botones horizontales que funcionan en el cuadro de diálogo, la configuración alternativa del botón de comando es una pila vertical en la esquina superior derecha. Vea [botones del comando interior](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) a continuación.

- El espacio situado a la izquierda de los botones de comando (inferior izquierda/centro del cuadro de diálogo) se considera parte de la "banda" de los controles de operación de diálogo. Lo único que debe ser intrusión en ese espacio es un vínculo de ayuda que es relevante para la tarea o el cuadro de diálogo global.

- Los botones de comando deben ser de 75x23 píxeles.

- Los botones de comando deben tener una separación de 6 píxeles.

  ![Alineación de botón básica](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08,01-c: alineación básica del botón**

#### <a name="labels"></a>Etiquetas

- Alinear a la izquierda todas las etiquetas.

- En el caso de las etiquetas que se encuentran sobre un control, se deben alinear a la izquierda con el control situado debajo y la parte inferior de la etiqueta debe ser 5 píxeles por encima de la parte superior del otro control (por ejemplo, un cuadro combinado).

- Para las etiquetas que se encuentran a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Se debe establecer una segunda columna implícita para alinear los cuadros de texto, los cuadros combinados u otros controles.

- Las etiquetas son mayúsculas y minúsculas y van seguidas de un signo de dos puntos. Vea [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distancia entre controles
 Controles de pila razonablemente. No hay ninguna instrucción absoluta para el espaciado entre los controles apilados. El grado de apriete entre los controles puede variar ligeramente entre los cuadros de diálogo. El espaciado recomendado es de 20 píxeles para los pares de control/etiqueta verticales y 9 píxeles para los pares de control/etiqueta horizontal. El espaciado de control mínimo para los pares horizontales es de 6 píxeles.

 ![Distancia recomendada entre controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08,01-d: recomendaciones para la distancia entre controles**

#### <a name="control-indentation"></a>Sangría de controles
 Cuando los controles están anidados, alinea los controles internos horizontalmente con el borde izquierdo del control anterior, normalmente la etiqueta.

 ![Alineación de control anidado](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08,01-e: alineación de controles anidados**

#### <a name="control-width"></a>Ancho del control
 El ancho de un cuadro de texto u otros controles similares no debe ser mayor que el promedio de entrada del campo. La palabra media inglesa es de cinco caracteres. Por ejemplo, un cuadro de texto que requiera un nombre de ruta de acceso largo debe tener el mismo tamaño que el diseño horizontal, mientras que una lista desplegable para los nombres de plataforma solo debe ser una longitud que permita la entrada más larga.

#### <a name="helper-text"></a>Texto auxiliar

- Un cuadro de diálogo puede mostrar texto auxiliar que proporciona más información sobre el propósito del cuadro de diálogo. Normalmente se encuentra en la parte superior y puede ser de 1-2 oraciones.

- La longitud de línea debe ser un ancho cómodo para que un usuario pueda analizar y leer. Un cuadro de diálogo medio no debe tener más de 550 píxeles de ancho.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Botones del comando interior
 En cuadros de diálogo más complejos, un control interno podría tener sus propios botones relacionados, lo que podría afectar al lugar donde se encuentran los botones de confirmación del cuadro de diálogo.

- Use una alineación vertical (columna) de los botones interiores **OK**cuando / la**cancelación** de la OK esté orientada horizontalmente en la esquina inferior derecha.

- Use una alineación horizontal (fila) de botones interiores cuando **OK** / la**cancelación** de la aceptar esté orientada verticalmente en la esquina superior derecha. Esta situación es menos frecuente.

- El tamaño del botón interior debe tener como destino el tamaño de botón estándar de 75x23 píxeles, que coincide con el tamaño de los botones de cancelación **correctos** / **Cancel** cuando sea posible. Si una etiqueta de botón hace que el botón supere el tamaño de botón estándar, los demás botones del conjunto deben alinearse con ese tamaño más amplio.

  ![Botones horizontales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08,01-f: botones interiores verticales con el botón Aceptar o cancelar horizontalmente**

  ![Botones verticales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08,01-g: botones interiores horizontales con aceptar o cancelar verticalmente**

#### <a name="browse-button"></a>[Examinar...] botón
 **[Examinar...]** los botones que siguen a un cuadro de texto deben deletrear "examinar..." en su totalidad, incluidos los puntos suspensivos. Si el espacio es estrecho o hay varios botones **[examinar...]** en la pantalla, el botón se puede reducir solo a los puntos suspensivos.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Diseño del cuadro de diálogo con la función
 En Visual Studio, los cuadros de diálogo tienen una apariencia más clara y ofrecen más espacio en blanco. La tipografía proporciona más énfasis e interés, ofreciendo más interlineado y una variación de los tamaños y pesos de las fuentes. Siempre que sea posible, los cromos y las barras de título se han reducido o quitado. El diseño de estos cuadros de diálogo debe seguir este patrón básico:

1. El fondo del cuadro de diálogo es blanco.

2. Hay un borde de regla de 1 píxel en un gris de valor medio.

3. El título del cuadro de diálogo ya no se encuentra en una barra de título, pero proporciona interés visual y énfasis en un tamaño de punto mayor. (Vea la sección tamaño de fuente en [estilo de texto](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)).

4. Las etiquetas Unidas con texto adicional, como una descripción, deben ser de **tipo entorno + negrita**.

5. Las columnas interiores están separadas por una regla de 1 píxel en gris claro.

6. Los vínculos predeterminados no tienen un carácter de subrayado. Los Estados de mantener el mouse y presionado tienen un cambio de color más el carácter de subrayado.

7. Los botones de confirmación (como **Aceptar** / **Cancelar**) se encuentran en la esquina inferior derecha.

### <a name="themed-dialog-layout-examples"></a>Ejemplos de diseño de cuadro de diálogo con
 ![Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08,01-h: cuadro de diálogo con los**

 ![Dimensiones del diálogo con temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08,01-i: cuadro de diálogo con las dimensiones**

 ![Fuentes del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08,01-j: cuadro de diálogo con las mismas fuentes**

 ![Colores del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08,01-k: colores de diálogo con la misma**

## <a name="see-also"></a>Vea también
- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controles (Windows)](/windows/desktop/uxguide/controls)
- [Cuadros de diálogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
