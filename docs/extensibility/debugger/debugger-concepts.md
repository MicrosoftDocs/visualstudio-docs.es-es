---
title: Conceptos del depurador (En el centro de la web Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738986"
---
# <a name="debugger-concepts"></a>Conceptos del depurador
Para compilar en el paquete de depuración de Visual Studio, debe estar familiarizado con los conceptos arquitectónicos utilizados en el diseño del paquete.

## <a name="in-this-section"></a>En esta sección
 [Sesión de depuración](../../extensibility/debugger/debug-session.md) Explica el rol de una sesión en la arquitectura de depuración.

 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md) Define lo que es un servidor en términos de arquitectura de depuración, tanto en términos abstractos como físicos.

 [Proveedores portuarios](../../extensibility/debugger/port-suppliers.md) Define lo que es un proveedor de puertos en términos de arquitectura de depuración.

 [Puertos](../../extensibility/debugger/ports.md) Define lo que es un puerto en términos de arquitectura de depuración.

 [Procesos](../../extensibility/debugger/processes.md) Define lo que es un proceso en términos de arquitectura de depuración.

 [Nodos de programa](../../extensibility/debugger/program-nodes.md) Define un nodo de programa en términos de arquitectura de depuración, incluida la forma en que puede identificarse a sí mismo y el proceso en el que se ejecuta.

 [Programas](../../extensibility/debugger/programs.md) Define un programa en términos de arquitectura de depuración.

 [Roscas](../../extensibility/debugger/threads.md) Define las características de los subprocesos en términos de arquitectura de depuración.

 [Marcos de pila](../../extensibility/debugger/stack-frames.md) Define un marco de pila en términos de arquitectura de depuración. Un marco de pila es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso.

 [Módulos](../../extensibility/debugger/modules.md) Define un módulo, en términos de arquitectura de depuración, como un contenedor físico de código, como un archivo ejecutable o un archivo DLL.

 [Puntos de interrupción](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Define los tres tipos de puntos de interrupción (pendientes, enlazados y errores) en términos de arquitectura de depuración.

## <a name="related-sections"></a>Secciones relacionadas
 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo funciona el motor de depuración (DE) simultáneamente dentro de los contextos de evaluación de código, documentación y expresión. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para ella.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general de los componentes de depuración de Visual Studio, que incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.
