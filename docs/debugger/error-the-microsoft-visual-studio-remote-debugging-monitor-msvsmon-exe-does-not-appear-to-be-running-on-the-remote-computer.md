---
title: "Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecut&#225;ndose en el equipo remoto. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Error: El Monitor de depuraci&#243;n remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecut&#225;ndose en el equipo remoto.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este mensaje de error significa que Visual Studio no pudo encontrar una instancia correcta del Monitor de depuración remota de Visual Studio en el equipo remoto. El Monitor de depuración remota de Visual Studio debe estar instalado para que funcione la depuración remota. Para información sobre cómo descargar y configurar el depurador remoto, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
> [!IMPORTANT]
>  Si cree que ha recibido este mensaje debido a un error en el producto, notifique este problema a Visual Studio [Enviar una sonrisa](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md). Si necesita más ayuda, vea [Hable con nosotros](../ide/talk-to-us.md) para obtener información sobre las distintas formas de ponerse en contacto con Microsoft.  
  
## Recibí este mensaje mientras estaba depurando en Visual Studio 2010 o versiones anteriores  
 Si la versión de Visual Studio que está usando es Visual Studio 2010 o versiones anteriores, es posible que reciba este error si el uso compartido de archivos e impresoras no está habilitado. Para más información sobre este problema, vea la versión de Visual Studio 2010 de esta documentación: [Error: El Monitor de depuración remota de Microsoft Visual Studio \(MSVSMON.EXE\) no parece estar ejecutándose en el equipo remoto \- Visual Studio 2010.](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## Recibí este mensaje mientras estaba depurando localmente  
 Si recibe este mensaje mientras depura localmente, es posible que un software antivirus o firewall de terceros sea el culpable. Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Los dos procesos se comunican con la red local en el equipo local. No sale ningún tráfico del equipo, pero es posible que el software de seguridad de terceros bloquee la comunicación.  
  
 Las siguientes secciones enumeran algunas otras razones por las que puede aparecer este mensaje, así como lo que puede hacer para corregir el problema.  
  
## El equipo remoto no está accesible  
 Pruebe a hacer [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) a la máquina remota. Si no recibe respuesta al ping, las herramientas remotas no se podrán conectar tampoco. Pruebe a reiniciar el equipo remoto y, de lo contrario, asegúrese de que está configurado correctamente en la red.  
  
## La versión del depurador remoto no coincide con la versión de Visual Studio  
 La versión de Visual Studio que se ejecuta localmente debe coincidir con la versión del monitor de depuración remota que se ejecuta en el equipo remoto. Para solucionar este problema, descargue e instale la versión correspondiente del monitor de depuración remota. Vaya al [Centro de descarga](http://www.microsoft.com/en-us/download) para buscar la versión adecuada del depurador remoto.  
  
## Los equipos locales y remotos tienen distintos modos de autenticación  
 Los equipos locales y remotos deben usar el mismo modo de autenticación. Para solucionar este problema, asegúrese de que ambos equipos usan el mismo modo de autenticación. Para más información sobre la autenticación, vea [Información general de la autenticación de Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## El depurador remoto se ejecuta bajo una cuenta de usuario diferente  
 Puede resolver este problema de una de las siguientes formas:  
  
-   Puede detener al depurador remoto y reiniciarlo con la cuenta que está usando en el equipo local.  
  
-   Puede iniciar el depurador remoto desde la línea de comandos con el parámetro  **\/allow \<nombre de usuario\>**: `msvsmon /allow <username@computer>`  
  
-   Puede agregar el usuario a los permisos del depurador remoto \(en la ventana del depurador remoto, **Herramientas \/ Permisos**\).  
  
-   Si no puede usar los métodos descritos en los pasos anteriores, puede permitir que cualquier usuario realice la depuración remota. En la ventana del depurador remoto, vaya al cuadro de diálogo **Herramientas\/Opciones**. Al seleccionar **Sin autenticación**, podrá activar **Permitir que cualquier usuario depure**. Sin embargo, debe usar esta opción solo como último recurso o si se encuentra en una red privada.  
  
## El firewall del equipo remoto no permite conexiones entrantes al depurador remoto  
 El firewall del equipo de Visual Studio y el firewall del equipo remoto deben configurarse para permitir la comunicación entre Visual Studio y el depurador remoto. Para obtener información sobre los puertos que usa el depurador remoto, vea [Asignaciones de puertos del depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obtener información sobre de cómo configurar el firewall de Windows, vea [Configurar el Firewall de Windows para la depuración remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## El software antivirus está bloqueando las conexiones  
 Software antivirus de Windows permite las conexiones del depurador remoto, pero algunos programas antivirus de terceros pueden bloquearlas. Consulte la documentación de su software antivirus para averiguar cómo permitir estas conexiones.  
  
## La directiva de seguridad de red está bloqueando la comunicación entre el equipo remoto y Visual Studio  
 Revise la seguridad de la red para asegurarse de que no está bloqueando la comunicación. Para más información sobre la directiva de seguridad de red de Windows, vea [Administración de seguridad](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## La red está demasiado ocupada para admitir la depuración remota  
 Puede que necesite realizar la depuración remota en otro momento o volver a programar un trabajo de la red correspondiente a otra hora distinta.  
  
## Más ayuda  
 Para obtener ayuda sobre el depurador remoto, incluidos los modificadores de línea de comandos, abra la dirección siguiente en un explorador:  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## Vea también  
 [Errores de la depuración remota y sus soluciones](../debugger/remote-debugging-errors-and-troubleshooting.md)