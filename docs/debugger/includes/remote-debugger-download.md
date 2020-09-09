---
title: Descarga del depurador remoto
description: Vínculos de descarga del depurador remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89325217"
---
En el dispositivo o servidor remoto en el que desea depurar, en lugar de en el equipo de Visual Studio, descargue e instale la versión correcta de las herramientas remotas desde los vínculos de la tabla siguiente.

- Descargue las herramientas remotas más recientes para su versión de Visual Studio. La última versión de las herramientas remotas es compatible con versiones anteriores de Visual Studio, pero las versiones anteriores de las herramientas remotas no son compatibles con versiones posteriores de Visual Studio. (Por ejemplo, si usa Visual Studio 2017, descargue la última actualización de las herramientas remotas para Visual Studio 2017. En este escenario, no descargue las herramientas remotas para Visual Studio 2019).
- Descargue las herramientas remotas con la misma arquitectura que el equipo en el que las va a instalar. Por ejemplo, si desea depurar una aplicación de 32 bits en un equipo remoto que ejecuta un sistema operativo de 64 bits, instale las herramientas remotas de 64 bits.

::: moniker range=">=vs-2019"

|Versión|Link|Notas|
|-|-|-|
|Visual Studio 2019|[Herramientas remotas](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Compatible con todas las versiones de Visual Studio 2019. Descargue la versión que coincida con el sistema operativo del dispositivo (x86, x64 o ARM64). En Windows Server, vea [Desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para obtener ayuda con la descarga de las herramientas remotas.|
|Visual Studio 2017|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatible con todas las versiones de Visual Studio 2017. Descargue la versión que coincida con el sistema operativo del dispositivo (x86, x64 o ARM64). En Windows Server, vea [Desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para obtener ayuda con la descarga de las herramientas remotas.|
|Visual Studio 2015|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Las Herramientas remotas para Visual Studio 2015 están disponibles en My.VisualStudio.com. Si se le solicita, únase al programa gratuito [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) o inicie sesión con su identificador de suscripción de Visual Studio. En Windows Server, vea [Desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para obtener ayuda con la descarga de las herramientas remotas.|
|Visual Studio 2013|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Página de descarga en la documentación de Visual Studio 2013|
|Visual Studio 2012|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Página de descarga de la documentación de Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Versión|Link|Notas|
|-|-|-|
|Visual Studio 2017|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatible con todas las versiones de Visual Studio 2017. Descargue la versión que coincida con el sistema operativo del dispositivo (x86, x64 o ARM64). En Windows Server, vea [Desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para obtener ayuda con la descarga de las herramientas remotas. Para obtener la última versión de las herramientas remotas, abra el [documento de Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Las Herramientas remotas para Visual Studio 2015 están disponibles en My.VisualStudio.com. Si se le solicita, únase al programa gratuito [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) o inicie sesión con su identificador de suscripción de Visual Studio. En Windows Server, vea [Desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para obtener ayuda con la descarga de las herramientas remotas.|
|Visual Studio 2013|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Página de descarga en la documentación de Visual Studio 2013|
|Visual Studio 2012|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Página de descarga de la documentación de Visual Studio 2012|

::: moniker-end

Puede ejecutar el depurador remoto mediante la copia de *msvsmon.exe* en el equipo remoto, en lugar de instalar las herramientas remotas. Sin embargo, el Asistente para configuración de Remote Debugger (*rdbgwiz.exe*) solo está disponible cuando se instalan las herramientas remotas. Es posible que tenga que usar el Asistente para configuración si desea ejecutar el depurador remoto como un servicio. Para más información, vea [(Opcional) Configuración del depurador remoto como servicio](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Para depurar aplicaciones de Windows 10 en dispositivos ARM, use ARM64, que está disponible con la última versión de las herramientas remotas.
>- Para depurar aplicaciones de Windows 10 en dispositivos Windows RT, use ARM, que solo está disponible en la descarga de las herramientas remotas de Visual Studio 2015.
