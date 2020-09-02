---
title: Marcos de pila | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3050e89db2f5cbb138f3d358b10c7cd936c560e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423392"
---
# <a name="stack-frames"></a>Marcos de pila
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En cuanto a la arquitectura del depurador, un **marco de pila**:  
  
- Es una abstracción de una pila que proporciona el contexto de ejecución de un subproceso. Un subproceso siempre se ejecuta dentro de una función. Un marco de pila contiene las variables locales de la función y los argumentos. Para depurar con Visual Studio, el lenguaje o el entorno que se está depurando deben admitir marcos de pila.  
  
- Puede identificar y describirse a sí mismo y puede devolver el subproceso asociado. Un marco de pila también puede devolver el contexto de código que representa el puntero de instrucción actual, así como la documentación asociada y los contextos de evaluación de expresión.  
  
- Tiene propiedades que describen el nombre, el tipo y el valor de variables locales y argumentos, y que aparecen en varias ventanas de depuración del IDE.  
  
- Se representa mediante una interfaz [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , creada normalmente por un motor de depuración (de) o una máquina virtual como consecuencia de la ejecución de un subproceso.  
  
## <a name="see-also"></a>Consulte también  
 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
