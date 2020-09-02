---
title: Nodos de programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153657"
---
# <a name="program-nodes"></a>Nodos de programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura del depurador, un **nodo de programa**:  
  
- Es una descripción ligera de un programa.  
  
- Puede identificarse y el proceso en el que se ejecuta, y se puede adjuntar, desasociar y describir el motor de depuración (DE) que lo creó, si existe.  
  
- Se representa mediante una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , creada normalmente por un puerto de o. Los nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que este nodo de programa representa.  
  
  Una vez que se inicia una sesión de depuración, dependiendo de la implementación del paquete de depuración, los nodos de programa se utilizan para crear los programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo de programa.  
  
  Antes de asociar un programa a, el IDE solo necesita una descripción ligera del programa. Esta información se puede obtener del nodo del programa. Una vez que el programa está asociado, el IDE debe mostrar información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene del propio programa.  
  
## <a name="see-also"></a>Consulte también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Procese](../../extensibility/debugger/processes.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
