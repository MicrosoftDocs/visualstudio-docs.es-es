---
title: Conceptos del depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e38c743ce7170e0842a3430c7b2aa190df94782b
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203811"
---
# <a name="debugger-concepts"></a>Conceptos del depurador
Para compilar en el paquete de depuración de Visual Studio, deberá estar familiarizado con los conceptos arquitectónicos usados en el diseño del paquete.  
  
## <a name="in-this-section"></a>En esta sección  
 [La sesión de depuración](../../extensibility/debugger/debug-session.md)  
 Explica la función de una sesión en la arquitectura de depuración.  
  
 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md)  
 Define un servidor de qué es en términos de arquitectura, la depuración en términos tanto físicos como abstractos.  
  
 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md)  
 Define qué es un proveedor de puerto en cuanto a la arquitectura de depuración.  
  
 [Puertos](../../extensibility/debugger/ports.md)  
 Define un puerto de qué es en términos de arquitectura de depuración.  
  
 [Procesos](../../extensibility/debugger/processes.md)  
 Define un proceso que está en términos de arquitectura de depuración.  
  
 [Nodos de programa](../../extensibility/debugger/program-nodes.md)  
 Define un nodo de programa en términos de arquitectura, incluido cómo pueden identificar propio y el proceso en que se está ejecutando la depuración.  
  
 [Programas](../../extensibility/debugger/programs.md)  
 Defina un programa en términos de arquitectura de depuración.  
  
 [Subprocesos](../../extensibility/debugger/threads.md)  
 Define las características de subprocesos en términos de arquitectura de depuración.  
  
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)  
 Define un marco de pila en términos de arquitectura de depuración. Un marco de pila es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso.  
  
 [Módulos](../../extensibility/debugger/modules.md)  
 Define un módulo, en términos de depuración de arquitectura, como un contenedor físico de código, como un archivo ejecutable o DLL.  
  
 [Puntos de interrupción](../../extensibility/debugger/breakpoints-visual-studio-sdk.md)  
 Define los tres tipos de puntos de interrupción, pendiente, límite y error, en términos de arquitectura de depuración.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración (DE) funciona simultáneamente dentro de código, documentación y contextos de evaluación de expresión. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.