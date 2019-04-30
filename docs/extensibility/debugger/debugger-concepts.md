---
title: Conceptos del depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e3a9043215c5242246e54dc3e1eb2e85cd26c91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925898"
---
# <a name="debugger-concepts"></a>Conceptos del depurador
Para compilar en el paquete de depuración de Visual Studio, deberá estar familiarizado con los conceptos arquitectónicos usados en el diseño del paquete.

## <a name="in-this-section"></a>En esta sección
 [La sesión de depuración](../../extensibility/debugger/debug-session.md) explica el rol de una sesión en la arquitectura de depuración.

 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md) define lo que un servidor está en términos de arquitectura, la depuración en términos tanto físicos como abstractos.

 [Proveedores de puerto](../../extensibility/debugger/port-suppliers.md) define lo que un proveedor de puerto está en términos de arquitectura de depuración.

 [Puertos](../../extensibility/debugger/ports.md) define un puerto de qué es en términos de arquitectura de depuración.

 [Procesos](../../extensibility/debugger/processes.md) define un proceso que está en términos de arquitectura de depuración.

 [Nodos de programa](../../extensibility/debugger/program-nodes.md) define un nodo de programa en términos de arquitectura, incluido cómo pueden identificar propio y el proceso se está ejecutando en la depuración.

 [Programas](../../extensibility/debugger/programs.md) define un programa en términos de arquitectura de depuración.

 [Subprocesos](../../extensibility/debugger/threads.md) define las características de subprocesos en términos de arquitectura de depuración.

 [Marcos de pila](../../extensibility/debugger/stack-frames.md) define un marco de pila en términos de arquitectura de depuración. Un marco de pila es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso.

 [Módulos](../../extensibility/debugger/modules.md) define un módulo, en términos de depuración de arquitectura, como un contenedor físico de código, como un archivo ejecutable o DLL.

 [Los puntos de interrupción](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) define los tres tipos de puntos de interrupción, pendiente, límite y error, en términos de arquitectura de depuración.

## <a name="related-sections"></a>Secciones relacionadas
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md) explica cómo el motor de depuración (DE) funciona simultáneamente dentro de los contextos de evaluación de expresión, documentación y código. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) proporciona información general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.