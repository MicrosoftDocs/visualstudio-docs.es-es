---
title: Nodos de programa ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738221"
---
# <a name="program-nodes"></a>Nodos de programa
En la arquitectura del depurador, un nodo de *programa:*

- Es una descripción ligera de un programa.

- Puede identificarse a sí mismo y el proceso en el que se está ejecutando. Un nodo de programa se puede asociar, separar y describir el motor de depuración (DE) que lo creó, si existe.

- Se representa mediante un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz, normalmente creado por un DE o puerto. Los nodos de programa se agregan a un puerto llamando a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que representa este nodo de programa.

  En algún momento después de iniciar una sesión de depuración, dependiendo de la implementación del paquete de depuración, los nodos del programa se utilizan para crear los programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo de programa.

  Antes de adjuntar un programa, el IDE solo necesita una descripción ligera del programa. Esta información se puede obtener del nodo del programa. Una vez que se adjunta el programa, el IDE muestra información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene del propio programa.

## <a name="see-also"></a>Vea también
- [Programs](../../extensibility/debugger/programs.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
