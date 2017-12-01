---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 109d9d8718a2c46dbd982e58b22dcf43e55b2205
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2017
---
1.  En el dispositivo o servidor máquina que se va a depurar (en lugar de la máquina que ejecuta Visual Studio), obtener la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Visual Studio 2017 Update 4|[Herramientas remotas](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Siempre descargar la versión que coincida con el sistema operativo del dispositivo (x86 o x x64). Para los exploradores más antiguos, use estos vínculos directos: [herramientas remotas (x64)](https://go.microsoft.com/fwlink/?LinkId=746570&clcid=0x409) y [herramientas remotas (x86)](https://go.microsoft.com/fwlink/?LinkId=746569&clcid=0x409).|
    |Visual Studio de 2017 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Si se le solicita, unirse al grupo de Visual Studio Dev Essentials libre o puede iniciar sesión con una suscripción válida a Visual Studio. Para los exploradores más antiguos, debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, unirse al grupo de Visual Studio Dev Essentials libre o puede iniciar sesión con una suscripción válida a Visual Studio. Para los exploradores más antiguos, debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, unirse al grupo de Visual Studio Dev Essentials libre o puede iniciar sesión con una suscripción válida a Visual Studio. Para los exploradores más antiguos, debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2013 de descarga|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2012 de descarga|
  
2.  En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (x 86, x64 o ARM) y descargue las herramientas remotas.
  
    > [!IMPORTANT]
    >  Se recomienda que instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coinciden. Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desea instalar. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto. 
    >   
    >  Superficie 3 cambia de ARM a x64 arquitectura. Una versión ARM de las herramientas remotas no está disponible para Visual Studio de 2017. Para Visual Studio 2015, busque la versión ARM en la descarga de Visual Studio 2015 RTW.
  
3.  Cuando haya terminado de descargar el archivo ejecutable, vaya a la sección siguiente y siga las instrucciones de instalación.

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que la **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) se instala solo cuando se descarga el herramientas. Debe utilizar el Asistente para configuración más adelante, especialmente si desea que el depurador remoto para que se ejecute como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](../../debugger/remote-debugging.md#bkmk_configureService).