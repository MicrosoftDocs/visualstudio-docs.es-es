---
title: "Error: Aseg&#250;rese de que DNS est&#225; bien configurado en el equipo de destino | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Error: Aseg&#250;rese de que DNS est&#225; bien configurado en el equipo de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Este error se produce cuando el equipo de destino no puede resolver el nombre del equipo host del depurador de Visual Studio.  Compruebe la configuración de DNS en el equipo de destino.  
  
-   Para obtener información sobre cómo ver la configuración de DNS en Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 o Windows Server 2008 R2, haga esto: en el menú **Inicio**, elija **Ayuda y soporte técnico** y, a continuación, busque Cambiar la configuración de TCP\/IP.  
  
-   Para obtener más información, vaya al [sitio web de Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) y busque Cambiar la configuración de TCP\/IP.  
  
 Si no puede resolver el problema de DNS, intente ejecutar el depurador remoto con una cuenta diferente.  Este error solo se produce cuando se ejecuta el depurador remoto con el sistema local o cuenta de servicio de red.  Si ejecuta el depurador remoto con otra cuenta, puede que la cuenta use la autenticación NTLM, que no requiere DNS.  .  Para conocer el procedimiento, consulte [Error: El servicio del depurador remoto de Visual Studio del equipo de destino no se puede volver a conectar a este equipo](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).