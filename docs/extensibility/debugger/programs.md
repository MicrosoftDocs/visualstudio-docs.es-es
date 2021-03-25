---
title: Programas | Microsoft Docs
description: En este artículo se describe la definición y el rol de un programa en la arquitectura del depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0769d2abc650305095115d1c645e3037096974de
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094619"
---
# <a name="programs"></a>Programas
En la arquitectura del depurador, un *programa*:

- Es un contenedor para un conjunto de subprocesos y un conjunto de módulos. Un programa no tiene una analogía única en el sistema operativo Windows.

     Un programa es un tipo de subproceso. Por ejemplo, al depurar un sitio web, un script se puede considerar como un programa. Mientras que un script se ejecuta en el proceso del motor de scripting, independientemente de otros scripts, también tiene su propio conjunto de subprocesos. Un motor DE depuración (DE) se asocia a un programa y no a un proceso o un subproceso.

- Puede identificarse y el proceso en el que se está ejecutando. Un programa se puede adjuntar a, desasociar de y describir el DE que lo creó, si existe. Un programa también puede ejecutar, detener, continuar y finalizar.

- Puede enumerar todos los subprocesos. Un programa también puede proporcionar su propia secuencia de desensamblado y puede enumerar todos los contextos de código de una posición de documento determinada.

- Se representa mediante una interfaz [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , creada antes de que se adjunte el programa o como parte del proceso de asociación, dependiendo de la implementación. Cuando un puerto enumera los programas de un proceso, cada programa se crea de acuerdo con la interfaz [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondiente que se pasa como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aunque los motores de depuración también crean `IDebugProgram2` interfaces para representar programas, estos programas no se crean de acuerdo con un nodo de programa. Las `IDebugProgramNode2` interfaces creadas por un de se utilizan para la depuración real, mientras que las creadas por un puerto se utilizan únicamente para detectar los programas que se ejecutan en un proceso.

## <a name="see-also"></a>Consulte también
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
