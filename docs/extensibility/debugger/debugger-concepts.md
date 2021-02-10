---
title: Conceptos del depurador | Microsoft Docs
description: Obtenga información sobre los conceptos de arquitectura utilizados en el diseño del paquete de depuración de Visual Studio para ayudarle a crear en ese paquete.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952413"
---
# <a name="debugger-concepts"></a>Conceptos del depurador
Para compilar en el paquete de depuración de Visual Studio, debe estar familiarizado con los conceptos de arquitectura utilizados en el diseño del paquete.

## <a name="in-this-section"></a>En esta sección
 [Sesión de depuración](../../extensibility/debugger/debug-session.md) Explica el rol de una sesión en la arquitectura de depuración.

 [Servidores](../../extensibility/debugger/servers-visual-studio-sdk.md) de Define lo que un servidor es en términos de arquitectura de depuración, tanto en términos abstractos como físicos.

 [Proveedores de puertos](../../extensibility/debugger/port-suppliers.md) Define qué es un proveedor de puerto en términos de arquitectura de depuración.

 [Puertos](../../extensibility/debugger/ports.md) de Define qué es un puerto en términos de arquitectura de depuración.

 [Procesos](../../extensibility/debugger/processes.md) de Define lo que es un proceso en términos de arquitectura de depuración.

 [Nodos de programa](../../extensibility/debugger/program-nodes.md) Define un nodo de programa en lo que se refiere a la arquitectura de depuración, lo que incluye cómo puede identificarse y el proceso en el que se está ejecutando.

 [Programas](../../extensibility/debugger/programs.md) de Define un programa en términos de arquitectura de depuración.

 [Subprocesos](../../extensibility/debugger/threads.md) Define las características de los subprocesos en cuanto a la arquitectura de depuración.

 [Marcos de pila](../../extensibility/debugger/stack-frames.md) Define un marco de pila en términos de arquitectura de depuración. Un marco de pila es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso.

 [Módulos](../../extensibility/debugger/modules.md) de Define un módulo, en términos de arquitectura de depuración, como un contenedor físico de código, como un archivo ejecutable o un archivo DLL.

 [Puntos de interrupción](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Define los tres tipos de puntos de interrupción (pendientes, enlazados y de error) en cuanto a la arquitectura de depuración.

## <a name="related-sections"></a>Secciones relacionadas
 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo el motor DE depuración (DE) funciona simultáneamente dentro del código, la documentación y los contextos de evaluación de expresiones. Para cada uno de los tres contextos, se describen la ubicación, la posición o la evaluación correspondientes.

 [Componentes del depurador](../../extensibility/debugger/debugger-components.md) Proporciona información general sobre los componentes de depuración de Visual Studio, entre los que se incluyen el motor DE depuración (DE), el evaluador DE expresiones (EE) y el controlador de símbolos (SH).

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.
