---
title: Nodos de programa | Microsoft Docs
description: En este artículo se describe la definición y el rol de un nodo de programa en la arquitectura del depurador Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c26fa95a5fedf325591ce517e7c12ecebcd705c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899087"
---
# <a name="program-nodes"></a>Nodos de programa
En la arquitectura del depurador, un *nodo de programa*:

- Es una descripción ligera de un programa.

- Puede identificarse a sí mismo y al proceso en el que se está ejecutando. Un nodo de programa se puede adjuntar, desasociar y describir el motor de depuración (DE) que lo creó, si lo hubiera.

- Se representa mediante una [interfaz IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) normalmente creada por un puerto DE o . Los nodos de programa se agregan a un puerto mediante una [llamada a AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que representa este nodo de programa.

  En algún momento después de iniciarse una sesión de depuración, en función de la implementación del paquete de depuración, los nodos de programa se usan para crear los programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo de programa.

  Antes de adjuntar un programa, el IDE solo necesita una descripción ligera del programa. Esta información se puede obtener del nodo del programa. Una vez asociado el programa, el IDE muestra información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene del propio programa.

## <a name="see-also"></a>Consulta también
- [Programs](../../extensibility/debugger/programs.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
