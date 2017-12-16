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
ms.openlocfilehash: 7e911686d1f8bff191c439f4fc2b92c37d60a31f
ms.sourcegitcommit: 38097344f3ff74ba7b03bcfa45910015ca6bc2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2017
---
1.  En el dispositivo o servidor máquina que se va a depurar (en lugar de la máquina que ejecuta Visual Studio), obtener la versión correcta de las herramientas remotas.

    |Versión|Vínculo|Notas|
    |-|-|-|
    |Versión 15.5 de Visual Studio 2017|[Herramientas remotas](https://www.visualstudio.com/downloads/#remote-tools-for-visual-studio-2017)|Siempre descargar la versión que coincida con el sistema operativo del dispositivo (x86 o x x64). Si se habilita el modo de seguridad mejorada (Windows Server), debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio de 2017 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Herramientas remotas para versiones anteriores de Visual Studio de 2017 están disponibles en My.VisualStudio.com. Si se le solicita, combinación del grupo de Visual Studio Dev Essentials libre o inicie sesión con su suscripción de Visual Studio identificador. Si se habilita el modo de seguridad mejorada (Windows Server), debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2015 Update 3|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, combinación del grupo de Visual Studio Dev Essentials libre o inicie sesión con su suscripción de Visual Studio identificador. Si se habilita el modo de seguridad mejorada (Windows Server), debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2015 (antigua)|[Herramientas remotas](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Si se le solicita, combinación del grupo de Visual Studio Dev Essentials libre o inicie sesión con su suscripción de Visual Studio identificador. Si se habilita el modo de seguridad mejorada (Windows Server), debe agregar nuevos sitios de confianza si se le solicita.|
    |Visual Studio 2013|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2013 de descarga|
    |Visual Studio 2012|[Herramientas remotas](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Página en la documentación de Visual Studio 2012 de descarga|
  
2.  En la página de descarga, elija la versión de las herramientas que coincida con el sistema operativo (x 86, x64 o ARM) y descargue las herramientas remotas.
  
    > [!IMPORTANT]
    >  Se recomienda que instalar la versión más reciente de las herramientas remotas que coincida con su versión de Visual Studio. No se recomiendan las versiones no coinciden. Además, debe instalar las herramientas remotas que tienen la misma arquitectura que el sistema operativo en el que desea instalar. En otras palabras, si desea depurar una aplicación de 32 bits en un equipo remoto ejecuta un sistema operativo de 64 bits, debe instalar la versión de 64 bits de las herramientas remotas en el equipo remoto. 
    >   
    >  Superficie 3 cambia de ARM a x64 arquitectura. Una versión ARM de las herramientas remotas no está disponible para Visual Studio de 2017. Para Visual Studio 2015, busque la versión ARM en la descarga de Visual Studio 2015 RTW.
  
3.  Cuando haya terminado de descargar el archivo ejecutable, vaya a la sección siguiente y siga las instrucciones de instalación.

Si intenta copiar el depurador remoto (msvsmon.exe) en el equipo remoto y ejecutarlo, tenga en cuenta que la **Asistente para configuración de Remote Debugger** (**rdbgwiz.exe**) se instala solo cuando se descarga el herramientas. Debe utilizar el Asistente para configuración más adelante, especialmente si desea que el depurador remoto para que se ejecute como un servicio. Para obtener más información, consulte [(opcional) configurar el depurador remoto como un servicio](../../debugger/remote-debugging.md#bkmk_configureService).