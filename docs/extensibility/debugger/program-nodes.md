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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 084a386cc7d7f9c6d606e7015e593a4075ba53a9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351426"
---
# <a name="program-nodes"></a>Nodos de programa
En la arquitectura de depurador, un *nodo programa*:

- Es una descripción de un programa ligera.

- Puede identificar el propio y el proceso que se está ejecutando. Un nodo del programa se puede conectar, se separa de y describir el motor de depuración (DE) que creó, si existe.

- Se representa mediante un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) suelen creada un puerto o DE interfaz. Nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que representa este nodo del programa.

  Después de que se inicia una sesión de depuración, dependiendo de la implementación del paquete de depuración, nodos de programa se utilizan para crear programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo del programa.

  Antes de que un programa está conectado a, el IDE necesita sólo una ligera descripción del programa. Esta información puede obtenerse desde el nodo del programa. Una vez que el programa está asociado a, el IDE muestra información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene desde el propio programa.

## <a name="see-also"></a>Vea también
- [Programas](../../extensibility/debugger/programs.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)