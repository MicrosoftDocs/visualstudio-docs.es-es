---
title: 'Cómo: buscar un proceso en la vista procesos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d23199031ce46e57e44a01720493fad4e77c7430
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Cómo: Buscar un proceso en la vista Procesos
Puede buscar un proceso específico en la vista procesos mediante su cadena de identificador o el módulo de proceso como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrarán los atributos del proceso seleccionado en el árbol de procesos.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Para buscar un proceso en la vista procesos  
  
1.  Organizar las ventanas de modo que ese Spy ++ y cuando se activa [vista procesos](../debugger/processes-view.md) ventana están visibles.  
  
2.  Desde el **búsqueda** menú, elija **Buscar proceso**  
  
     El [cuadro de diálogo Buscar proceso](../debugger/process-search-dialog-box.md) se abre.  
  
3.  Escriba el identificador de proceso o una cadena de módulo como criterio de búsqueda.  
  
4.  Desactive los campos para los que no desea especificar los valores.  
  
    > [!TIP]
    >  Para buscar todos los procesos que pertenecen a un módulo, borre el **proceso** cuadro y escriba el nombre del módulo en el **módulo** cuadro. A continuación, utilice **Buscar siguiente** para continuar la búsqueda para los procesos.  
  
5.  Elija **una** o **hacia abajo** para la dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un proceso coincidente, se resalta en el **vista proceso** ventana.