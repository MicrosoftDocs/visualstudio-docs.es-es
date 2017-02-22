---
title: "Excepciones (SDK de Visual Studio) | Microsoft Docs"
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
  - "depurar [SDK de depuración], control de excepciones"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Excepciones (SDK de Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A continuación se describe el proceso que se produce cuando se producen excepciones.  
  
## Proceso de control de excepciones  
  
1.  Cuando una excepción es primero se produce, pero antes de que controla el controlador de excepciones en el programa que se está depurando, el motor de \(DE\) depuración envía [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) el administrador de depuración de sesión \(SDM\) como un evento que detiene.  Se envía `IDebugExceptionEvent2` si solo los valores para la excepción \(especificada en el cuadro de diálogo excepciones en el paquete de depuración\) especifican que el usuario desea detener en notificaciones de primera oportunidad.  
  
2.  El SDM llama [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obtener la propiedad de la excepción.  
  
3.  El paquete de depuración llama a [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones de mostrar al usuario.  
  
4.  El paquete de depuración pregunta al usuario cómo controlar la excepción abrir un cuadro de diálogo excepciones de primera oportunidad.  
  
5.  Si el usuario decide continuar, el SDM llama [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Si el método devuelve S\_OK, llama a [IDebugExceptionEvent2:: PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         O bien  
  
         Si el método devuelve S\_FALSE, el programa que se está depurando se da una segunda oportunidad de controlar la excepción.  
  
6.  Si el programa que se depura no tiene un controlador para una excepción de segunda oportunidad, el OF envía `IDebugExceptionEvent2` al SDM como **EVENT\_SYNCHRONIZATION\_STOP**.  
  
7.  El paquete de depuración pregunta al usuario cómo controlar la excepción abrir un cuadro de diálogo excepciones de primera oportunidad.  
  
8.  El paquete de depuración llama a [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones de mostrar al usuario.  
  
9. El paquete de depuración pregunta al usuario cómo controlar la excepción abrir un cuadro de diálogo excepciones de segunda oportunidad.  
  
10. Si el método devuelve S\_OK, llama a `IDebugExceptionEvent2::PassToDebuggee`.  
  
## Vea también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)