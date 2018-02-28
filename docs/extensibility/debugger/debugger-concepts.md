---
title: Conceptos del depurador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 920706adb86d79e635e4f5289ca010e03282853e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-concepts"></a>Conceptos del depurador
Para compilar en el paquete de depuración de Visual Studio, deberá estar familiarizado con los conceptos arquitectónicos usados en diseñar el paquete.  
  
## <a name="in-this-section"></a>En esta sección  
 [Sesión de depuración](../../extensibility/debugger/debug-session.md)  
 Explica el rol de una sesión en la arquitectura de depuración.  
  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Define un servidor de qué es en cuanto a la depuración de arquitectura, en términos abstractos y físicos.  
  
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)  
 Define qué es un proveedor de puerto en cuanto a la arquitectura de depuración.  
  
 [Puertos](../../extensibility/debugger/ports.md)  
 Define un puerto de qué es en cuanto a la arquitectura de depuración.  
  
 [Procesos](../../extensibility/debugger/processes.md)  
 Define un proceso que está en cuanto a la arquitectura de depuración.  
  
 [Nodos de programa](../../extensibility/debugger/program-nodes.md)  
 Define un nodo de programa en cuanto a la arquitectura, incluido cómo puede identificar propio y el proceso en que se está ejecutando la depuración.  
  
 [Programas](../../extensibility/debugger/programs.md)  
 Define un programa en cuanto a la arquitectura de depuración.  
  
 [Subprocesos](../../extensibility/debugger/threads.md)  
 Define las características de subprocesos en cuanto a la arquitectura de depuración.  
  
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)  
 Define un marco de pila en cuanto a la arquitectura de depuración. Un marco de pila es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso.  
  
 [Módulos](../../extensibility/debugger/modules.md)  
 Define un módulo, en cuanto a la depuración de arquitectura, como un contenedor físico del código, como un archivo ejecutable o un archivo DLL.  
  
 [Puntos de interrupción](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Define los tres tipos de puntos de interrupción, pendiente, enlazadas a error, en cuanto a la arquitectura de depuración.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración (Alemania) funciona simultáneamente dentro de código, documentación y los contextos de evaluación de expresión. Describe, para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona una visión general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (Alemania), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a varias tareas de depuración, como iniciar un programa y la evaluación de expresiones.