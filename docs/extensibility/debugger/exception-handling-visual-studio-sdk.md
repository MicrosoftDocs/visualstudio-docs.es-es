---
title: Excepciones (Visual Studio SDK) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a0d950de8e9f91232e3526064561a7508c133b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>Excepciones (SDK de Visual Studio)
A continuación describe el proceso que tiene lugar cuando se produzcan excepciones.  
  
## <a name="exception-handling-process"></a>Proceso de control de excepciones  
  
1.  Cuando se produce una excepción por primera vez, pero antes de se controla mediante el controlador de excepciones en el programa que se está depurando, el motor de depuración (Alemania) envía una [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) en el Administrador de depuración de sesión (SDM) como un evento de detención. El `IDebugExceptionEvent2` se envía si solo la configuración de la excepción (especificado en el cuadro de diálogo de excepciones en el paquete de depuración) especifica que el usuario desea detener en las notificaciones de excepciones de primera oportunidad.  
  
2.  Las llamadas SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obtener la propiedad de excepción.  
  
3.  Las llamadas de paquete de depuración [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones se presentan al usuario.  
  
4.  El paquete de depuración pide al usuario cómo abrir un cuadro de diálogo de excepciones de primera oportunidad para controlar la excepción.  
  
5.  Si el usuario decide continuar, se llama el SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Si el método devuelve S_OK, llama a [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         O bien  
  
         Si el método devuelve S_FALSE, el programa que se está depurando tiene una segunda oportunidad para controlar la excepción.  
  
6.  Si el programa que se está depurando no tiene ningún controlador para una excepción de segunda oportunidad, envía la DE un `IDebugExceptionEvent2` para el SDM como **EVENT_SYNC_STOP**.  
  
7.  El paquete de depuración pide al usuario cómo abrir un cuadro de diálogo de excepciones de primera oportunidad para controlar la excepción.  
  
8.  Las llamadas de paquete de depuración [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones se presentan al usuario.  
  
9. El paquete de depuración pide al usuario cómo controlar la excepción al abrir un cuadro de diálogo de excepción de segunda oportunidad.  
  
10. Si el método devuelve S_OK, llama a `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)