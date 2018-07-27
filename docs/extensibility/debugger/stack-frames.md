---
title: Marcos de pila | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21ef19e1eaf9e98da3e774f1d0038f03c131ec45
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276720"
---
# <a name="stack-frames"></a>Marcos de pila
En la arquitectura de depurador, un *marco de pila*:  
  
-   Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos a él. Para depurar con Visual Studio, el lenguaje o entorno que se está depurando debe admitir los marcos de pila.  
  
-   Puede identificar y describirse a sí mismos y puede devolver el subproceso asociado. También puede devolver un marco de pila que representa el puntero de instrucción actual y la documentación asociada al contexto del código y contextos de evaluación de expresión.  
  
-   Tiene propiedades que describen el nombre, tipo y valor de argumentos y variables locales y cuáles deben aparecer en varias ventanas de depuración IDE.  
  
-   Se representa mediante un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz, suelen ser creado por un motor de depuración (DE) o una máquina virtual como consecuencia de ejecución de un subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)