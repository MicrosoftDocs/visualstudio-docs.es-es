---
title: 'Cómo: buscar temas en la tabla de contenido | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer 2.0, table of contents filtering
- Help Viewer 2.0, Contents tab
- Contents tab [Help Viewer 2.0]
- table of contents filtering [Help Viewer 2.0]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4dccd82ea260c6d113ffaf077922c5e22946bbbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651887"
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Cómo: Buscar temas en la tabla de contenido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la pestaña **Contenido**, puede usar la tabla de contenido (TDC) para buscar información. La tabla de contenido es una lista ampliable que contiene todos los temas en los libros instalados. Para obtener información de accesibilidad sobre cómo navegar por la TDC, vea [Teclas de método abreviado (Visor de Ayuda)](../ide/shortcut-keys-help-viewer.md).

> [!IMPORTANT]
> El ámbito de temas disponibles en la TDC depende del filtro seleccionado.

## <a name="filter-the-toc"></a>Filtrar la TDC
 Puede filtrar la TDC para limitar el ámbito de los temas que aparecen en la pestaña **contenido** . los títulos aparecen en la lista solo si contienen la raíz del término que especifique. Por ejemplo, si especifica "solucionar" como un filtro, solo aparecerán los títulos que contengan "solucionar" o "solucionar problemas". Se contraen los nodos cuyos títulos no contienen el término en un único nodo con puntos suspensivos (...).

#### <a name="to-filter-the-toc"></a>Para filtrar la TDC

1. Elija la pestaña **Contenido**.

2. En el cuadro de texto **Filtrar contenido**, escriba un término.

> [!NOTE]
> Si el filtro tarda mucho tiempo en ejecutarse, puede mostrar resultados más rápidamente mediante el operador de búsqueda avanzada `title:`.

## <a name="synchronize-a-topic-with-the-toc"></a>Sincronizar un tema con la TDC
 Si abrió un tema mediante el índice o las características de búsqueda de texto completo, puede determinar dónde está este tema en la TDC sincronizándola con la ventana del tema.

#### <a name="to-synchronize-the-toc-with-the-topic-window"></a>Para sincronizar la TDC con la ventana del tema

1. Consulte un tema.

2. Haga clic en el botón **Mostrar tema en contenido** en la barra de herramientas o presione Ctrl+S.

     Se abre la pestaña **Contenido** y se muestra la ubicación del tema en la TDC.

## <a name="see-also"></a>Vea también
 [Buscar información](../ide/locate-information.md) [visor de ayuda de Microsoft](../ide/microsoft-help-viewer.md)
