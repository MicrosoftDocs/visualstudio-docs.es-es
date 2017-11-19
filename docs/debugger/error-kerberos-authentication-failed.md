---
title: "Error: Error de autenticación de Kerberos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37dc0626a1f96d20aa7cf1cb4a3ca2d811d391b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="error-kerberos-authentication-failed"></a>Error: Error de autenticación Kerberos
Al intentar realizar la depuración remota, podría aparecer el siguiente mensaje de error:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 Este error se produce cuando el Monitor de depuración remota de Visual Studio se está ejecutando con la cuenta de sistema local o de servicio de red. Con una de estas cuentas, el depurador remoto debe establecer una conexión de autenticación Kerberos para comunicarse de vuelta con el equipo host del depurador de Visual Studio.  
  
 La autenticación Kerberos no está disponible bajo estas condiciones:  
  
-   El equipo de destino o el equipo host del depurador está en un grupo de trabajo, en lugar de en un dominio  
  
     \- o -  
  
-   Kerberos está deshabilitado en el controlador de dominio.  
  
 Si la autenticación Kerberos no está disponible, cambie la cuenta que se usa para ejecutar el Monitor de depuración remota de Visual Studio. Para conocer el procedimiento, consulte [Error: servicio de The Visual Studio Remote Debugger en el equipo de destino no se puede conectar a este equipo](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
 Si ambos equipos están conectados al mismo dominio y todavía aparece este mensaje, compruebe que DNS en el equipo de destino está resolviendo correctamente el nombre del equipo host del depurador. Vea el procedimiento siguiente.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Para comprobar que DNS en el equipo de destino está resolviendo correctamente el nombre del equipo host del depurador  
  
1.  En el equipo de destino, abra el **iniciar** menú, elija **Accesorios** y, a continuación, haga clic en **símbolo**.  
  
2.  En el **símbolo** ventana, escriba:  
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3.  La primera línea de la respuesta `ping` muestra el nombre del equipo completo y la dirección IP que devuelve DNS para el equipo especificado.  
  
4.  En el equipo host del depurador, abra un **símbolo** ventana y ejecute `ipconfig`.  
  
5.  Compare los valores de la dirección IP.  
  
## <a name="see-also"></a>Vea también  
 [Errores de depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuración remota](../debugger/remote-debugging.md)