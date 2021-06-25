---
title: Programas | Microsoft Docs
description: En este artículo se describe la definición y el rol de un programa en la arquitectura del depurador en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 07b23fbafd9342b555e2578c4bc0401371e30785
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901284"
---
# <a name="programs"></a>Programas
En la arquitectura del depurador, un *programa*:

- Es un contenedor para un conjunto de subprocesos y un conjunto de módulos. Un programa no tiene ninguna analogía única en el sistema operativo Windows.

     Un programa es un tipo de subproceso. Por ejemplo, al depurar un sitio web, un script se puede ver como un programa. Mientras que un script se ejecuta en el proceso del motor de scripting, independientemente de otros scripts, también tiene su propio conjunto de subprocesos. Un motor de depuración (DE) se asocia a un programa y no a un proceso o un subproceso.

- Puede identificarse a sí mismo y al proceso en el que se ejecuta. Un programa se puede adjuntar, desasociar y describir el DE que lo creó, si lo hubiera. Un programa también puede ejecutar, detener, continuar y finalizar.

- Puede enumerar todos sus subprocesos. Un programa también puede proporcionar su propia secuencia de desensamblado y puede enumerar todos los contextos de código de una posición de documento determinada.

- Se representa mediante una [interfaz IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) creada antes de adjuntar el programa, o como parte del proceso de asociación, según la implementación. Cuando un puerto enumera los programas de un proceso, cada programa se crea de acuerdo con una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondiente pasada como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aunque los motores de depuración también crean `IDebugProgram2` interfaces para representar programas, estos programas no se crean de acuerdo con un nodo de programa. Las interfaces creadas por un DE se usan para la depuración real, mientras que las creadas por un puerto solo se usan para detectar qué programas se ejecutan `IDebugProgramNode2` en un proceso.

## <a name="see-also"></a>Consulta también
- [Procesos](../../extensibility/debugger/processes.md)
- [Nodos de programa](../../extensibility/debugger/program-nodes.md)
- [Módulos](../../extensibility/debugger/modules.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Posición del documento](../../extensibility/debugger/document-position.md)
- [Contexto de código](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
