---
title: Vista procesos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8b9c04d1cabd44418c70725ef331c9c4b5ec67e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997681"
---
# <a name="processes-view"></a>Vista Procesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La vista procesos muestra un árbol de todos los procesos activos en el sistema. Se muestran el nombre de identificador y el módulo de proceso. Utilice la vista procesos si desea examinar un proceso del sistema, que normalmente corresponde a un programa en ejecución. Los procesos se identifican por nombres de módulo, o se designan "procesos del sistema".  
  
 Microsoft Windows admite varios procesos. Cada proceso puede tener uno o varios subprocesos y cada subproceso puede tener uno o más ventanas de nivel superior de asociadas. Cada ventana de nivel superior puede poseer una serie de windows. Un símbolo + indica que un nivel está contraído. La vista contraída consta de una línea por proceso. Haga clic en el signo + para expandir el nivel.  
  
 Utilice la vista procesos si desea examinar un proceso del sistema, que normalmente corresponde a un programa en ejecución. Los procesos se identifican por nombres de módulo, o se designan "procesos del sistema". Para buscar un proceso, contraer el árbol y busque en la lista.  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-open-the-processes-view"></a>Para abrir la vista procesos  
  
1. Desde el **Spy** menú, elija **procesos**.  
  
   ![Spy&#43; &#43; vista procesos](../debugger/media/spy-processes.png "Spy ++ _Processes")  
   Vista de procesos de Spy++  
  
   La ilustración anterior muestra la vista procesos con los nodos de proceso y subproceso expandidos.  
  
### <a name="in-this-section"></a>En esta sección  
 [Buscar un proceso en la vista procesos](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Explica cómo buscar un proceso específico en la vista procesos.  
  
 [Mostrar propiedades del proceso](../debugger/how-to-display-process-properties.md)  
 Explica cómo mostrar más información acerca de un mensaje.  
  
### <a name="related-sections"></a>Secciones relacionadas  
 [Vistas de Spy++](../debugger/spy-increment-views.md)  
 Explica las vistas de árbol de Spy ++ de windows, los mensajes, los procesos y subprocesos.  
  
 [Usar Spy++](../debugger/using-spy-increment.md)  
 Presenta la herramienta Spy ++ y explica cómo se puede usar.  
  
 [Cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md)  
 Se usa para encontrar el nodo de un proceso específico en la vista procesos.  
  
 [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md)  
 Muestra las propiedades de un proceso seleccionado en la vista procesos.  
  
 [Referencia de Spy++](../debugger/spy-increment-reference.md)  
 Incluye secciones que describen cada Spy ++ menú y cuadro de diálogo.
