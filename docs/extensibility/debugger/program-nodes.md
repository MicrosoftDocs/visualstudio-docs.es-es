---
title: Nodos de programa | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50ab93c31a340bf8a2f4e2deb5f202707d7826b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="program-nodes"></a>Nodos de programa
En cuanto a la arquitectura del depurador, una **nodo programa**:  
  
-   Es una descripción de un programa ligera.  
  
-   Puede identificar propio y el proceso se está ejecutando y puede adjuntarse, se separa de y describir el motor de depuración (Alemania) que creó, si lo hay.  
  
-   Se representa mediante un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz, normalmente se crea un puerto o Alemania. Nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que representa este nodo de programa.  
  
 En algún momento después de que se haya iniciado una sesión de depuración, dependiendo de la implementación del paquete de depuración, nodos de programa se utilizan para crear programas correspondientes. Cuando un proceso se consulta de sus programas, se enumeran los programas, uno para cada nodo del programa.  
  
 Antes de que un programa que está asociado a, el IDE tiene solo una ligera descripción del programa. Puede obtener esta información desde el nodo de programa. Una vez que el programa que está asociado a, el IDE se necesita para mostrar información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene desde el propio programa.  
  
## <a name="see-also"></a>Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Procesos](../../extensibility/debugger/processes.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)