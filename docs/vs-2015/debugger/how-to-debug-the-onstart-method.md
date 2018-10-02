---
title: 'Cómo: depurar el método OnStart | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2528c99c0f607c3fc98cb8d10e15bfa0c2316f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574291"
---
# <a name="how-to-debug-the-onstart-method"></a>Cómo: Depurar el método OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar el método OnStart](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-the-onstart-method).  
  
Se puede depurar un servicio de Windows si se inicia el servicio y se asocia el depurador al proceso del servicio. Para más información, consulte [Depuración de aplicaciones de servicios de Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). Sin embargo, para depurar el método <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> de un servicio de Windows, debe iniciar el depurador desde dentro del método.  
  
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
  
3.  Seleccione **Sí, depurar \<nombre del servicio >.**  
  
4.  En la ventana del depurador Just-In-Time, seleccione la versión de Visual Studio que quiere usar para la depuración.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Una nueva instancia de Visual Studio se inicia y la ejecución se detiene en el método `Debugger.Launch()` .  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)



