---
title: Excepciones (Visual Studio SDK) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 646479184061b093d5d84f81827a4106bd3cda47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100795"
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
  
         -o bien-  
  
         Si el método devuelve S_FALSE, el programa que se está depurando tiene una segunda oportunidad para controlar la excepción.  
  
6.  Si el programa que se está depurando no tiene ningún controlador para una excepción de segunda oportunidad, envía la DE un `IDebugExceptionEvent2` para el SDM como **EVENT_SYNC_STOP**.  
  
7.  El paquete de depuración pide al usuario cómo abrir un cuadro de diálogo de excepciones de primera oportunidad para controlar la excepción.  
  
8.  Las llamadas de paquete de depuración [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones se presentan al usuario.  
  
9. El paquete de depuración pide al usuario cómo controlar la excepción al abrir un cuadro de diálogo de excepción de segunda oportunidad.  
  
10. Si el método devuelve S_OK, llama a `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Vea también  
 [Llamada a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)