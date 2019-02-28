---
title: 'Cómo: depurar el método OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fc5e8a7e0bbc80fd7fa0aa2d242239a9be6a219
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714977"
---
# <a name="how-to-debug-the-onstart-method"></a>Cómo: Depurar el método OnStart
Se puede depurar un servicio de Windows si se inicia el servicio y se asocia el depurador al proceso del servicio. Para obtener más información, consulta [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Sin embargo, para depurar el método <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> de un servicio de Windows, debe iniciar el depurador desde dentro del método.

1. Agregue una llamada a <xref:System.Diagnostics.Debugger.Launch%2A> al principio del método `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Inicie el servicio (puede usar `net start`o iniciarlo en la ventana **Servicios** ).

    Debería ver un cuadro de diálogo similar al siguiente:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Seleccione **Sí, depurar \<nombre del servicio**.

4. En la ventana del depurador Just-In-Time, seleccione la versión de Visual Studio que quiere usar para la depuración.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Una nueva instancia de Visual Studio se inicia y la ejecución se detiene en el método `Debugger.Launch()` .

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
