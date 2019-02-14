---
title: Procedimiento Depurar el método OnStart | Microsoft Docs
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
ms.openlocfilehash: 2bf37bef11c4d07ac0cb2c218f03f344a02ed4e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005573"
---
# <a name="how-to-debug-the-onstart-method"></a>Cómo: Depurar el método OnStart
Se puede depurar un servicio de Windows si se inicia el servicio y se asocia el depurador al proceso del servicio. Para obtener más información, consulta [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Sin embargo, para depurar el método <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> de un servicio de Windows, debe iniciar el depurador desde dentro del método.  
  
1.  Agregue una llamada a <xref:System.Diagnostics.Debugger.Launch%2A> al principio del método `OnStart()`.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Inicie el servicio (puede usar `net start`o iniciarlo en la ventana **Servicios** ).  
  
     Debería ver un cuadro de diálogo similar al siguiente:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Seleccione **Sí, depurar \<nombre del servicio**.  
  
4.  En la ventana del depurador Just-In-Time, seleccione la versión de Visual Studio que quiere usar para la depuración.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Una nueva instancia de Visual Studio se inicia y la ejecución se detiene en el método `Debugger.Launch()` .  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)