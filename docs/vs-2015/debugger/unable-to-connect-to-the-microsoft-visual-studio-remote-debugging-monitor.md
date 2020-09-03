---
title: No se puede conectar al Monitor de depuración remota de Microsoft Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477060"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>No se puede conectar al Monitor de depuración remota de Microsoft Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este mensaje de error aparece cuando escribe un nombre de Monitor de depuración remota de Visual Studio no válido en el cuadro de diálogo **Asociar al proceso** . El nombre del Monitor de depuración remota es generalmente el mismo del equipo al cual intenta conectarse para llevar a cabo la depuración remota. Es posible que este mensaje aparezca debido a que el equipo remoto no existe en la red, el monitor de depuración remota no está correctamente configurado en el equipo remoto o no es posible tener acceso a este último debido a problemas de red o a la presencia de un firewall.  
  
> [!IMPORTANT]
> Si necesita más ayuda, vea [Talk to Us](../ide/talk-to-us.md) para obtener información sobre las distintas formas de ponerse en contacto con Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Recibí este mensaje mientras estaba depurando localmente  
 Si recibe este mensaje mientras depura localmente, es posible que un software antivirus o firewall de terceros sea el culpable. Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Los dos procesos se comunican con la red local en el equipo local. Nada de tráfico de red sale del equipo, pero es posible que el software de seguridad de terceros bloquee la comunicación.  
  
 Las siguientes secciones enumeran algunas otras razones por las que puede aparecer este mensaje, así como lo que puede hacer para corregir el problema.  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que el Monitor de depuración remota de Visual Studio está instalado y en ejecución en el equipo remoto. Para obtener información sobre el depurador remoto y cómo instalarlo, vea [depuración remota](../debugger/remote-debugging.md).  
  
- En Visual Studio, examine las propiedades del proyecto (**Proyecto / Propiedades / Depuración**). Asegúrese de que el **nombre del servidor remoto** es correcto.  
  
- Compruebe que se tiene acceso al equipo remoto en la red.  
  
## <a name="the-remote-machine-is-not-reachable"></a>El equipo remoto no está accesible  
 Pruebe a hacer [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) a la máquina remota. Si no recibe respuesta al ping, las herramientas remotas no se podrán conectar tampoco. Pruebe a reiniciar el equipo remoto y, de lo contrario, asegúrese de que está configurado correctamente en la red.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versión del depurador remoto no coincide con la versión de Visual Studio  
 La versión de Visual Studio que se ejecuta localmente debe coincidir con la versión del monitor de depuración remota que se ejecuta en el equipo remoto. Para solucionar este problema, descargue e instale la versión correspondiente del monitor de depuración remota. Vaya a [suscripciones de Visual Studio](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) para encontrar la versión correcta del Depurador remoto para su versión de Visual Studio.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Los equipos locales y remotos tienen distintos modos de autenticación  

 Los equipos locales y remotos deben usar el mismo modo de autenticación. Para solucionar este problema, asegúrese de que ambos equipos usan el mismo modo de autenticación. Puede cambiar el modo de autenticación en el depurador remoto en el diálogo **Herramientas / Opciones** .  
  
 Para más información sobre la autenticación, vea [Información general de la autenticación de Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>El depurador remoto se ejecuta bajo una cuenta de usuario diferente  
 Puede resolver este problema de una de las siguientes formas:  
  
- Puede detener al depurador remoto y reiniciarlo con la cuenta que está usando en el equipo local.  
  
- Puede iniciar el depurador remoto desde la línea de comandos con el parámetro **/allow \<username>** : `msvsmon /allow <username@computer>`  
  
- Puede Agregar el usuario a los permisos del Depurador remoto (en la ventana del Depurador remoto, **herramientas/permisos**).  
  
- Si no puede usar los métodos descritos en los pasos anteriores, puede permitir que cualquier usuario realice la depuración remota. En la ventana del depurador remoto, vaya al cuadro de diálogo **Herramientas/Opciones** . Al seleccionar   **Sin autenticación**, podrá activar **Permitir que cualquier usuario depure**. Sin embargo, debe usar esta opción solo como último recurso o si se encuentra en una red privada.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>El firewall del equipo remoto no permite conexiones entrantes al depurador remoto  
 El firewall del equipo de Visual Studio y el firewall del equipo remoto deben configurarse para permitir la comunicación entre Visual Studio y el depurador remoto. Para obtener información sobre los puertos que usa el depurador remoto, vea [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Para obtener información sobre de cómo configurar el firewall de Windows, vea [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>El software antivirus está bloqueando las conexiones  
 Software antivirus de Windows permite las conexiones del depurador remoto, pero algunos programas antivirus de terceros pueden bloquearlas. Consulte la documentación de su software antivirus para averiguar cómo permitir estas conexiones.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La directiva de seguridad de red está bloqueando la comunicación entre el equipo remoto y Visual Studio  
 Revise la seguridad de la red para asegurarse de que no está bloqueando la comunicación. Para más información sobre la directiva de seguridad de red de Windows, vea [Administración de seguridad](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La red está demasiado ocupada para admitir la depuración remota  
 Puede que necesite realizar la depuración remota en otro momento o volver a programar un trabajo de la red correspondiente a otra hora distinta.  
  
## <a name="more-help"></a>Más ayuda  
 Para obtener ayuda sobre el depurador remoto, incluidos los modificadores de línea de comandos, abra la dirección siguiente en un explorador:  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Consulte también  
 [Remote Debugging](../debugger/remote-debugging.md)
