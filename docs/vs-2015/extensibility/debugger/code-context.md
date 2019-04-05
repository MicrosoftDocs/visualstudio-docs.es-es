---
title: Contexto de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fedbb786c7282af213b5e5d5b80c06cb2f08159
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999126"
---
# <a name="code-context"></a>Contexto de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración, un **contexto del código**:  
  
-   Proporciona una abstracción de una posición en el código tal y como se sabe que el motor de depuración (DE). Para la mayoría de las arquitecturas de tiempo de ejecución en la actualidad, un contexto de código puede considerarse como una dirección en la secuencia de instrucciones de un programa. Para los idiomas no tradicionales, donde no se puede representar código por instrucciones, se puede representar un contexto de código por otros medios.  
  
-   Describe la posición actual en la secuencia de ejecución del programa que se está depurando.  
  
-   Existe solo cuando se ha detenido un programa en un punto de interrupción.  
  
-   Tiene un contexto de documento asociado.  
  
-   Se implementa mediante un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Contexto de documento](../../extensibility/debugger/document-context.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
