---
title: Marcos de pila ( Stack Frames) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712839"
---
# <a name="stack-frames"></a>Marcos de pila
En la arquitectura del depurador, un marco de *pila:*

- Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos para ella. Para depurar con Visual Studio, el lenguaje o entorno que se está depurando debe admitir marcos de pila.

- Puede identificarse y describirse a sí mismo, y puede devolver el subproceso asociado. Un marco de pila también puede devolver el contexto de código que representa el puntero de instrucción actual y los contextos de evaluación de documentación y expresión asociados.

- Tiene propiedades que describen el nombre, el tipo y el valor de las variables y argumentos locales, y que aparecen en varias ventanas de depuración IDE.

- Se representa mediante un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz, normalmente creado por un motor de depuración (DE) o máquina virtual como consecuencia de la ejecución de un subproceso.

## <a name="see-also"></a>Vea también
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
