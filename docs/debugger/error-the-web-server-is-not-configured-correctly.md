---
title: 'Error: el servidor Web no está configurado correctamente | Microsoft Docs'
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
ms.openlocfilehash: be5db0a08a287e2611c29396e96e72719b5106a7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736925"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Error: El servidor Web no está configurado correctamente

Después de seguir los pasos detallados aquí para resolver el problema y antes de volver a intentar la depuración, es posible que también necesite restablecer IIS. Para ello, abra un símbolo del sistema de administrador y escriba `iisreset`.

Siga estos pasos para resolver este problema:

1. Si la aplicación web hospedada en el servidor está configurada como una compilación de versión, vuelva a publicarla como una compilación de depuración y compruebe que el archivo Web. config contiene `debug=true` en el elemento de compilación. Restablezca IIS e inténtelo de nuevo.

    Por ejemplo, si usa un perfil de publicación para una compilación de versión, cámbielo para depurar y volver a publicar. De lo contrario, el atributo Debug se establecerá en `false` al publicar.

2. IIS Compruebe que la ruta de acceso física es correcta. En IIS, este valor se encuentra en **configuración básica > ruta de acceso física** (o **Configuración avanzada** en versiones anteriores de IIS).

    La ruta de acceso física puede ser incorrecta si la aplicación web se copió en un equipo diferente, se cambió de nombre manualmente o se trasladó. Restablezca IIS e inténtelo de nuevo.

3. Si está depurando localmente en Visual Studio, compruebe que el servidor correcto está seleccionado en las propiedades. (Abra **propiedades > servidores** o propiedades de > Web **> depurar** según el tipo de proyecto. Para un proyecto de formularios Web Forms, Abra **páginas de propiedades > opciones de inicio > servidor**).

    Si usa un servidor externo (personalizado) como IIS, la dirección URL debe ser correcta. En caso contrario, seleccione IIS Express e inténtelo de nuevo.

4. IIS Asegúrese de que la versión correcta de ASP.NET está instalada en el servidor.

    Las versiones no coincidentes de ASP.NET en IIS y en el proyecto de Visual Studio pueden producir este problema. Es posible que tenga que establecer la versión de .NET Framework en Web. config. Para instalar ASP.NET en IIS, use el [instalador de plataforma web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte también [iis 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.net Core, [hospedar en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

4. Si el límite de `maxConnection` en IIS es demasiado bajo y tiene demasiadas conexiones, puede que tenga que [aumentar el límite de conexiones](/iis/configuration/system.applicationhost/sites/sitedefaults/limits).

## <a name="see-also"></a>Vea también
- [Depuración remota de ASP.NET en un equipo remoto de IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)