---
title: "Contexto de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración] y contextos"
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Contexto de c&#243;digo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de depuración, **un contexto de código**:  
  
-   Proporciona una abstracción de una posición en código como se conoce al motor de depuración \(DE\).  Para la mayoría de las arquitecturas en tiempo de ejecución actual, un contexto del código se puede considerar como dirección en una secuencia de instrucciones de programa.  Para los lenguajes no tradicionales, donde el código no se puede representar mediante instrucciones, un contexto de código puede representarse por otros medios.  
  
-   Describe la posición actual en la secuencia de ejecución del programa que se depura.  
  
-   Sólo existe cuando un programa ha detenido en un punto de interrupción.  
  
-   Tiene un contexto asociado del documento.  
  
-   Se implementa mediante una interfaz de [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .  
  
## Vea también  
 [Contexto de documento](../../extensibility/debugger/document-context.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)