---
title: Diseño para Visual Studio | Microsoft Docs
description: Obtenga información sobre el diseño de Visual Studio diálogos, incluidos los diálogos sin insertar y los diálogos nuevos que tienen una apariencia con un aspecto con el mismo formato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e52b7b3fd620080b73e8d3de80672003ecb8fcf7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900536"
---
# <a name="layout-for-visual-studio"></a>Diseño para Visual Studio
La mayoría de los Visual Studio diálogos son diseño de diálogos de la utilidad [,](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)que son los diálogos no ateados que siguen los principios estándar de diseño de diálogos de escritorio [de Windows](/windows/desktop/uxguide/win-dialog-box). A Visual Studio para actualizar su interfaz de usuario, algunos de los diálogos más destacados tienen un nuevo diseño que los establece como experiencias de definición de productos. Estos [diseños de diálogos con aspecto](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) themed tienen una apariencia de tipo themed.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Diseño del cuadro de diálogo de la utilidad

- Todos los controles dentro de un cuadro de diálogo de utilidad deben comenzar en la parte superior o izquierda y fluir hacia abajo.

- No centrar nunca los controles en un cuadro de diálogo para rellenar un área grande.

- Use la fuente del entorno para todo el texto del cuadro de diálogo. Al escribir una especificación visual, especifique la fuente del entorno en lugar de seleccionar una fuente y un tamaño determinados. Vea [La fuente del entorno](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Use el espaciado de control y la selección de ubicación coherentes para admitir el objetivo de calidad en la separación.

- Los diálogos pueden ser más complejos a partir de un mayor número de controles, una yuxtaposición única de controles o ambos. En esas situaciones complejas, permita espacio adecuado entre las agrupaciones de control para proporcionar al usuario un flujo lógico para analizar.

### <a name="utility-dialog-layout-examples"></a>Ejemplos de diseño de cuadro de diálogo de utilidad
 Todas las dimensiones se expresan como píxeles.

 ![Espaciado de cuadro de diálogo para etiquetas por encima de los controles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figura 08.01-a: Directrices de espaciado para diálogos de utilidad con etiquetas anteriores**

 ![Espaciado de cuadro de diálogo para etiquetas a la izquierda de los controles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figura 08.01-b: Directrices de espaciado para diálogos de utilidad con etiquetas a la izquierda de los controles**

### <a name="layout-details"></a>Detalles del diseño

#### <a name="margins"></a>Márgenes

- Todos los diálogos deben tener un borde de 12 píxeles alrededor de todos los bordes.

- Los márgenes dentro de un marco de grupo deben estar a 9 píxeles del borde del marco.

- Los márgenes dentro de un control de pestaña deben estar a 6 píxeles del borde del control de ficha.

#### <a name="command-buttons"></a>Botones de comando

- Los botones de comando funcionan en el marco de diálogo, no en el contenido. Deben colocarse en la parte inferior derecha y deben tener suficiente espacio variable arriba para establecer los botones claramente independientes.

- Si hay botones horizontales que funcionan dentro del cuadro de diálogo, la configuración del botón de comando alternativo es una pila vertical en la esquina superior derecha. Consulte [Botones de comandos interiores a](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) continuación.

- El espacio situado a la izquierda de los botones de comando (inferior izquierda o centro del diálogo) se considera parte de la "banda" de controles de operación de diálogo. Lo único que debe intruir en ese espacio es un vínculo de Ayuda que sea relevante para la tarea o el cuadro de diálogo general.

- Los botones de comando deben ser de 75 x 23 píxeles.

- Los botones de comando deben tener una separación de 6 píxeles.

  ![Alineación de botón básica](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figura 08.01-c: Alineación de botón básico**

#### <a name="labels"></a>Etiquetas

- Alinear todas las etiquetas a la izquierda.

- En el caso de las etiquetas que se encuentra encima de un control, deben alinearse a la izquierda exactamente con el control que hay debajo y la parte inferior de la etiqueta debe estar 5 píxeles por encima de la parte superior del otro control (por ejemplo, un cuadro combinado).

- En el caso de las etiquetas que se encuentra a la izquierda de los controles, el ancho mínimo entre la etiqueta y el control de entrada es de 10 píxeles. Se debe establecer una segunda columna implícita para alinear los cuadros de texto, los cuadros combinados u otros controles.

- Las etiquetas son mayúsculas y minúsculas y van seguidas de dos puntos. Vea [Estilo de texto.](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

#### <a name="distance-between-controls"></a>Distancia entre controles
 Controles de pila razonablemente. No hay ninguna directriz absoluta para el espaciado entre controles apilados. La tensión entre los controles puede variar ligeramente entre los diálogos. El espaciado recomendado es de 20 píxeles para los pares de etiquetas y control verticales y de 9 píxeles para los pares de etiquetas y control horizontal. El espaciado de control mínimo para los pares horizontales es de 6 píxeles.

 ![Distancia recomendada entre controles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figura 08.01-d: Recomendaciones para la distancia entre controles**

#### <a name="control-indentation"></a>Sangría de control
 Cuando los controles están anidados, alinee los controles internos horizontalmente con el borde izquierdo del control anterior, normalmente la etiqueta .

 ![Alineación de control anidado](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figura 08.01-e: Alineación de controles anidados**

#### <a name="control-width"></a>Ancho del control
 El ancho de un cuadro de texto u otros controles similares no debe ser mayor que la entrada media del campo. La palabra en inglés promedio es de cinco caracteres. Por ejemplo, un cuadro de texto que requiere un nombre de ruta de acceso largo debe ser siempre que el diseño horizontal lo permita, mientras que una lista desplegable para los nombres de plataforma solo debe ser una longitud que permita la entrada más larga.

#### <a name="helper-text"></a>Texto del asistente

- Un cuadro de diálogo puede mostrar texto auxiliar que proporciona más información sobre el propósito del diálogo. Normalmente, se encuentra en la parte superior y puede tener entre 1 y 2 oraciones.

- La longitud de línea debe ser un ancho cómodo para que un usuario lo analice y lea. Un cuadro de diálogo medio no debe tener más de 550 píxeles de ancho.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Botones de comando interior
 En diálogos más complejos, un control interno podría tener sus propios botones relacionados, lo que podría afectar a dónde se encuentran los botones de confirmación del diálogo.

- Use una alineación vertical (columna) de botones interiores cuando **Aceptar** cancelar esté /  orientado horizontalmente en la esquina inferior derecha.

- Use una alineación horizontal (fila) de botones interiores cuando **Aceptar** cancelar esté /  orientado verticalmente en la esquina superior derecha. Esta situación es menos común.

- El tamaño del botón interior debe tener como destino el tamaño de botón estándar de 75 x 23 píxeles, que coincida con el tamaño de los botones **Aceptar** / **cancelar** siempre que sea posible. Si una etiqueta de botón hace que el botón supere el tamaño del botón estándar, los demás botones de ese conjunto deben alinearse con ese tamaño más amplio.

  ![Botones horizontales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figura 08.01-f: Botones interiores verticales con ok/cancel horizontal**

  ![Botones verticales Aceptar y Cancelar](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figura 08.01-g: Botones interiores horizontales con aceptar/cancelar vertical**

#### <a name="browse-button"></a>[Examinar...] Botón
 **[Examinar...]** Los botones que siguen a un cuadro de texto deben escribir "Examinar..." en su totalidad, incluidos los puntos suspensivos. Si el espacio es estrecho o hay varios **botones [Examinar...]** en la pantalla, el botón se puede reducir solo a los puntos suspensivos.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Diseño del cuadro de diálogo con información
 Los diálogos con Visual Studio tienen un aspecto más claro y ofrecen más espacio en blanco. La tipografía proporciona más énfasis e interés, lo que ofrece más espaciado de línea abierto y una variación de los tamaños de fuente y los pesos. Siempre que sea posible, las barras de chrome y title se han reducido o quitado. El diseño de estos diálogos debe seguir este patrón básico:

1. El fondo del cuadro de diálogo es blanco.

2. Hay un borde de regla de 1 píxel en un gris de valor medio.

3. El título del cuadro de diálogo ya no se encuentra en una barra de título, sino que proporciona interés visual y énfasis en un tamaño de punto mayor. (Vea la sección tamaño de fuente en [Estilo de texto).](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)

4. Las etiquetas junto con texto adicional, como una descripción, deben ser **Fuente de entorno + Negrita.**

5. Las columnas interiores están separadas por una regla de 1 píxel en gris claro.

6. Los vínculos predeterminados no tienen caracteres de subrayado. Los estados de mantener el puntero y presionado tienen un cambio de color más un carácter de subrayado.

7. Los botones de confirmación (como **Aceptar** / **cancelar)** se senten en la esquina inferior derecha.

### <a name="themed-dialog-layout-examples"></a>Ejemplos de diseño de cuadros de diálogo con información
 ![Diseño del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figura 08.01-h: Cuadro de diálogo con información**

 ![Dimensiones del diálogo con temas](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figura 08.01-i: Cuadro de diálogo con información sobre dimensiones**

 ![Fuentes del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figura 08.01-j: Cuadro de diálogo con tema: fuentes**

 ![Colores del cuadro de diálogo con temas](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figura 08.01-k: Cuadro de diálogo con tema: colores**

## <a name="see-also"></a>Consulta también
- [Patrones de aplicaciones para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Controles (Windows)](/windows/desktop/uxguide/controls)
- [Cuadros de diálogo (Windows)](/windows/desktop/uxguide/win-dialog-box)
