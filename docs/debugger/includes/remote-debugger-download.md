---
title: Descarga del depurador remoto
description: Vínculos de descarga para el depurador remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809263"
---
1.  En el dispositivo o servidor máquina que desea depurar (en lugar de la máquina que ejecuta Visual Studio), obtenga la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Visual Studio 2017 (versión más reciente)|[Herramientas remotas](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Descargar siempre la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o ARM64). En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda para descargar las herramientas remotas.|
    |Visual Studio 2017 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Herramientas remotas para versiones anteriores de Visual Studio 2017 están disponibles en My.VisualStudio.com. Si se le solicita, Id. del grupo de Visual Studio Dev Essentials gratuita de combinación o inicie sesión con su suscripción de Visual Studio En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda para descargar las herramientas remotas.|
    |Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, Id. del grupo de Visual Studio Dev Essentials gratuita de combinación o inicie sesión con su suscripción de Visual Studio En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging.md#unblock_msvsmon) para obtener ayuda para descargar las herramientas remotas.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Descargar página de documentación de Visual Studio 2013|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Descargar página de documentación de Visual Studio 2012|

2.  En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (x86, x64, ARM o ARM64) y descargue las herramientas remotas.

    > [!IMPORTANT]
    >  Se recomienda que instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coinciden. Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desee instalarlo. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto.
    >
    >  Para depurar en Windows 10 en dispositivos ARM, elija la descarga de ARM64 disponible con la versión más reciente de las herramientas remotas.  Los dispositivos Windows RT, elija la versión ARM, que solo está disponible en la descarga de Visual Studio 2015 RTW.

3.  Cuando haya terminado de descargar el archivo ejecutable, vaya a la sección siguiente y siga las instrucciones de configuración.

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que el **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) se instala solo al descargar la herramientas. Es posible que deba usar al Asistente para configuración más adelante, especialmente si desea que el depurador remoto para ejecutarse como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](../../debugger/remote-debugging.md#bkmk_configureService).
