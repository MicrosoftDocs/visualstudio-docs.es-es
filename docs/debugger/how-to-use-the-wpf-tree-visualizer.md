---
title: "Cómo: usar el visualizador de árboles WPF | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e30d1fbd8cd23a514d1036bc43c809626c665d73
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Cómo: Usar el visualizador de árboles de WPF
Puede usar el visualizador de árboles de WPF para explorar el árbol visual de un objeto de WPF y ver las propiedades de dependencia de WPF para los objetos contenidos en ese árbol. Para obtener más información sobre los árboles visuales, vea [árboles de WPF](/dotnet/framework/wpf/advanced/trees-in-wpf). Para obtener más información acerca de las propiedades de dependencia, vea [información general sobre propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview).  
  
 Al abrir el visualizador de árboles de WPF, verá dos paneles: el **árbol Visual** a la izquierda y la **propiedades de** *nombre***:**  *Tipo de* panel de la derecha. Seleccione cualquier objeto en el **árbol Visual** panel y el **propiedades de** *nombre***:***tipo* panel es se actualiza automáticamente para mostrar las propiedades de ese objeto.  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>Para abrir el visualizador de árboles de WPF  
  
1.  En una información sobre datos, **inspección** ventana, **automático** ventana, o **locales** ventana, junto a un nombre de objeto WPF, haga clic en la flecha situada junto al icono de lupa.  
  
     Se mostrará una lista de visualizadores.  
  
2.  Haga clic en **visualizador de árboles WPF**.  
  
### <a name="to-search-the-visual-tree"></a>Para buscar en el árbol visual  
  
-   En el **árbol Visual** panel, escriba la cadena que desea buscar en el **búsqueda** cuadro.  
  
     El visualizador de árboles de WPF buscará inmediatamente el primer objeto del árbol visual que coincida con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.  
  
    -   Para ir a la siguiente coincidencia dentro del árbol visual, haga clic en **siguiente**.  
  
    -   Para volver a la coincidencia anterior, haga clic en **Prev**.  
  
    -   Para borrar los criterios de búsqueda, haga clic en **borrar**.  
  
### <a name="to-search-the-properties-list"></a>Para buscar en la lista de propiedades  
  
-   En el **propiedades de** *nombre***:***tipo* panel, escriba la cadena de la que desea buscar en el **filtrar**cuadro.  
  
     El visualizador de árboles de WPF buscará inmediatamente las propiedades que coincidan con la cadena que ha escrito; ahora, la lista solo muestra las propiedades que coinciden con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.  
  
    -   Para borrar los criterios de búsqueda, haga clic en **borrar**.  
  
### <a name="to-close-the-visualizer"></a>Para cerrar el visualizador  
  
-   Haga clic en el **cerrar** icono en la esquina superior derecha del cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Crear los visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Árboles en WPF](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [Información general sobre las propiedades de dependencia](/dotnet/framework/wpf/advanced/dependency-properties-overview)