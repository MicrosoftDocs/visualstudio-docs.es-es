---
title: 'Error: Ensure that DNS is Correctly Configured on the Target Computer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6815e21d0fe7af3a24f2fc36a4f448ec420c89de
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299748"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Error: Asegúrese de que DNS está bien configurado en el equipo de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al intentar realizar una depuración remota, es posible recibir el siguiente mensaje de error:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Este error se produce cuando el equipo de destino no puede resolver el nombre del equipo host del depurador de Visual Studio. Compruebe la configuración de DNS en el equipo de destino.  
  
- Para obtener información sobre cómo ver la configuración de DNS en Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 o Windows Server 2008 R2, haga esto: en el menú **Inicio**, elija **Ayuda y soporte técnico** y después busque **Cambiar la configuración de TCP/IP**.  
  
- Para obtener más información, vaya al [sitio web de Microsoft Windows](https://go.microsoft.com/fwlink/?LinkId=252720) y busque **Cambiar la configuración de TCP/IP**.  
  
  Si no puede resolver el problema de DNS, intente ejecutar el depurador remoto con una cuenta diferente. Este error solo se produce cuando se ejecuta el depurador remoto con el sistema local o cuenta de servicio de red. Si ejecuta el depurador remoto con otra cuenta, puede que la cuenta use la autenticación NTLM, que no requiere DNS. . For the procedure, see [Error: The Visual Studio Remote Debugger service on the target computer cannot connect back to this computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).
