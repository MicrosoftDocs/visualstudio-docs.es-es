---
title: para la depuración del método OnStart | Microsoft Docs
description: Obtenga información sobre cómo depurar el método OnStart de un servicio de Windows en Visual Studio; para ello, inicie el depurador desde dentro del método.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903147"
---
# <a name="how-to-debug-the-onstart-method"></a>Procedimiento Depuración del método OnStart
Se puede depurar un servicio de Windows si se inicia el servicio y se asocia el depurador al proceso del servicio. Para obtener más información, vea [Cómo: Depurar aplicaciones de servicios de Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Sin embargo, para depurar el método <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> de un servicio de Windows, debe iniciar el depurador desde dentro del método.

1. Agregue una llamada a <xref:System.Diagnostics.Debugger.Launch%2A> al principio del método `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Inicie el servicio (puede usar `net start`o iniciarlo en la ventana **Servicios** ).

    Debería ver un cuadro de diálogo similar al siguiente:

    ![Captura de pantalla de un cuadro de diálogo del Depurador Just-in-Time de Visual Studio en la que se muestra que se ha producido una excepción no controlada de .NET Framework en WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Seleccione **Sí, depurar \<service name>.**

4. En la ventana del depurador Just-In-Time, seleccione la versión de Visual Studio que quiere usar para la depuración.

    ![Captura de pantalla de una ventana del Depurador Just-in-Time de Visual Studio con la opción "New instance of Microsoft Visual Studio 2015" (Nueva instancia de Microsoft Visual Studio 2015) seleccionada en la lista de Depuradores posibles.](../debugger/media/justintimedebugger.png)

5. Una nueva instancia de Visual Studio se inicia y la ejecución se detiene en el método `Debugger.Launch()` .

## <a name="see-also"></a>Vea también
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
