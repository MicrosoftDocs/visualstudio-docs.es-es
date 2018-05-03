---
title: Uso de la tabla de contenido del Visor de Ayuda de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/02/2017
ms.technology:
- vs-help-viewer
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db53125c30a2136500b6c99818b7143511bd2788
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Cómo: Buscar temas en la tabla de contenido
En la pestaña **Contenido**, puede usar la tabla de contenido (TDC) para buscar información. La tabla de contenido es una lista ampliable que contiene todos los temas en los libros instalados. Para obtener información de accesibilidad sobre cómo navegar por la TDC, vea [Teclas de método abreviado (Visor de Ayuda)](../ide/shortcut-keys-help-viewer.md).  
  
> [!IMPORTANT]
>  El ámbito de temas disponibles en la TDC depende del filtro seleccionado.  
  
## <a name="filter-the-toc"></a>Filtrar la TDC  
Puede filtrar la TDC para limitar el ámbito de temas que aparecen en la pestaña **Contenido**. Los títulos se muestran en la lista solo si contienen la raíz del término que especifique. Por ejemplo, si especifica "solucionar" como un filtro, solo aparecerán los títulos que contengan "solucionar" o "solucionar problemas". Los nodos cuyos títulos no contienen el término se contraen en un único nodo con puntos suspensivos (**...**).  
  
#### <a name="to-filter-the-toc"></a>Para filtrar la TDC  
  
1.  Elija la pestaña **Contenido**.  
  
2.  En el cuadro de texto **Filtrar contenido**, escriba un término.  
  
> [!NOTE]
>  Si el filtro tarda mucho tiempo en ejecutarse, puede mostrar resultados más rápidamente mediante el operador de búsqueda avanzada `title:`.  
  
## <a name="synchronize-a-topic-with-the-toc"></a>Sincronizar un tema con la TDC  
Si abrió un tema mediante el índice o las características de búsqueda de texto completo, puede determinar dónde está este tema en la TDC sincronizándola con la ventana del tema.
  
#### <a name="to-synchronize-the-toc-with-the-topic-window"></a>Para sincronizar la TDC con la ventana del tema  
  
1.  Consulte un tema.  
  
2.  Haga clic en el botón **Mostrar tema en contenido** en la barra de herramientas o presione **Ctrl**+**S**.  
  
     Se abre la pestaña **Contenido** y se muestra la ubicación del tema en la TDC.  
  
## <a name="see-also"></a>Vea también
[Cómo: Buscar temas en el índice](../ide/how-to-find-topics-in-the-index.md)  
[Cómo: Buscar temas](../ide/how-to-search-for-topics.md)  
[Visor de Ayuda de Microsoft](../ide/microsoft-help-viewer.md)