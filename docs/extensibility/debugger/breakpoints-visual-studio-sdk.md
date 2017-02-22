---
title: "Puntos de interrupci&#243;n (SDK de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "puntos de interrupción"
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Puntos de interrupci&#243;n (SDK de Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

hay tres tipos de puntos de interrupción: pendiente, enlazado, y error.  
  
 **un punto de interrupción pendiente:**  
  
-   Es una abstracción que contiene toda la información necesaria para enlazar un punto de interrupción a uno o varios contextos de código en uno o más programas.  Cada vez que un programa que es código depurado de la causa a cargar, el motor de depuración comprueba todos los puntos de interrupción pendientes para ver si pueden enlazarse.  
  
     Un punto de interrupción pendiente propio nunca se enlaza al código, pero obtiene suficiente y se dice contener todos los puntos de interrupción enlazados que genera.  
  
-   Se representa mediante una interfaz de [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
 **un punto de interrupción enlazado:**  
  
-   Es una abstracción para un punto de interrupción asociado a o el límite de un único contexto de código.  cada punto de interrupción enlazado se genera en respuesta a un punto de interrupción pendiente.  un punto de interrupción pendiente puede, sin embargo, generar más de un punto de interrupción enlazado.  
  
     Cuando se descarga el código, un punto de interrupción enlazado puede ser independiente y descartó.  
  
-   Se representa mediante una interfaz de [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .  
  
 **Un punto de interrupción de error:**  
  
-   Es una abstracción para describir un error en intentar enlazar un punto de interrupción pendiente en un contexto del código.  Un punto de interrupción de error describe un error en la ubicación o en la expresión propia de punto de interrupción.  Para obtener más información, vea [puntos de interrupción obligatorios](../../extensibility/debugger/binding-breakpoints.md).  
  
     El error de punto de interrupción puede ser un error o una advertencia.  
  
-   Se representa mediante una interfaz de [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .  
  
## Vea también  
 [Programas](../../extensibility/debugger/programs.md)   
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Contexto de código](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)