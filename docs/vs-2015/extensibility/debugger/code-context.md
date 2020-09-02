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
ms.openlocfilehash: d59a4c79cb21386fa6f6e7031404aeb0b435b3b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197371"
---
# <a name="code-context"></a>Contexto de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración, un **contexto de código**:  
  
- Proporciona una abstracción de una posición en el código tal y como lo conoce el motor DE depuración (DE). Para la mayoría de las arquitecturas en tiempo de ejecución de hoy en día, un contexto de código puede considerarse una dirección en el flujo de instrucciones de un programa. En el caso de los lenguajes no tradicionales, donde el código no se puede representar mediante instrucciones, un contexto de código puede representarse por otros medios.  
  
- Describe la posición actual en la secuencia de ejecución del programa que se está depurando.  
  
- Solo existe cuando un programa se ha detenido en un punto de interrupción.  
  
- Tiene un contexto de documento asociado.  
  
- Se implementa mediante una interfaz [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Contexto del documento](../../extensibility/debugger/document-context.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
