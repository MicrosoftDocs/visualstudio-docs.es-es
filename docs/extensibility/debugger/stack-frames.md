---
title: Marcos de pila | Microsoft Docs
description: En este artículo se describe la definición y el rol de un marco de pila en la arquitectura del depurador Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898557"
---
# <a name="stack-frames"></a>Marcos de pila
En la arquitectura del depurador, un *marco de pila*:

- Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos que contiene. Para depurar con Visual Studio, el lenguaje o entorno que se está depurando debe admitir marcos de pila.

- Puede identificarse y describirse a sí mismo, y puede devolver el subproceso asociado. Un marco de pila también puede devolver el contexto de código que representa el puntero de instrucción actual y los contextos de evaluación de expresiones y documentación asociados.

- Tiene propiedades que describen el nombre, el tipo y el valor de las variables y argumentos locales, y que aparecen en varias ventanas de depuración del IDE.

- Se representa mediante una [interfaz IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) normalmente creada por un motor de depuración (DE) o una máquina virtual como consecuencia de ejecutar un subproceso.

## <a name="see-also"></a>Consulta también
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
