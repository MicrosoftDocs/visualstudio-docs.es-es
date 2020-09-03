---
title: Marcos de pila | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712839"
---
# <a name="stack-frames"></a>Marcos de pila
En la arquitectura del depurador, un *marco de pila*:

- Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos. Para depurar con Visual Studio, el lenguaje o el entorno que se está depurando deben admitir marcos de pila.

- Puede identificar y describirse a sí mismo y puede devolver el subproceso asociado. Un marco de pila también puede devolver el contexto de código que representa el puntero de instrucción actual y la documentación asociada y los contextos de evaluación de expresión.

- Tiene propiedades que describen el nombre, el tipo y el valor de variables locales y argumentos, y que aparecen en varias ventanas de depuración del IDE.

- Se representa mediante una interfaz [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , creada normalmente por un motor de depuración (de) o una máquina virtual como consecuencia de la ejecución de un subproceso.

## <a name="see-also"></a>Vea también
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
- [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
