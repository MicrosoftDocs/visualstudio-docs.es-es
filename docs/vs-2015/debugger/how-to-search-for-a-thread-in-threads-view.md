---
title: 'Cómo: buscar un subproceso en la vista subprocesos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 071b32a6f8947289d12ad8a402a316b1d174f65f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581607"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Cómo: Buscar un subproceso en la vista de subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: buscar un subproceso en la vista subprocesos](https://docs.microsoft.com/visualstudio/debugger/how-to-search-for-a-thread-in-threads-view).  
  
Puede buscar un subproceso concreto en la vista de subprocesos mediante el uso de su cadena de identificador o el módulo del subproceso como criterios de búsqueda. También puede especificar la dirección inicial de la búsqueda. Los campos en el cuadro de diálogo mostrará los atributos del subproceso seleccionado en el árbol de subproceso.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Para buscar un subproceso en la vista de subprocesos  
  
1.  Organizar las ventanas por lo que ese Spy ++ y un activo [vista de subprocesos](../debugger/threads-view.md) ventana están visibles.  
  
2.  Desde el **búsqueda** menú, elija **Buscar subproceso**.  
  
     El [cuadro de diálogo Buscar subproceso](../debugger/thread-search-dialog-box.md) se abre.  
  
3.  Escriba el identificador de subproceso o una cadena de módulo como criterios de búsqueda.  
  
4.  Borrar todos los campos que no desea especificar los valores.  
  
    > [!TIP]
    >  Para buscar todos los subprocesos que pertenecen a un módulo, desactive la **subprocesos** nombre de cuadro de texto y el tipo del módulo en el **módulo** cuadro. A continuación, usar **Buscar siguiente** para continuar la búsqueda de subprocesos.  
  
5.  Elija **seguridad** o **abajo** para la dirección inicial de la búsqueda.  
  
6.  Haga clic en **Aceptar**.  
  
 Si se encuentra un subproceso coincidente, éste se resalta en la ventana de vista de subprocesos.



