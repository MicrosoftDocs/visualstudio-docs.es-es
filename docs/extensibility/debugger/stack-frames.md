---
title: Marcos de pila | Documentos de Microsoft
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
ms.openlocfilehash: feb2bc9d87486b6f83cf4b19ecec24c8c03edee5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128004"
---
# <a name="stack-frames"></a>Marcos de pila
En cuanto a la arquitectura del depurador, una **marco de pila**:  
  
-   Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos a él. Para depurar con Visual Studio, el idioma o el entorno que se está depurando debe admitir marcos de pila.  
  
-   Puede identificar y autodescriptivos y puede devolver el subproceso asociado. También puede devolver un marco de pila al contexto del código que representa el puntero de instrucción actual, así como la documentación asociada y contextos de evaluación de expresión.  
  
-   Tiene propiedades que describen el nombre, el tipo y el valor de las variables locales y argumentos, y que aparecen en varias ventanas de depuración IDE.  
  
-   Se representa mediante un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfaz, suelen ser creado por un motor de depuración (Alemania) o la máquina virtual como consecuencia de ejecutar un subproceso.  
  
## <a name="see-also"></a>Vea también  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)