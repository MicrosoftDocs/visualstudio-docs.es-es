---
title: 'Error: Asegúrese de que DNS está configurado correctamente en el equipo de destino | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b2238cd606f748d53c48722d9719bd936550ae1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Error: Asegúrese de que DNS está bien configurado en el equipo de destino
Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Este error se produce cuando el equipo de destino no puede resolver el nombre del equipo host del depurador de Visual Studio. Compruebe la configuración de DNS en el equipo de destino.  
  
-   Para obtener información acerca de cómo ver la configuración de DNS en Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 o Windows Server 2008 R2, hacer esto: en el **iniciar** menú, elija **ayuda y soporte técnico** y, a continuación, busque **configuración TCP/IP de cambio**.  
  
-   Para obtener más información, vaya a [sitio web de Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) y busque **configuración TCP/IP de cambio**.  
  
 Si no puede resolver el problema de DNS, intente ejecutar el depurador remoto con una cuenta diferente. Este error solo se produce cuando se ejecuta el depurador remoto con el sistema local o cuenta de servicio de red. Si ejecuta el depurador remoto con otra cuenta, puede que la cuenta use la autenticación NTLM, que no requiere DNS. . Para conocer el procedimiento, consulte [Error: servicio de The Visual Studio Remote Debugger en el equipo de destino no se puede conectar a este equipo](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).