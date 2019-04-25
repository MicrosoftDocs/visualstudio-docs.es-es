---
title: 'Error: No se puede iniciar la depuración en el servidor Web | Documentos de Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048767"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: No es posible iniciar la depuración en el servidor web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al intentar depurar una aplicación de ASP.NET que se ejecutan en un servidor Web, obtendrá este mensaje de error: No se puede iniciar la depuración en el servidor Web.
  
En muchos casos, este error se produce porque IIS no está configurado correctamente.

## <a name="vxtbshttpservererrorsthingstocheck"></a> Compruebe la configuración de IIS

Después de llevar a cabo pasos para resolver un problema detallado aquí y antes de intentar de nuevo depurar, es posible que deba restablecer IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset`, o puede hacerlo en el Administrador de IIS. 

* Detener y reiniciar los grupos de aplicaciones, vuelva a intentarlo.

    El grupo de aplicaciones se haya detenido u otro cambio de configuración que ha realizado puede requerir que se detenga y reinicie el grupo de aplicaciones.
    
    > [!NOTE]
    > Si mantiene detener el grupo de aplicaciones, es posible que deba desinstalar el módulo URL Rewrite desde el Panel de Control y, a continuación, vuelva a instalar mediante el instalador de plataforma Web (WPI). Esto podría ser un problema después de una actualización del sistema significativos.

* Compruebe la configuración del grupo de aplicaciones, corrija si es necesario y, a continuación, vuelva a intentar.

    Si han cambiado las credenciales de contraseña, deberá actualizarlos en el grupo de aplicaciones. Además, si recientemente ha instalado ASP.NET, el grupo de aplicaciones puede configurarse para una versión de ASP.NET. Corrija el problema y reinicie el grupo de aplicaciones.
    
* Compruebe que la carpeta de aplicación Web tiene los permisos adecuados.

    Asegúrese de que se asigne a IIS_IUSRS o IUSR (o el usuario específico asociado con el grupo de aplicaciones) de lectura y ejecución de derechos para la carpeta de aplicación Web. Corrija el problema y reinicie el grupo de aplicaciones.

* Si está utilizando un archivo de HOSTS con direcciones locales, pruebe a usar la dirección de bucle invertido en lugar de la dirección IP del equipo.

* Abrir la página de localhost en el explorador.

     Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.
     
     Para obtener información sobre la implementación en IIS, consulte [Remote Debugging ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o, para ASP.NET Core, [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Asegúrese de que está instalada la versión correcta de ASP.NET en IIS.  Consulte [implementar una aplicación ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) o, para ASP.NET Core, [publicar en IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Crear una aplicación ASP.NET básica en el servidor.

     Si no se puede obtener la aplicación para que funcione con el depurador, intente crear una aplicación ASP.NET básica localmente en el servidor e intente depurar la aplicación básica. Si se puede depurar una aplicación básica, que puede ayudarle a identificar cuál es la diferencia entre las dos configuraciones.
  
* Resolver errores de autenticación si solo usa la dirección IP

     De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Si se configura el sitio web en IIS para requerir la autenticación, se producirá un error en esta autenticación. Para corregir este problema, puede especificar el nombre del equipo remoto en lugar de la dirección IP.
     
## <a name="other-causes"></a>Otras causas

Si está usando una versión anterior de Visual Studio:

- Reinicie Visual Studio con privilegios elevados y vuelva a intentarlo.

    Un error en las versiones anteriores (arreglar más adelante) requiere privilegios elevados en algunos escenarios de depuración de ASP.NET.
    
- Si se ejecutan varias instancias de Visual Studio, vuelva a abrir el proyecto en una instancia de Visual Studio e inténtelo de nuevo.

## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
