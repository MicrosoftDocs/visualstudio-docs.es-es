---
title: Procedimiento Búsqueda de un subproceso en la vista Subprocesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838481"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Procedimiento Búsqueda de un subproceso en la vista Subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para buscar un subproceso específico en la vista Subprocesos, utilice su id. de subproceso o cadena de módulo como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. En los campos del cuadro de diálogo se mostrarán los atributos del subproceso seleccionado en el árbol de subprocesos.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para buscar un subproceso en la vista Subprocesos  
  
1. Organice las ventanas para que se vean la ventana de Spy++ y una ventana activa de la [vista Subprocesos](../debugger/threads-view.md).  
  
2. En el menú **Buscar**, seleccione **Buscar subproceso**.  
  
    Se abrirá el [cuadro de diálogo Buscar subproceso](../debugger/thread-search-dialog-box.md).  
  
3. Escriba el id. de subproceso o una cadena de módulo como criterios de búsqueda.  
  
4. Borre los campos en los que no quiera especificar ningún valor.  
  
   > [!TIP]
   > Para buscar todos los subprocesos que pertenecen a un módulo, desactive el cuadro de texto **Subproceso** y escriba el nombre del módulo en el cuadro **Módulo**. A continuación, use **Buscar siguiente** para seguir buscando subprocesos.  
  
5. Seleccione **Arriba** o **Abajo** para determinar la dirección inicial de la búsqueda.  
  
6. Haga clic en **Aceptar**.  
  
   Si se encuentra un subproceso coincidente, se resaltará en la ventana de la vista Ventanas.
