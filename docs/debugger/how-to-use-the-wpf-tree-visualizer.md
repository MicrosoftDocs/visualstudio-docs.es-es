---
title: Uso del visualizador de árboles de WPF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ebe49365d5854a363b49ba0bde6431ae2121ebd
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851065"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Procedimiento Usar el visualizador de árboles de WPF
Puede usar el visualizador de árboles de WPF para explorar el árbol visual de un objeto de WPF y ver las propiedades de dependencia de WPF para los objetos contenidos en ese árbol. Para obtener más información sobre los árboles visuales, vea [Árboles en WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Para obtener más información sobre las propiedades de dependencia, vea [Introducción a las propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Al abrir el visualizador de árboles de WPF, verá dos paneles: el **Árbol visual** a la izquierda y las **Propiedades de** _Nombre_ **:** _Tipo_ a la derecha. Al seleccionar cualquier objeto en el panel **Árbol visual**, el panel **Propiedades de** _Nombre_ **:** _Tipo_ se actualizará automáticamente para mostrar las propiedades de dicho objeto.

 > [!NOTE]
 > También puede usar el [árbol visual dinámico y el explorador de propiedades dinámicas](../xaml-tools/inspect-xaml-properties-while-debugging.md) para examinar el árbol visual de los objetos WPF. El visualizador de árboles de WPF es una característica heredada y no está en desarrollo activo.

### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir el visualizador de árboles de WPF

1. En una Información sobre datos, una ventana **Inspección**, una ventana **Automático** o una ventana **Variables locales**, junto al nombre de un objeto WPF, haga clic en la flecha adyacente al icono de lupa.

     Se mostrará una lista de visualizadores.

2. Haga clic en **Visualizador de árboles de WPF**.

### <a name="to-search-the-visual-tree"></a>Para buscar en el árbol visual

- En el panel **Árbol visual**, escriba la cadena que desea buscar en el cuadro **Buscar**.

  El visualizador de árboles de WPF buscará inmediatamente el primer objeto del árbol visual que coincida con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.

  - Para ir a la siguiente coincidencia dentro del árbol visual, haga clic en **Siguiente**.

  - Para volver a la coincidencia anterior, haga clic en **Anterior**.

  - Para borrar el criterio de búsqueda, haga clic en **Borrar**.

### <a name="to-search-the-properties-list"></a>Para buscar en la lista de propiedades

- En el panel **Propiedades de** _Nombre_ **:** _Tipo_, escriba la cadena que desea buscar en el cuadro **Filtro**.

  El visualizador de árboles de WPF buscará inmediatamente las propiedades que coincidan con la cadena que ha escrito; ahora, la lista solo muestra las propiedades que coinciden con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.

  - Para borrar el criterio de búsqueda, haga clic en **Borrar**.

### <a name="to-close-the-visualizer"></a>Para cerrar el visualizador

- Haga clic en el icono **Cerrar** situado en la esquina superior derecha del cuadro de diálogo.

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Árboles en WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Información general sobre las propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview)
