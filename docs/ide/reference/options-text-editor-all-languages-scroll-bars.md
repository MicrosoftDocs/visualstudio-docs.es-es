---
title: Opciones, Editor de texto, Todos los idiomas, Barras de desplazamiento
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a753574e883872780446929f7c2349b0d726c71a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817589"
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

- cambios
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