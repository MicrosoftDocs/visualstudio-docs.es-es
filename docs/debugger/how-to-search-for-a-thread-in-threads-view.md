---
title: 'Cómo: buscar un subproceso en la vista de subprocesos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d582a10e2738b69724765477ee64c47e8cb68c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Cómo: Buscar un subproceso en la vista de subprocesos
Puede buscar un subproceso concreto en la vista de subprocesos mediante el uso de la cadena de identificador o el módulo de subproceso como criterio de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrarán los atributos del subproceso seleccionado en el árbol de subproceso.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para buscar un subproceso en la vista de subprocesos  
  
1.  Organizar las ventanas de modo que ese Spy ++ y cuando se activa [vista de subprocesos](../debugger/threads-view.md) ventana están visibles.  
  
2.  Desde el **búsqueda** menú, elija **Buscar subproceso**.  
  
     El [cuadro de diálogo Buscar subproceso](../debugger/thread-search-dialog-box.md) se abre.  
  
3.  Escriba el identificador del subproceso o una cadena de módulo como criterio de búsqueda.  
  
4.  Desactive los campos para los que no desea especificar los valores.  
  
    > [!TIP]
    >  Para buscar todos los subprocesos que pertenecen a un módulo, borre el **subprocesos** nombre de cuadro de texto y el tipo del módulo en el **módulo** cuadro. A continuación, utilice **Buscar siguiente** para continuar la búsqueda para los subprocesos.  
  
5.  Elija **una** o **hacia abajo** para la dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un subproceso coincidente, se resalta en la ventana de vista de subprocesos.