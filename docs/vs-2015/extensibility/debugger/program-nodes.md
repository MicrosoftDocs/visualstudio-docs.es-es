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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153657"
---
# <a name="program-nodes"></a>Nodos de programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **nodo programa**:  
  
- Es una descripción de un programa ligera.  
  
- Puede identificar a sí mismo y el proceso se ejecuta en y se puede adjuntar, se separa de y describir el motor de depuración (DE) que creó, si existe.  
  
- Se representa mediante un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) suelen creada un puerto o DE interfaz. Nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que representa este nodo del programa.  
  
  Después de que se inicia una sesión de depuración, dependiendo de la implementación del paquete de depuración, nodos de programa se utilizan para crear programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo del programa.  
  
  Antes de que un programa está conectado a, el IDE necesita sólo una ligera descripción del programa. Esta información puede obtenerse desde el nodo del programa. Una vez que el programa está asociado a, el IDE se necesita para mostrar información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene desde el propio programa.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
