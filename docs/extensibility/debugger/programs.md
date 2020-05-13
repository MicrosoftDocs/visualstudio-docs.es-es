---
title: Programas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738209"
---
# <a name="programs"></a>Programas
En la arquitectura del depurador, un *programa:*

- Es un contenedor para un conjunto de subprocesos y un conjunto de módulos. Un programa no tiene una sola analogía en el sistema operativo Windows.

     Un programa es una especie de subproceso. Por ejemplo, al depurar un sitio Web, un script se puede ver como un programa. Mientras que un script se ejecuta en el proceso del motor de scripting, independientemente de otros scripts, también tiene su propio conjunto de subprocesos. Un motor de depuración (DE) se asocia a un programa y no a un proceso o un subproceso.

- Puede identificarse a sí mismo y el proceso en el que se está ejecutando. Un programa se puede adjuntar, separar y describir el DE que lo creó, si existe. Un programa también puede ejecutarse, detener, continuar y terminarse.

- Puede enumerar todos sus subprocesos. Un programa también puede proporcionar su propia secuencia de desensamblado y puede enumerar todos los contextos de código de una posición de documento determinada.

- Se representa mediante un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaz, creado antes de que se adjunta el programa, o como parte del proceso de asociación, dependiendo de la implementación. Cuando un puerto enumera los programas de un proceso, cada programa se crea de acuerdo con una interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondiente que se pasa como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Mientras que los `IDebugProgram2` motores de depuración también crean interfaces para representar programas, estos programas no se crean de acuerdo con un nodo de programa. Las `IDebugProgramNode2` interfaces creadas por un DE se utilizan para la depuración real, mientras que las creadas por un puerto se utilizan solo para detectar qué programas se ejecutan en un proceso.

## <a name="see-also"></a>Vea también
- [Procesos](../../extensibility/debugger/processes.md)
- [Nodos de programa](../../extensibility/debugger/program-nodes.md)
- [Módulos](../../extensibility/debugger/modules.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Posición del documento](../../extensibility/debugger/document-position.md)
- [Contexto del código](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
