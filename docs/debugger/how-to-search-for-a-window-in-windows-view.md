---
title: "Cómo: buscar una ventana en la vista ventanas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dfec3f78e9f95a55d453c45c5a264125152cbf1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>Cómo: Buscar una ventana en la vista Ventanas
Puede buscar una ventana concreta en la vista ventanas mediante su identificador, título, clase o una combinación de su título y clase como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrará los atributos de la ventana seleccionada en el árbol de la ventana.  
  
 Empiece con el árbol expandido en el segundo nivel (todas las ventanas que son elementos secundarios del escritorio), para que pueda identificar ventanas del nivel del escritorio por su nombre de clase y el título. Una vez que haya elegido una ventana de nivel de escritorio, puede expandir ese nivel para buscar una ventana secundaria concreta.  
  
### <a name="to-search-for-a-window-in-windows-view"></a>Para buscar una ventana en la vista ventanas  
  
1.  Organizar las ventanas de modo que ese Spy ++, la [Windows Vista](../debugger/windows-view.md) ventana y la ventana de destino son visibles.  
  
2.  Desde el **búsqueda** menú, elija **Buscar ventana**.  
  
     El [cuadro de diálogo Buscar ventana](../debugger/window-search-dialog-box.md) se abre.  
  
    > [!TIP]
    >  Para reducir la acumulación de elementos de pantalla, seleccione la **Ocultar Spy** opción. Esta opción oculta la ventana principal de Spy ++ y deja solo el **ventana búsqueda** cuadro de diálogo visible encima de las otras aplicaciones. La ventana principal de Spy ++ se restaura al hacer clic en **Aceptar** o **cancelar**, o cuando se borra el **Ocultar Spy ++** opción.  
  
3.  Arrastre el **herramienta de búsqueda** sobre la ventana de destino. A medida que arrastra la herramienta, el **ventana búsqueda** cuadro de diálogo muestra los detalles de la ventana seleccionada.  
  
     - O  
  
     Si conoce el identificador de la ventana que desee (por ejemplo, desde el depurador), puede escribirla en el **controlar** cuadro.  
  
     - O  
  
     Si conoce el título o una clase de la ventana que desea, puede escribir en el **título** y **clase** cuadros de texto y desactive el **controlar** cuadro de texto.  
  
4.  Elija **una** o **hacia abajo** para la dirección inicial de la búsqueda.  
  
5.  Haga clic en **Aceptar**.  
  
     Si se encuentra una ventana coincidente, se resalta en el [Windows Vista](../debugger/windows-view.md) ventana.