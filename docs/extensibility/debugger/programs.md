---
title: Programas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e34dbcf9c19b5e8e7a16d2f409159597670cb8cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="programs"></a>Programas
En cuanto a la arquitectura del depurador, una **programa**:  
  
-   Es un contenedor para un conjunto de subprocesos y un conjunto de módulos. Un programa no tiene ningún analogía único en el sistema operativo Windows.  
  
     Un programa es un tipo de subproceso. Por ejemplo, cuando se depura un sitio Web, una secuencia de comandos puede considerarse como un programa. Mientras se ejecuta un script en el proceso del motor de scripting, independientemente de otras secuencias de comandos, también tiene su propio conjunto de subprocesos. Un motor de depuración (Alemania) se asocia a un programa pero no a un proceso o un subproceso.  
  
-   Puede identificar propio y el proceso se está ejecutando y puede adjuntarse, se separa de y describir el Alemania que creó, si lo hay. Un programa puede ejecutar, detener, continuar y terminará.  
  
-   Puede enumerar todos sus subprocesos. Un programa también puede proporcionar su propia secuencia de desensamblado y puede enumerar todos los contextos de código de una posición de documento determinado.  
  
-   Se representa mediante un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaz, creada antes de que el programa que está asociado, o como parte del proceso de adjuntar, dependiendo de la implementación. Cuando un puerto enumera los programas de un proceso, se crea cada programa de acuerdo con su correspondiente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaz se pasa como argumento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Aunque los motores de depuración también crear `IDebugProgram2` interfaces que representan, estos programas no se crean con arreglo a un nodo de programa. El `IDebugProgramNode2` interfaces creadas por una DE se utilizan para la depuración real, mientras que los creados por un puerto se usan solo para detectar qué programas se ejecutan en un proceso.  
  
## <a name="see-also"></a>Vea también  
 [Procesos](../../extensibility/debugger/processes.md)   
 [Nodos de programa](../../extensibility/debugger/program-nodes.md)   
 [Módulos](../../extensibility/debugger/modules.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Posición del documento](../../extensibility/debugger/document-position.md)   
 [Contexto del código](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)