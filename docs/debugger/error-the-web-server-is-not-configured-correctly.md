---
title: 'Error: El servidor web no está correctamente | Documentos de Microsoft'
ms.custom: ''
ms.date: 09/20/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9ff79148af491ee27aeae20b66b4d7b742bef6b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente

Después de realizar los pasos que se detallan a continuación para solucionar el problema y antes de intentar de nuevo depurar, también tendrá que restablecer IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset`.

Siga estos pasos para resolver este problema:

1. Si la aplicación web que se hospedan en el servidor está configurada como una versión de lanzamiento, volver a publicar como una compilación de depuración y compruebe que el archivo web.config contiene `debug=true` en el elemento de compilación. Restablecer IIS y vuelva a intentarlo.

    Por ejemplo, si utiliza un perfil de publicación para una versión de lanzamiento, cambiar a la depuración y volver a publicar. En caso contrario, se establecerá el atributo de depuración en `false` al publicar.

2. (IIS) Compruebe que la ruta de acceso física es correcta. En IIS, encontrar esta opción en **configuración básica > ruta de acceso física** (o **configuración avanzada** en versiones anteriores de IIS).

    La ruta de acceso física puede ser incorrecta si se copió en un equipo diferente, se cambió de nombre manualmente o se mueve la aplicación web. Restablecer IIS y vuelva a intentarlo.

3. Si está depurando localmente en Visual Studio, compruebe que esté seleccionado el servidor correcto en las propiedades. (Abra **Propiedades > Web > servidores** o **Propiedades > depurar** según el tipo de proyecto. Para un proyecto de formularios Web Forms, abra **páginas de propiedades > Opciones de Inicio > servidor**).

    Si está usando un servidor externo (personalizado) como IIS, la dirección URL debe ser correcta. En caso contrario, seleccione IIS Express y vuelva a intentarlo.

4. (IIS) Asegúrese de que la versión correcta de ASP.NET está instalada en el servidor.

    Versiones de ASP.NET en IIS y en el proyecto de Visual Studio pueden causar este problema. Debe establecer la versión de framework en el archivo web.config. Para instalar ASP.NET en IIS, use la [instalador de plataforma Web (WPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte también [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.NET Core, [Host en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
4. Si el `maxConnection` límite en IIS es demasiado bajo y hay demasiadas conexiones, puede que necesite [aumentar el límite de conexión](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).
  
## <a name="see-also"></a>Vea también  
 [Depuración ASP.NET remota en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)   
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)