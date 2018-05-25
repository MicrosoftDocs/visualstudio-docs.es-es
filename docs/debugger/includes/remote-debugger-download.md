---
title: Descarga del depurador remoto
description: Vínculos de descarga para que el depurador remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 358dc0b457381bb56532e6cae1156aac9ea2dba2
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
1.  En el dispositivo o servidor máquina que se va a depurar (en lugar de la máquina que ejecuta Visual Studio), obtener la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Visual Studio 2017 (última versión)|[Herramientas remotas](https://www.visualstudio.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Siempre descargar la versión que coincida con el sistema operativo del dispositivo (x86 o x x64). En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda descargar las herramientas remotas.|
    |Visual Studio de 2017 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Herramientas remotas para versiones anteriores de Visual Studio de 2017 están disponibles en My.VisualStudio.com. Si se le solicita, combinación del grupo de Visual Studio Dev Essentials libre o inicie sesión con su suscripción de Visual Studio identificador. En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda descargar las herramientas remotas.|
    |Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, combinación del grupo de Visual Studio Dev Essentials libre o inicie sesión con su suscripción de Visual Studio identificador. En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda descargar las herramientas remotas.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2013 de descarga|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2012 de descarga|
  
2.  En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (x 86, x64 o ARM) y descargue las herramientas remotas.
  
    > [!IMPORTANT]
    >  Se recomienda que instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coinciden. Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desea instalar. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto. 
    >   
    >  Superficie 3 cambia de ARM a x64 arquitectura. Una versión ARM de las herramientas remotas no está disponible para Visual Studio de 2017. Para Visual Studio 2015, busque la versión ARM en la descarga de Visual Studio 2015 RTW.
  
3.  Cuando haya terminado de descargar el archivo ejecutable, vaya a la sección siguiente y siga las instrucciones de instalación.

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que la **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) se instala solo cuando se descarga el herramientas. Debe utilizar el Asistente para configuración más adelante, especialmente si desea que el depurador remoto para que se ejecute como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](../../debugger/remote-debugging.md#bkmk_configureService).
