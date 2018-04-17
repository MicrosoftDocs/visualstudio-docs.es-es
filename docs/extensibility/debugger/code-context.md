---
title: Contexto de código | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a84596246ae930cdffc0265f2f2e09652661819
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="code-context"></a>Contexto del código
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración, un **contexto del código**:  
  
-   Proporciona una abstracción de una posición en el código como se sabe que el motor de depuración (Alemania). Para la mayoría de tiempo de ejecución de arquitecturas en la actualidad, un contexto de código puede considerarse como una dirección de la secuencia de instrucciones de un programa. Para los idiomas no tradicionales, donde el código no puede representarse por instrucciones, se puede representar un contexto de código de alguna otra manera.  
  
-   Describe la posición actual en el flujo de ejecución del programa que se está depurando.  
  
-   Existe solo cuando un programa se detiene en un punto de interrupción.  
  
-   Tiene un contexto de documento asociado.  
  
-   Se implementa mediante un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Contexto del documento](../../extensibility/debugger/document-context.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)