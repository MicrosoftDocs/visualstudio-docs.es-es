---
title: Control de excepciones (SDK de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738766"
---
# <a name="exception-handling-visual-studio-sdk"></a>Control de excepciones (SDK de Visual Studio)
A continuación se describe el proceso que se produce cuando se producen excepciones.

## <a name="exception-handling-process"></a>Proceso de manejo de excepciones

1. Cuando se produce una excepción por primera vez, pero antes de que se controla mediante el controlador de excepciones en el programa que se está depurando, el motor de depuración (DE) envía un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) al administrador de depuración de sesión (SDM) como un evento de detención. Se `IDebugExceptionEvent2` envía si solo la configuración de la excepción (especificada en el cuadro de diálogo Excepciones del paquete de depuración) especifica que el usuario desea detenerse en las notificaciones de excepción de primera oportunidad.

2. El SDM llama a [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obtener la propiedad de excepción.

3. El paquete de depuración llama a [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones presentar al usuario.

4. El paquete de depuración pregunta al usuario cómo controlar la excepción abriendo un cuadro de diálogo de excepción de primera oportunidad.

5. Si el usuario decide continuar, el SDM llama a [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Si el método devuelve S_OK, llama a [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         o bien

         Si el método devuelve S_FALSE, el programa que se está depurando tiene una segunda oportunidad para controlar la excepción.

6. Si el programa que se está depurando no tiene ningún `IDebugExceptionEvent2` controlador para una excepción de segunda oportunidad, la DE envía un al SDM como **EVENT_SYNC_STOP**.

7. El paquete de depuración pregunta al usuario cómo controlar la excepción abriendo un cuadro de diálogo de excepción de primera oportunidad.

8. El paquete de depuración llama a [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar qué opciones presentar al usuario.

9. El paquete de depuración pregunta al usuario cómo controlar la excepción abriendo un cuadro de diálogo de excepción de segunda oportunidad.

10. Si el método devuelve `IDebugExceptionEvent2::PassToDebuggee`S_OK, llama a .

## <a name="see-also"></a>Vea también
- [Eventos del depurador de llamadas](../../extensibility/debugger/calling-debugger-events.md)
