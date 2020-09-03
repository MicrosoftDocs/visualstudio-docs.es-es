---
title: 'Error: No es posible iniciar la depuración en el servidor web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185483"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: No es posible iniciar la depuración en el servidor web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se intenta depurar una aplicación de ASP.NET que se ejecuta en un servidor web, puede obtener este mensaje de error: No se puede iniciar la depuración en el servidor Web.
  
En muchos casos, este error se produce porque IIS no está configurado correctamente.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Comprobación de la configuración de IIS

Después de seguir los pasos para resolver un problema detallado aquí y antes de volver a intentar la depuración, es posible que también tenga que restablecer IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset` o puede hacerlo en el administrador de IIS. 

* Detenga y reinicie los grupos de aplicaciones y vuelva a intentarlo.

    Puede que el grupo de aplicaciones se haya detenido u otro cambio de configuración que haya realizado puede requerir que detenga y reinicie el grupo de aplicaciones.
    
    > [!NOTE]
    > Si el grupo de aplicaciones se detiene, puede que tenga que desinstalar el módulo URL Rewrite del panel de control y, a continuación, volver a instalarlo mediante el instalador de plataforma web (WPI). Esto podría ser un problema después de una actualización importante del sistema.

* Compruebe la configuración del grupo de aplicaciones, corríjala si es necesario y vuelva a intentarlo.

    Si las credenciales de contraseña han cambiado, puede que tenga que actualizarlas en el grupo de aplicaciones. Además, si ha instalado ASP.NET recientemente, es posible que el grupo de aplicaciones esté configurado para la versión incorrecta de ASP.NET. Corrija el problema y reinicie el grupo de aplicaciones.
    
* Compruebe que la carpeta de la aplicación web tiene los permisos adecuados.

    Asegúrese de conceder a IIS_IUSRS o IUSR (o al usuario específico asociado al grupo de aplicaciones) derechos de lectura y ejecución para la carpeta de la aplicación Web. Corrija la incidencia y reinicie el grupo de aplicaciones.

* Si usa un archivo HOSTS con direcciones locales, pruebe a usar la dirección de bucle invertido en lugar de la dirección IP del equipo.

* Abra la página localhost en el explorador.

     Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.
     
     Para obtener información acerca de la implementación en IIS, vea [depuración remota ASP.net en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o, por ASP.net Core, [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Asegúrese de que en IIS está instalada la versión correcta de ASP.NET.  Vea [implementar una aplicación de ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) o, por ASP.net Core, [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Cree una aplicación ASP.NET básica en el servidor.

     Si no consigue que la aplicación funcione con el depurador, intente crear una aplicación ASP.NET básica localmente en el servidor y depurarla. Si puede depurar una aplicación básica, esto puede ayudarle a identificar las diferencias entre las dos configuraciones.
  
* Resolver errores de autenticación si solo usa la dirección IP

     De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Si el sitio web está configurado en IIS para requerir autenticación, se producirá un error de autenticación. Para corregir este problema, puede especificar el nombre del equipo remoto, en lugar de la dirección IP.
     
## <a name="other-causes"></a>Otras causas

Si usa una versión anterior de Visual Studio:

- Reinicie Visual Studio con privilegios elevados e inténtelo de nuevo.

    Un error en versiones anteriores (corregido más adelante) requería privilegios elevados en algunos escenarios de depuración de ASP.NET.
    
- Si se están ejecutando varias instancias de Visual Studio, vuelva a abrir el proyecto en una instancia de Visual Studio e inténtelo de nuevo.

## <a name="see-also"></a>Consulte también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
