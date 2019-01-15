---
title: Opciones, Editor de texto, Todos los idiomas, Barras de desplazamiento
ms.date: 10/25/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Scroll_Bars
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 881f995dc8f4c675691f7eaa63d26acefd4b3d01
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876791"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Opciones, Editor de texto, Todos los idiomas, Barras de desplazamiento
Este cuadro de diálogo le permite cambiar el comportamiento predeterminado de la barra de desplazamiento del Editor de código. Para mostrar estas opciones, seleccione **Opciones** desde el menú **Herramientas**. En la carpeta **Editor de texto**, expanda la subcarpeta **Todos los idiomas** y después seleccione **Barras de desplazamiento**.

> [!CAUTION]
> Esta página establece las opciones predeterminadas de todos los lenguajes de desarrollo. Restablecer una opción en este cuadro de diálogo restablecerá las opciones de barras de desplazamiento de todos los idiomas para cualquier elección seleccionada aquí. Para cambiar las opciones del Editor de texto solo de un lenguaje, expanda la subcarpeta de ese lenguaje y seleccione sus páginas de opciones.

## <a name="show-horizontal-scroll-bar"></a>Mostrar barra de desplazamiento horizontal

Cuando está seleccionada, muestra una barra de desplazamiento horizontal que le permite desplazarse de lado a lado para ver elementos que quedan fuera del área de visualización del editor. Si las barras de desplazamiento horizontales no están disponibles, puede usar las teclas de dirección para desplazarse.

## <a name="show-vertical-scroll-bar"></a>Mostrar barra de desplazamiento vertical

Cuando está seleccionada, muestra una barra de desplazamiento vertical que le permite desplazarse hacia arriba y hacia abajo para ver elementos que quedan fuera del área de visualización del editor. Si las barras de desplazamiento verticales no están disponibles, puede usar las teclas de dirección, la tecla Retroceder Página y la tecla Avanzar Página para desplazarse.

## <a name="display"></a>Pantalla

### <a name="show-annotations-over-vertical-scroll-bar"></a>Mostrar anotaciones en barra de desplazamiento vertical

Seleccione si la barra de desplazamiento vertical muestra las siguientes anotaciones:

- trabajando
- marcas
- errores
- posición del símbolo de intercalación

> [!TIP]
> La opción **Mostrar marcas** incluye puntos de interrupción y marcadores.

Para probarla, abra un archivo de código largo y reemplace texto que aparezca en distintos lugares del archivo. La barra de desplazamiento muestra el efecto de los reemplazos, por lo que puede revertir los cambios si ha reemplazado algo que no debería haber reemplazado.

## <a name="behavior"></a>Comportamiento

La barra de desplazamiento tiene dos modos: el modo Barra y el modo Mapa.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Usar el modo Barra para la barra de desplazamiento vertical

El *modo Barra* muestra indicadores de anotación en la barra de desplazamiento. Al hacer clic en la barra de desplazamiento, se desplaza hacia arriba o hacia abajo de la página pero no salta a esa ubicación en el archivo.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Usar el modo Mapa para la barra de desplazamiento vertical

En el *modo Mapa*, cuando hace clic en una ubicación de la barra de desplazamiento, el cursor salta a esa ubicación en el archivo en lugar de solo desplazarse hacia arriba o hacia abajo de una página. En la barra desplazamiento se muestran líneas de código en miniatura. Puede elegir el ancho de la columna del mapa si selecciona un valor en **Información general del código fuente**. Para habilitar una vista previa más grande del código cuando deja el puntero en el mapa, seleccione la opción **Mostrar información sobre herramientas de la vista previa**. Las zonas contraídas están sombreadas de manera diferente y se expanden cuando se hace doble clic en ellas.

> [!TIP]
> Para desactivar la vista de código en miniatura en el mapa, establezca **Información general del código fuente** en **Off**. Si se selecciona **Mostrar información sobre herramientas de la vista previa**, seguirá viendo una vista previa del código en esa ubicación cuando mantenga el puntero del mouse sobre la barra de desplazamiento y el cursos seguirá saltando a esa ubicación en el archivo cuando se haga clic.

## <a name="see-also"></a>Vea también

- [Cómo: Personalizar la barra de desplazamiento](../how-to-track-your-code-by-customizing-the-scrollbar.md)