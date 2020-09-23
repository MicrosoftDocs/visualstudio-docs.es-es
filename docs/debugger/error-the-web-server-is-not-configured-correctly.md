---
title: El servidor web no está configurado correctamente | Microsoft Docs
ms.date: 09/20/2017
ms.topic: error-reference
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
ms.openlocfilehash: 9dc8253896bfdcf818e0848482a6c637350f590f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851546"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente

Después de seguir los pasos detallados aquí para resolver la incidencia y, antes de volver a intentar la depuración, es posible que también necesite restablecer IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset`.

Para resolver la incidencia, siga estos pasos:

1. Si la aplicación web hospedada en el servidor está configurada como una compilación de versión, vuelva a publicarla como una compilación de depuración y compruebe que el archivo web.config contiene `debug=true` en el elemento de compilación. Restablezca IIS e inténtelo de nuevo.

    Por ejemplo, si usa un perfil de publicación para una compilación de versión, cámbielo a depuración y vuelva a publicar. De lo contrario, el atributo debug se establecerá en `false` al publicar.

2. (IIS) Compruebe que la ruta de acceso física es correcta. En IIS, este valor se encuentra en **Configuración básica > Ruta de acceso física** (o **Configuración avanzada** en versiones anteriores de IIS).

    Es posible que la ruta de acceso física sea incorrecta si la aplicación web se ha copiado a otro equipo, se ha cambiado de nombre manualmente o se ha movido. Restablezca IIS e inténtelo de nuevo.

3. Si va a depurar localmente en Visual Studio, compruebe que el servidor correcto está seleccionado en las propiedades. (Abra **Propiedades > Web > Servidores** o **Propiedades > Depurar** en función del tipo de proyecto. Para un proyecto de formularios Web Forms, abra **Páginas de propiedades > Opciones de inicio > Servidor**).

    Si va a usar un servidor externo (personalizado) como IIS, la dirección URL debe ser correcta. En caso contrario, seleccione IIS Express e inténtelo de nuevo.

4. (IIS) Asegúrese de que en el servidor está instalada la versión correcta de ASP.NET.

    Las versiones no coincidentes de ASP.NET en IIS y en el proyecto de Visual Studio pueden producir esta incidencia. Es posible que tenga que establecer la versión del marco en web.config. Para instalar ASP.NET en IIS, use el [Instalador de plataforma web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vea también [IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.NET Core, [Hospedaje en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Si el límite `maxConnection` en IIS es demasiado bajo y tiene demasiadas conexiones, puede que tenga que [aumentar el límite de conexiones](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vea también
- [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)