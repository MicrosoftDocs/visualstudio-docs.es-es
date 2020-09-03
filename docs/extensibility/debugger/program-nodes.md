---
title: Nodos de programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738221"
---
# <a name="program-nodes"></a>Nodos de programa
En la arquitectura del depurador, un *nodo de programa*:

- Es una descripción ligera de un programa.

- Puede identificarse y el proceso en el que se está ejecutando. Un nodo de programa se puede adjuntar a, desasociar de y describir el motor de depuración (DE) que lo creó, si existe.

- Se representa mediante una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , creada normalmente por un puerto de o. Los nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que este nodo de programa representa.

  Una vez que se inicia una sesión de depuración, dependiendo de la implementación del paquete de depuración, los nodos de programa se utilizan para crear los programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo de programa.

  Antes de asociar un programa a, el IDE solo necesita una descripción ligera del programa. Esta información se puede obtener del nodo del programa. Una vez que el programa está asociado, el IDE muestra información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene del propio programa.

## <a name="see-also"></a>Vea también
- [Programs](../../extensibility/debugger/programs.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
