---
title: Nodos de programa | Microsoft Docs
description: En este artículo se describe la definición y el rol de un nodo de programa en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 5658026b60006a58ba168ca713028b9876a3c57d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094632"
---
# <a name="program-nodes"></a>Nodos de programa
En la arquitectura del depurador, un *nodo de programa*:

- Es una descripción ligera de un programa.

- Puede identificarse y el proceso en el que se está ejecutando. Un nodo de programa se puede adjuntar a, desasociar de y describir el motor de depuración (DE) que lo creó, si existe.

- Se representa mediante una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , creada normalmente por un puerto de o. Los nodos de programa se agregan a un puerto mediante una llamada a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Cuando se agrega un nodo de programa a un puerto, se agrega al proceso que contiene el programa que este nodo de programa representa.

  Una vez que se inicia una sesión de depuración, dependiendo de la implementación del paquete de depuración, los nodos de programa se utilizan para crear los programas correspondientes. Cuando se consulta un proceso para sus programas, se enumeran los programas, uno para cada nodo de programa.

  Antes de asociar un programa a, el IDE solo necesita una descripción ligera del programa. Esta información se puede obtener del nodo del programa. Una vez que el programa está asociado, el IDE muestra información más detallada, como una lista de todos los subprocesos que se ejecutan en el programa. Esta información se obtiene del propio programa.

## <a name="see-also"></a>Consulte también
- [Programs](../../extensibility/debugger/programs.md)
- [Procesos](../../extensibility/debugger/processes.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
