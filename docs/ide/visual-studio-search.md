---
title: Uso de la búsqueda de Visual Studio
description: Aprenda a usar la búsqueda de Visual Studio para buscar opciones, menús y código.
ms.date: 10/08/2020
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.QuickLaunch
- IDE navigator
ms.assetid: 3870a8fd-4afa-4f1e-a811-9fdf41a9e82d
monikerRange: vs-2019
author: profexorgeek
ms.author: jusjohns
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9f8182646af4facb0f2f86c74f95dff091d55d1
ms.sourcegitcommit: cea9e5787ff33e0e18aa1942bf4236748e0ef547
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199711"
---
# <a name="use-visual-studio-search"></a>Uso de la búsqueda de Visual Studio

El entorno de desarrollo integrado (IDE) de Visual Studio tiene muchos menús, opciones y características que pueden ser difíciles de recordar. La característica de búsqueda de Visual Studio es un cuadro de búsqueda único que ayuda a los desarrolladores a buscar opciones y menús del IDE, y que también busca en el código. Tanto si no está familiarizado con Visual Studio como si es un desarrollador experimentado, esta característica le ofrece una manera rápida de buscar en las características del IDE y en el código.

Use el método abreviado de teclado **Ctrl**+**Q** para acceder al cuadro de búsqueda o haga clic en el cuadro de entrada de búsqueda de Visual Studio situado junto a la barra de menús de forma predeterminada:

:::image type="content" source="media/visual-studio-search-cropped.png" alt-text="Cuadro de búsqueda de Visual Studio" lightbox="media/visual-studio-search.png":::

> [!NOTE]
> El comando que ejecuta la búsqueda de Visual Studio es `Window.QuickLaunch`, y puede que vea que esta característica se conoce como búsqueda rápida o inicio rápido.

A diferencia de otras características de búsqueda, como Buscar en archivos o Buscar en el Explorador de soluciones, los resultados de la búsqueda de Visual Studio incluyen características del IDE, opciones de menú, nombres de archivo, etc. En las secciones siguientes se habla de los distintos tipos de resultados que puede encontrar la búsqueda de Visual Studio.

## <a name="search-menus-options-and-windows"></a>Búsqueda en menús, opciones y ventanas

Puede usar el cuadro de búsqueda de Visual Studio para buscar valores, opciones y elementos de configuración similares. Por ejemplo, busque *cambiar tema* para buscar y abrir rápidamente el cuadro de diálogo que permite cambiar el tema de color de Visual Studio, como se muestra en la siguiente captura de pantalla:

:::image type="content" source="media/visual-studio-search-options.png" alt-text="Cuadro de búsqueda de Visual Studio":::

> [!TIP]
> En la mayoría de los casos, la búsqueda de Visual Studio también va a recordarle el menú, las teclas de método abreviado y la ubicación de cada elemento de los resultados.

Puede usar el cuadro de búsqueda de Visual Studio para buscar elementos de menú y comandos. Por ejemplo, busque *limpiar sol* para buscar y ejecutar rápidamente el comando Limpiar solución. Los resultados de la búsqueda también ofrecen un recordatorio de dónde encontrar este comando en los menús, como se muestra en la siguiente captura de pantalla:

:::image type="content" source="media/visual-studio-search-menu.png" alt-text="Cuadro de búsqueda de Visual Studio":::

Por último, puede buscar ventanas o paneles que pueda haber cerrado accidentalmente. Por ejemplo, busque *prueba* para buscar y abrir la ventana Explorador de pruebas:

:::image type="content" source="media/visual-studio-search-window.png" alt-text="Cuadro de búsqueda de Visual Studio":::

## <a name="search-files-and-code"></a>Búsqueda en archivos y código

La búsqueda de Visual Studio también busca en los elementos de la solución por nombre de archivo, código, método y otras coincidencias. En la captura de pantalla siguiente, una búsqueda de *markdown* ha encontrado el archivo MarkdownMetaExtractor.cs, la clase `MarkdownMetaExtractor` y dos métodos dentro de la solución:

:::image type="content" source="media/visual-studio-search-files.png" alt-text="Cuadro de búsqueda de Visual Studio":::

También puede realizar una búsqueda de mayúsculas y minúsculas combinadas. En la siguiente captura de pantalla, una búsqueda de *FSS* ha encontrado un archivo **F** older **S** ize **S** canner, una clase y un método:

:::image type="content" source="media/visual-studio-search-camel.png" alt-text="Cuadro de búsqueda de Visual Studio":::

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](reference/visual-studio-commands.md)