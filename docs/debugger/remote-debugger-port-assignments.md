---
title: Las asignaciones de puerto del depurador remoto | Documentos de Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 05/18/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab48d9b6a67563171e28dab1f08e496750585288
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476054"
---
# <a name="remote-debugger-port-assignments"></a>Asignaciones de puertos del depurador remoto
El depurador remoto de Visual Studio se puede ejecutar como una aplicación o como un servicio en segundo plano. Cuando se ejecuta como una aplicación, usa un puerto asignado de forma predeterminada como se muestra a continuación:  

-   Visual Studio 2017:4022

-   Visual Studio 2015: 4020  
  
-   Visual Studio 2013: 4018  
  
-   Visual Studio 2012: 4016  
  
 En otras palabras, el número de puerto asignado al depurador remoto se incrementa en 2 para cada versión. Puede establecer un número de puerto distinto según desee. Explicaremos cómo establecer números de puerto en una sección posterior.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Puerto del depurador remoto en sistemas operativos de 32 bits  
 TCP 4022 (en Visual Studio de 2017) es el puerto principal y se requiere para todos los escenarios. Puede configurar este puerto desde la línea de comandos o en la ventana del depurador remoto.  
  
 En la ventana del depurador remoto, haga clic en **Herramientas > opciones**y establecer el número de puerto TCP/IP.  
  
 En la línea de comandos, iniciar el depurador remoto con la **/puerto** cambiar: **msvsmon /port \<número de puerto >**.  
  
 Puede encontrar todo el depurador remoto modificadores de línea de comandos en la Ayuda de depuración remota (presione **F1** o haga clic en **Ayuda > uso de** en la ventana del depurador remoto).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Puerto del depurador remoto en sistemas operativos de 64 bits  
 Cuando se inicia la versión de 64 bits del depurador remoto, usa el puerto 4022 de forma predeterminada.  Si depura un proceso de 32 bits, la versión de 64 bits del depurador remoto inicia una versión de 32 bits del depurador remoto en el puerto 4023. Si ejecuta al depurador remoto de 32 bits, usa 4022 y 4023 no se utiliza.  
  
 Este puerto es configurable desde la línea de comandos: **Msvsmon /wow64port \<número de puerto >**.  
  
## <a name="the-discovery-port"></a>Puerto de detección  
 UDP 3702 se usa para buscar instancias en ejecución del depurador remoto en la red (por ejemplo, el cuadro de diálogo **Buscar** en el cuadro de diálogo **Asociar al proceso** ). Se usa solo para detectar una máquina que ejecute el depurador remoto, por lo que es opcional si tiene alguna otra manera de conocer el nombre del equipo o la dirección IP del equipo de destino. Se trata de un puerto estándar para la detección, por lo que no es posible configurar el número de puerto.  
  
 Si no desea habilitar la detección, puede iniciar msvsmon desde la línea de comandos con la detección deshabilitada:  **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Puertos del depurador remoto en Azure  
 El depurador remoto en Azure usa los puertos siguientes. Los puertos del servicio en la nube se asignan a los puertos en la máquina virtual individual. Todos los puertos son TCP.  
  
||||  
|-|-|-|  
|**Conexión**|**Puerto en el servicio en la nube**|**Puerto en la máquina virtual**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Vea también  
 [Depuración remota](../debugger/remote-debugging.md)