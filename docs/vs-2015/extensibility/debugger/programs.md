---
title: Programas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c9beccd5e72c26d695d443c4ab2aa4198e71784
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999456"
---
# <a name="programs"></a>Programas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura de depurador, un **programa**:  
  
-   Es un contenedor para un conjunto de subprocesos y un conjunto de módulos. Un programa no tiene ningún analogía único en el sistema operativo de Windows.  
  
     Un programa es un tipo de subproceso. Por ejemplo, cuando se depura un sitio Web, una secuencia de comandos puede verse como un programa. Mientras se ejecuta una secuencia de comandos en el proceso de motor de scripting, independientemente de otras secuencias de comandos, también tiene su propio conjunto de subprocesos. Un motor de depuración (DE) se asocia a un programa y no a un proceso o un subproceso.  
  
-   Puede identificar a sí mismo y el proceso se ejecuta en y se puede adjuntar, se separa de y describir la DE que lo creó, si existe. Un programa puede ejecutar, detener, continuar y se termina.  
  
-   Puede enumerar todos sus subprocesos. Un programa también puede proporcionar su propia secuencia de desensamblado y puede enumerar todos los contextos de código de una posición de documento determinado.  
  
-   Se representa mediante un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaz, creada antes de que el programa está asociado o como parte del proceso de adjuntar, dependiendo de la implementación. Cuando un puerto enumera los programas de un proceso, se crea cada programa de conformidad con el correspondiente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz se pasa como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aunque los motores de depuración también creación `IDebugProgram2` no se crean interfaces para representar estos programas, programas de conformidad con un nodo de programa. El `IDebugProgramNode2` creadas por una DE las interfaces de se usan para la depuración real, mientras que los creados por un puerto se usan solo para detectar qué programas se ejecutan en un proceso.  
  
## <a name="see-also"></a>Vea también  
 [Procesos](../../extensibility/debugger/processes.md)   
 [Nodos de programa](../../extensibility/debugger/program-nodes.md)   
 [Módulos](../../extensibility/debugger/modules.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Posición del documento](../../extensibility/debugger/document-position.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
