---
title: "Llamar a eventos del depurador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], eventos"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Llamar a eventos del depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

los eventos en sesiones de depuración aparecen en un orden concreto.  
  
## Explicación  
 Para entender el modelo de llamadas entre el motor de depuración y la \(DE\) sesión depurar el administrador \(SDM\), el siguiente representa el orden de llamada de los eventos que se producen en una sesión de depuración típica:  
  
1.  [La asociación y el desasociar un programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Iniciar el depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [finalizar un programa](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [crear un punto de interrupción](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Cuando un punto de interrupción enlazado o de desatadura](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Errores de punto de interrupción](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Alcanzar un punto de interrupción](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [eliminar un punto de interrupción](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Entrar en el modo de interrupción](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Recorrido en modo de interrupción](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Control de excepciones](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## Vea también  
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)