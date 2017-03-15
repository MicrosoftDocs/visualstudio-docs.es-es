---
title: "C&#243;mo: Depurar el m&#233;todo OnStart | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OnStart (método)"
  - "depuración [Visual Studio], servicios de Windows"
  - "depurar código administrado, método OnStart"
  - "depurar aplicaciones para servicios de Windows, método OnStart"
  - "aplicaciones de servicios de Windows, depuración"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Depurar el m&#233;todo OnStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede depurar un servicio de Windows si se inicia el servicio y se asocia el depurador al proceso del servicio. Para obtener más información, consulta [How to: Debug Windows Service Applications](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md). Sin embargo, para depurar el método <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> de un servicio de Windows, debe iniciar el depurador desde dentro del método.  
  
1.  Agregue una llamada a <xref:System.Diagnostics.Debugger.Launch%2A> al principio del método `OnStart()`.  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Inicie el servicio \(puede usar `net start` o iniciarlo en la ventana **Servicios**\).  
  
     Debería ver un cuadro de diálogo similar al siguiente:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Seleccione **Sí, depurar \<nombre del servicio\>.**  
  
4.  En la ventana del depurador Just\-In\-Time, seleccione la versión de Visual Studio que quiere usar para la depuración.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Una nueva instancia de Visual Studio se inicia y la ejecución se detiene en el método `Debugger.Launch()`.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)