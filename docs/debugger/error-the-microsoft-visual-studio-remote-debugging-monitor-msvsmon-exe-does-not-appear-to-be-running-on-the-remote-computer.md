---
title: 'Error: El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
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
ms.openlocfilehash: 683af8cf0c75068a58b5e8cf4732cdf69c586d4f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Error: El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto.
Este mensaje de error significa que Visual Studio no pudo encontrar una instancia correcta del Monitor de depuración remota de Visual Studio en el equipo remoto. El Monitor de depuración remota de Visual Studio debe estar instalado para que funcione la depuración remota. Para obtener información sobre cómo descargar y configurar el depurador remoto, consulte [depuración remota](../debugger/remote-debugging.md).  
  
> [!IMPORTANT]
>  Si cree que ha recibido este mensaje debido a un error en el producto, inicie [notifique este problema a Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Si necesita más ayuda, vea [Talk to Us](../ide/talk-to-us.md) para obtener información sobre las distintas formas de ponerse en contacto con Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Recibí este mensaje mientras estaba depurando en Visual Studio 2010 o versiones anteriores  
 Si la versión de Visual Studio que está usando es Visual Studio 2010 o versiones anteriores, es posible que reciba este error si el uso compartido de archivos e impresoras no está habilitado. Para obtener más información acerca de este problema, consulte la versión de Visual Studio 2010 de esta documentación: [Error: The Microsoft Visual Studio Monitor de depuración remota (MSVSMON. (EXE) no parece estar ejecutándose en el equipo remoto. -Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Recibí este mensaje mientras estaba depurando localmente  
 Si recibe este mensaje mientras depura localmente, es posible que un software antivirus o firewall de terceros sea el culpable. Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Los dos procesos se comunican con la red local en el equipo local. No sale ningún tráfico del equipo, pero es posible que el software de seguridad de terceros bloquee la comunicación.  
  
 Las siguientes secciones enumeran algunas otras razones por las que puede aparecer este mensaje, así como lo que puede hacer para corregir el problema.  
  
## <a name="the-remote-machine-is-not-reachable"></a>El equipo remoto no está accesible  
 Pruebe a hacer [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) a la máquina remota. Si no recibe respuesta al ping, las herramientas remotas no puedan conectar tampoco. Pruebe a reiniciar el equipo remoto y, de lo contrario, asegúrese de que está configurado correctamente en la red.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versión del depurador remoto no coincide con la versión de Visual Studio  
 La versión de Visual Studio que se ejecuta localmente debe coincidir con la versión del monitor de depuración remota que se ejecuta en el equipo remoto. Para solucionar este problema, descargue e instale la versión correspondiente del monitor de depuración remota. Vaya al [Centro de descarga](http://www.microsoft.com/en-us/download) para buscar la versión adecuada del depurador remoto.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Los equipos locales y remotos tienen distintos modos de autenticación  
 Los equipos locales y remotos deben usar el mismo modo de autenticación. Para solucionar este problema, asegúrese de que ambos equipos usan el mismo modo de autenticación. Para más información sobre la autenticación, vea [Información general de la autenticación de Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>El depurador remoto se ejecuta bajo una cuenta de usuario diferente  
 Puede resolver este problema de una de las siguientes formas:  
  
-   Puede detener al depurador remoto y reiniciarlo con la cuenta que está usando en el equipo local.  
  
-   Puede iniciar el depurador remoto desde la línea de comandos con el **/ allow \<nombre de usuario >** parámetro: `msvsmon /allow <username@computer>`  
  
-   Puede agregar el usuario a los permisos del depurador remoto (en la ventana del depurador remoto, **Herramientas > permisos**).  
  
-   Si no puede usar los métodos descritos en los pasos anteriores, puede permitir que cualquier usuario realice la depuración remota. En la ventana del depurador remoto, vaya a la **Herramientas > opciones** cuadro de diálogo. Al seleccionar   **Sin autenticación**, podrá activar **Permitir que cualquier usuario depure**. Sin embargo, debe usar esta opción solo como último recurso o si se encuentra en una red privada.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>El firewall en el equipo remoto no permite conexiones entrantes al depurador remoto  
 El firewall del equipo de Visual Studio y el firewall del equipo remoto deben configurarse para permitir la comunicación entre Visual Studio y el depurador remoto. Para obtener información sobre los puertos que usa el depurador remoto, vea [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Para obtener información sobre de cómo configurar el firewall de Windows, vea [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>El software antivirus está bloqueando las conexiones  
 Software antivirus de Windows permite las conexiones del depurador remoto, pero algunos programas antivirus de terceros pueden bloquearlas. Consulte la documentación de su software antivirus para averiguar cómo permitir estas conexiones.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La directiva de seguridad de red está bloqueando la comunicación entre el equipo remoto y Visual Studio  
 Revise la seguridad de la red para asegurarse de que no está bloqueando la comunicación. Para obtener más información acerca de la directiva de seguridad de red de Windows, vea [configuración de la directiva de seguridad](/windows/device-security/security-policy-settings/security-policy-settings).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La red está demasiado ocupada para admitir la depuración remota  
 Puede que necesite realizar la depuración remota en otro momento o volver a programar un trabajo de la red correspondiente a otra hora distinta.  
  
## <a name="more-help"></a>Más ayuda  
 Para obtener ayuda de depurador remoto, incluidos los modificadores de línea de comandos, haga clic en **Ayuda > uso de** en la ventana del depurador remoto. Si no tiene abierta puede ver la página web mediante la copia de la siguiente línea a un **Explorador de archivos** ventana. (Es necesario reemplazar \<directorio de instalación de Visual Studio > con la ubicación de la instalación de Visual Studio.)  
  
 res: / /*\<directorio de instalación de Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)