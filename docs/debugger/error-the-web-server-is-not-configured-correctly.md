---
title: 'Error: El servidor web no está configurado correctamente | Documentos de Microsoft'
ms.date: 09/20/2017
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc0c61b766b6f93fd1321b15861000d7c628f124
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850402"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente

Después de realizar los pasos detallados aquí para resolver el problema y antes de intentar de nuevo depurar, es posible que también deba restablezca IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset`.

Siga estos pasos para resolver este problema:

1. Si la aplicación web hospedada en el servidor está configurada como una versión de lanzamiento, volver a publicar como una compilación de depuración y compruebe que el archivo web.config contiene `debug=true` en el elemento de compilación. Restablecer IIS y vuelva a intentarlo.

    Por ejemplo, si usa un perfil de publicación para una versión de lanzamiento, cámbielo a depuración y volver a publicar. En caso contrario, se establecerá el atributo de depuración en `false` al publicar.

2. (IIS) Compruebe que la ruta de acceso física es correcta. En IIS, encontrar esta opción en **configuración básica > ruta de acceso física** (o **configuración avanzada** en versiones anteriores de IIS).

    La ruta de acceso física puede ser incorrecto si se copian en un equipo diferente, cambiar manualmente el nombre o mover la aplicación web. Restablecer IIS y vuelva a intentarlo.

3. Si está depurando localmente en Visual Studio, compruebe que el servidor correcto está seleccionado en las propiedades. (Abra **Propiedades > Web > servidores** o **Propiedades > depurar** según el tipo de proyecto. Para un proyecto de formularios Web Forms, abra **páginas de propiedades > Opciones de Inicio > servidor**).

    Si usa un servidor externo (personalizado) como IIS, la dirección URL debe ser correcta. En caso contrario, seleccione IIS Express y vuelva a intentarlo.

4. (IIS) Asegúrese de que la versión correcta de ASP.NET está instalada en el servidor.

    No coinciden las versiones de ASP.NET en IIS y en el proyecto de Visual Studio pueden causar este problema. Es posible que deba establecer la versión de .NET framework en el archivo web.config. Para instalar ASP.NET en IIS, use el [instalador de plataforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte también [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.NET Core, [Host en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Si el `maxConnection` límite en IIS es demasiado bajo y tiene demasiadas conexiones, es posible que deba [aumentar el límite de conexiones](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vea también
- [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)