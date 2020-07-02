---
title: Asignaciones de puertos del depurador remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542108"
---
# <a name="remote-debugger-port-assignments"></a>Asignaciones de puertos del depurador remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El depurador remoto de Visual Studio se puede ejecutar como una aplicación o como un servicio en segundo plano. Cuando se ejecuta como una aplicación, usa un puerto asignado de forma predeterminada como se muestra a continuación:  
  
- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  En otras palabras, el número de puerto asignado al depurador remoto se incrementa en 2 para cada versión. Puede establecer un número de puerto distinto según desee. Explicaremos cómo establecer números de puerto en una sección posterior.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Puerto del depurador remoto en sistemas operativos de 32 bits  
 El puerto TCP 4020 (en Visual Studio de 2015) es el puerto principal y el necesario para todos los escenarios. Puede configurar este puerto desde la línea de comandos o en la ventana del depurador remoto.  
  
 En la ventana del Depurador remoto, haga clic en **herramientas/opciones**y establezca el número de puerto TCP/IP.  
  
 En la línea de comandos, inicie el depurador remoto con el modificador **/Port** : **msvsmon/Port \<port number> **.  
  
 Puede encontrar todos los modificadores de la línea de comandos del Depurador remoto en la ayuda de depuración remota (presione **F1** o haga clic en **ayuda/uso** en la ventana del Depurador remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Puerto del depurador remoto en sistemas operativos de 64 bits  
 Cuando se inicia la versión de 64 bits del depurador remoto, este usa el puerto 4020 de manera predeterminada.  Si depura un proceso de 32 bits, la versión de 64 bits del depurador remoto inicia una versión de 32 bits del depurador remoto en el puerto 4021. Si ejecuta el depurador remoto de 32 bits, usa el puerto 4020 y no usa el puerto 4021.  
  
 Este puerto se puede configurar desde la línea de comandos: **msvsmon/wow64port \<port number> **.  
  
## <a name="the-discovery-port"></a>Puerto de detección  
 UDP 3702 se usa para buscar instancias en ejecución del depurador remoto en la red (por ejemplo, el cuadro de diálogo **Buscar** en el cuadro de diálogo **Asociar al proceso** ). Se usa solo para detectar una máquina que ejecute el depurador remoto, por lo que es opcional si tiene alguna otra manera de conocer el nombre del equipo o la dirección IP del equipo de destino. Se trata de un puerto estándar para la detección, por lo que no es posible configurar el número de puerto.  
  
 Si no quiere habilitar la detección, puede iniciar msvsmon desde la línea de comandos con la detección deshabilitada:  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Puertos del depurador remoto en Azure  
 El depurador remoto en Azure usa los puertos siguientes. Los puertos del servicio en la nube se asignan a los puertos en la máquina virtual individual. Todos los puertos son TCP.  

|**Connection**|**Puerto en el servicio en la nube**|**Puerto en la máquina virtual**|  
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Consulte también  
 [Remote Debugging](../debugger/remote-debugging.md)
