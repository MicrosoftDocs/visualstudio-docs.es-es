---
title: Control de excepciones (SDK de Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738766"
---
# <a name="exception-handling-visual-studio-sdk"></a>Control de excepciones (SDK de Visual Studio)
A continuación se describe el proceso que se produce cuando se producen excepciones.

## <a name="exception-handling-process"></a>Proceso de control de excepciones

1. Cuando se inicia una excepción por primera vez, pero antes de que la controle el controlador de excepciones en el programa que se está depurando, el motor DE depuración (DE) envía un [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) al administrador de depuración de sesión (SDM) como un evento de detención. `IDebugExceptionEvent2`Se envía si solo los valores de la excepción (especificados en el cuadro de diálogo excepciones en el paquete de depuración) especifican que el usuario desea detenerse en las notificaciones de excepciones de primera oportunidad.

2. El SDM llama a [IDebugExceptionEvent2:: GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obtener la propiedad de la excepción.

3. El paquete de depuración llama a [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar las opciones que se van a presentar al usuario.

4. El paquete de depuración pregunta al usuario Cómo controlar la excepción abriendo un cuadro de diálogo de excepción de primera oportunidad.

5. Si el usuario decide continuar, el SDM llama a [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Si el método devuelve S_OK, llama a [IDebugExceptionEvent2::P asstodebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         o bien

         Si el método devuelve S_FALSE, el programa que se está depurando recibe una segunda oportunidad para controlar la excepción.

6. Si el programa que se está depurando no tiene ningún controlador para una excepción de segunda oportunidad, el DE envía un `IDebugExceptionEvent2` al SDM como **EVENT_SYNC_STOP**.

7. El paquete de depuración pregunta al usuario Cómo controlar la excepción abriendo un cuadro de diálogo de excepción de primera oportunidad.

8. El paquete de depuración llama a [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar las opciones que se van a presentar al usuario.

9. El paquete de depuración pregunta al usuario Cómo controlar la excepción abriendo un cuadro de diálogo de excepción de segunda oportunidad.

10. Si el método devuelve S_OK, llama a `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>Vea también
- [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)
