---
title: 'Cómo: usar el visualizador de árboles WPF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7276690152e74599df6183cf602aca518e3b944f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685332"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Cómo: Usar el visualizador de árboles de WPF
Puede usar el visualizador de árboles de WPF para explorar el árbol visual de un objeto de WPF y ver las propiedades de dependencia de WPF para los objetos contenidos en ese árbol. Para obtener más información sobre los árboles visuales, vea [árboles en WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Para obtener más información acerca de las propiedades de dependencia, consulte [información general sobre las propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview).

 Al abrir el visualizador de árboles de WPF, verá dos paneles: el **árbol Visual** a la izquierda y la **propiedades de** _nombre_**:**  _Tipo_ panel de la derecha. Seleccione cualquier objeto en el **árbol Visual** panel y el **propiedades de** _nombre_**:**_tipo_ panel es actualiza automáticamente para mostrar las propiedades de ese objeto.

### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir el visualizador de árboles de WPF

1.  En una Información sobre datos, una ventana **Inspección**, una ventana **Automático** o una ventana **Variables locales**, junto al nombre de un objeto WPF, haga clic en la flecha adyacente al icono de lupa.

     Se mostrará una lista de visualizadores.

2.  Haga clic en **Visualizador de árboles de WPF**.

### <a name="to-search-the-visual-tree"></a>Para buscar en el árbol visual

-   En el panel **Árbol visual**, escriba la cadena que desea buscar en el cuadro **Buscar**.

     El visualizador de árboles de WPF buscará inmediatamente el primer objeto del árbol visual que coincida con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.

    -   Para ir a la siguiente coincidencia dentro del árbol visual, haga clic en **Siguiente**.

    -   Para volver a la coincidencia anterior, haga clic en **Anterior**.

    -   Para borrar el criterio de búsqueda, haga clic en **Borrar**.

### <a name="to-search-the-properties-list"></a>Para buscar en la lista de propiedades

-   En el **propiedades de** _nombre_**:**_tipo_ panel, escriba la cadena que desea buscar en el **filtrar**cuadro.

     El visualizador de árboles de WPF buscará inmediatamente las propiedades que coincidan con la cadena que ha escrito; ahora, la lista solo muestra las propiedades que coinciden con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.

    -   Para borrar el criterio de búsqueda, haga clic en **Borrar**.

### <a name="to-close-the-visualizer"></a>Para cerrar el visualizador

-   Haga clic en el icono **Cerrar** situado en la esquina superior derecha del cuadro de diálogo.

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Árboles en WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)
- [Información general sobre las propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview)
