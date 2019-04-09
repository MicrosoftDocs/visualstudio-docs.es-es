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
ms.openlocfilehash: 600f34377e5901148149bb6e94c2277b37a435af
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2019
ms.locfileid: "59291707"
---
En el dispositivo remoto o servidor que desee depurar en, en lugar de la máquina de Visual Studio, descargue e instale la versión correcta de las herramientas remotas de uno de los vínculos en la tabla siguiente.

- Descargue las herramientas remotas más reciente para su versión de Visual Studio. La versión más reciente de herramientas remotas es compatible con versiones anteriores de Visual Studio, pero las versiones anteriores de herramientas remotas no son compatibles con versiones posteriores de Visual Studio.
- Descargue las herramientas remotas con la misma arquitectura que la máquina está instalando en. Por ejemplo, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, instale las herramientas remotas de 64 bits.

::: moniker range=">=vs-2019"

|Versión|Link|Notas|
|-|-|-|
|Visual Studio 2019 RC|[Herramientas remotas](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2019)|Es compatible con todas las versiones de Visual Studio de 2019. Descargue la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o ARM64). En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para descargar las herramientas remotas de ayuda.|
|Visual Studio 2017 (versión más reciente)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Es compatible con todas las versiones de Visual Studio 2017. Descargue la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o ARM64). En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para descargar las herramientas remotas de ayuda.|
|Visual Studio 2015|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Herramientas remotas para Visual Studio 2015 están disponibles en My.VisualStudio.com. Si se le solicite, únase a la versión gratuita [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programa o inicie sesión con su identificador de suscripción de Visual Studio. En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para descargar las herramientas remotas de ayuda.|
|Visual Studio 2013|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Descargar página de documentación de Visual Studio 2013|
|Visual Studio 2012|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Descargar página de documentación de Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Versión|Link|Notas|
|-|-|-|
|Visual Studio 2017 (versión más reciente)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Es compatible con todas las versiones de Visual Studio 2017. Descargue la versión que coincida con el sistema operativo del dispositivo (x 86, x64 o ARM64). En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para descargar las herramientas remotas de ayuda.|
|Visual Studio 2015|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Herramientas remotas para Visual Studio 2015 están disponibles en My.VisualStudio.com. Si se le solicite, únase a la versión gratuita [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programa o inicie sesión con su identificador de suscripción de Visual Studio. En Windows Server, vea [desbloquear la descarga del archivo](../../debugger/remote-debugging-unblock-file-download.md) para descargar las herramientas remotas de ayuda.|
|Visual Studio 2013|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Descargar página de documentación de Visual Studio 2013|
|Visual Studio 2012|[Herramientas remotas](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Descargar página de documentación de Visual Studio 2012|

::: moniker-end

Puede ejecutar el depurador remoto copiando *msvsmon.exe* para el equipo remoto, en lugar de instalar las herramientas remotas. Sin embargo, el Asistente para configuración de Remote Debugger (*rdbgwiz.exe*) está disponible solo al instalar las herramientas remotas. Es posible que deba usar al Asistente para configuración si desea ejecutar al depurador remoto como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Para depurar aplicaciones de Windows 10 en dispositivos ARM, utilice ARM64, que está disponible con la versión más reciente de las herramientas remotas.
>- Para depurar aplicaciones de Windows 10 en dispositivos Windows RT, use ARM, que solo está disponible en las descargas de herramientas remotas de Visual Studio 2015.
