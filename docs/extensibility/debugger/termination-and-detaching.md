---
title: "Separar y terminaci&#243;n | Microsoft Docs"
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
  - "programas, eventos de finalización"
  - "motores de depuración, cuando se desasocia de programas"
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Separar y terminaci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe la terminación normal.  
  
## Explicación  
 Después de [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o de [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) la interfaz continúa, si no hay puntos de interrupción, excepciones, errores en tiempo de ejecución, o los bucles sin fin en la aplicación para depurar, el programa que se está depurando se ejecutará hasta completarse.  Es terminación normal.  
  
 Debe enviar [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) a la terminación normal de implementan.  esto requiere implementar el método de [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .  
  
## Vea también  
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)