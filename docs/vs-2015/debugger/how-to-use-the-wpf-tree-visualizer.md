---
title: Filtrar Usar el visualizador de árboles WPF | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6d2fc99235c9001cd465236c82588e33a842c168
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998534"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>Filtrar Usar el visualizador de árboles de WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el visualizador de árboles de WPF para explorar el árbol visual de un objeto de WPF y ver las propiedades de dependencia de WPF para los objetos contenidos en ese árbol. Para obtener más información sobre los árboles visuales, vea [árboles en WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649). Para obtener más información acerca de las propiedades de dependencia, consulte [información general sobre las propiedades de dependencia](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5).  
  
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
  
-   En el **propiedades de** _nombre_**:**_tipo_ panel, escriba la cadena de la que desea buscar en el **filtrar**cuadro.  
  
     El visualizador de árboles de WPF buscará inmediatamente las propiedades que coincidan con la cadena que ha escrito; ahora, la lista solo muestra las propiedades que coinciden con la cadena que ha escrito. Escriba más caracteres si desea buscar una coincidencia más precisa.  
  
    -   Para borrar el criterio de búsqueda, haga clic en **Borrar**.  
  
### <a name="to-close-the-visualizer"></a>Para cerrar el visualizador  
  
-   Haga clic en el icono **Cerrar** situado en la esquina superior derecha del cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Utilizar un visualizador](../misc/how-to-use-a-visualizer.md)   
 [Creación de visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)   
 [Árboles en WPF](http://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [Información general sobre las propiedades de dependencia](http://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
