---
title: 'Error: no se puede iniciar la depuración en el servidor Web | Microsoft Docs'
ms.date: 05/23/2018
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 706a20a00792e7c67b39535322fbd2530f2a2ad3
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588992"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: No se puede iniciar la depuración en el servidor Web

Al intentar depurar una aplicación de ASP.NET que se ejecuta en un servidor Web, puede obtener este mensaje de error: `Unable to start debugging on the Web server`.

A menudo, este error se produce porque se ha producido un error o un cambio de configuración que requiere una actualización de los grupos de aplicaciones, un restablecimiento de IIS o ambos. Para restablecer IIS, abra un símbolo del sistema con privilegios elevados y escriba `iisreset`.

## <a name="specificerrors"></a>¿Cuál es el mensaje de error detallado?

El mensaje `Unable to start debugging on the Web server` es genérico. Normalmente, se incluye un mensaje más específico en la cadena de error que puede ayudarle a identificar la causa del problema o a buscar una corrección más exacta. Estos son algunos de los mensajes de error más comunes que se anexan al mensaje de error principal:

- [IIS no muestra un sitio web que coincida con la dirección URL de inicio](#IISlist)
- [El servidor web no está configurado correctamente](#web_server_config)
- [No se puede conectar con el servidor WebServer](#unabletoconnect)
- [El servidor Web no respondió a tiempo](#webservertimeout)
- [El Monitor de depuración remota de Microsoft Visual Studio (msvsmon.exe) no parece estar ejecutándose en el equipo remoto](#msvsmon)
- [El servidor remoto devolvió un error](#server_error)
- [No se pudo iniciar la depuración de ASP.NET](#aspnet)
- [El depurador no se puede conectar al equipo remoto](#cannot_connect)
- [Busque en la ayuda los errores de configuración comunes. Ejecución de la página Web fuera del depurador puede proporcionar más información.](#see_help)

## <a name="IISlist"></a>IIS no muestra un sitio web que coincida con la dirección URL de inicio

- Reinicie Visual Studio como administrador y vuelva a intentar la depuración. (Algunos escenarios de depuración de ASP.NET requieren privilegios elevados).

    Puede configurar Visual Studio para que se ejecute siempre como administrador; para ello, haga clic con el botón derecho en el icono de acceso directo de Visual Studio, elija **propiedades > avanzadas**y, a continuación, elija Ejecutar siempre como administrador.

## <a name="web_server_config"></a> El servidor web no está configurado correctamente

- Vea [el error: el servidor Web no está configurado correctamente](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>No se puede conectar con el servidor WebServer

- ¿Está ejecutando Visual Studio y el servidor Web en el mismo equipo y depurando con **F5** (en lugar de **asociar al proceso**)? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor Web y la dirección URL de inicio correctos. (Abra **propiedades > servidores** o propiedades de > Web **> depurar** según el tipo de proyecto. Para un proyecto de formularios Web Forms, Abra **páginas de propiedades > opciones de inicio > servidor**).

- En caso contrario, reinicie el grupo de aplicaciones y, a continuación, restablezca IIS. Para obtener más información, vea [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>El servidor Web no respondió a tiempo

- Restablezca IIS y vuelva a intentar la depuración. Pueden asociarse varias instancias del depurador al proceso de IIS; un restablecimiento los termina. Para obtener más información, vea [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto

- Si realiza la depuración en un equipo remoto, asegúrese de que ha [instalado y ejecuta el depurador remoto](../debugger/remote-debugging.md). Si el mensaje menciona un firewall, asegúrese de que estén abiertos los [puertos correctos en el Firewall](../debugger/remote-debugger-port-assignments.md) , especialmente si usa un firewall de terceros.
- Si está utilizando un archivo de hosts, asegúrese de que está configurado correctamente. Por ejemplo, si se depura con **F5** (en lugar de **asociar al proceso**), el archivo de hosts debe incluir la misma dirección URL del proyecto que en las propiedades del proyecto, **propiedades > servidores > Web** o **Propiedades > depurar**, dependiendo de el tipo de proyecto.

## <a name="server_error"></a>El servidor remoto devolvió un error

Busque en el [archivo de registro de IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) los códigos de error y la información adicional, así como la entrada de [blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)de IIS 7.

Además, estos son algunos de los códigos de error comunes y algunas sugerencias.
- (403) Prohibido. Hay muchas causas posibles de este error, por lo que debe comprobar el archivo de registro y la configuración de seguridad de IIS para el sitio Web. Asegúrese de que el archivo Web. config del servidor incluye `debug=true` en el elemento de compilación. Asegúrese de que la carpeta de la aplicación web tiene los permisos adecuados y que la configuración del grupo de aplicaciones es correcta (es posible que haya cambiado una contraseña). Consulte [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck). Si esta configuración ya es correcta y está depurando localmente, compruebe también que se está conectando al tipo de servidor y la dirección URL correctos (en **propiedades > servidores de > web** o **Propiedades > depurar**, en función del tipo de proyecto).
- (503) Servidor no disponible. Es posible que el grupo de aplicaciones se haya detenido debido a un error o un cambio de configuración. Reinicie el grupo de aplicaciones.
- (404) No encontrado. Asegúrese de que el grupo de aplicaciones está configurado para la versión correcta de ASP.NET.

## <a name="aspnet"></a>No se pudo iniciar la depuración de ASP.NET

- Reinicie el grupo de aplicaciones y restablezca IIS. Para obtener más información, vea [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck).
- Si va a realizar reescrituras de direcciones URL, pruebe un archivo Web. config básico sin reescritura de direcciones URL. Vea la **Nota** sobre el módulo URL Rewrite en [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a>El depurador no se puede conectar al equipo remoto

Si va a depurar localmente, abra las propiedades del proyecto en Visual Studio y asegúrese de que el proyecto está configurado para conectarse al servidor Web y la dirección URL correctos. (Abra **propiedades > servidores** o propiedades de > Web **> depurar** según el tipo de proyecto).

Este error puede producirse al depurar localmente porque Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del Depurador remoto para depurar aplicaciones de 64 bits. Compruebe el grupo de aplicaciones en IIS para asegurarse de que la **habilitación de las aplicaciones de 32 bits** está establecida en `true`, reinicie IIS e inténtelo de nuevo.

Además, si está usando un archivo de hosts, asegúrese de que está configurado correctamente. Por ejemplo, el archivo de hosts debe incluir la misma dirección URL del proyecto que en las propiedades del proyecto, **propiedades > servidores > web** o **Propiedades > depurar**, dependiendo del tipo de proyecto.

## <a name="see_help"></a> Busque en la ayuda los errores de configuración comunes. La ejecución de la Página Web fuera del depurador puede proporcionar más información.

- ¿Está ejecutando Visual Studio y el servidor Web en el mismo equipo? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor Web y la dirección URL de inicio correctos. (Abra **propiedades > servidores** o propiedades de > Web **> depurar** según el tipo de proyecto).

- Si eso no funciona o está depurando de forma remota, siga los pasos descritos en [comprobar la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="vxtbshttpservererrorsthingstocheck"></a>Comprobar la configuración de IIS

Después de seguir los pasos detallados aquí para resolver el problema y antes de volver a intentar la depuración, es posible que también necesite restablecer IIS. Para ello, abra un símbolo del sistema con privilegios elevados y escriba `iisreset`.

* Detenga y reinicie los grupos de aplicaciones de IIS y vuelva a intentarlo.

    Es posible que el grupo de aplicaciones se haya detenido como resultado de un error. O bien, otro cambio de configuración que haya realizado puede requerir que detenga y reinicie el grupo de aplicaciones.

    > [!NOTE]
    > Si el grupo de aplicaciones se detiene, puede que tenga que desinstalar el módulo URL Rewrite del panel de control. Puede volver a instalarlo mediante el instalador de plataforma web (WebPI). Este problema puede producirse después de una actualización importante del sistema.

* Compruebe la configuración del grupo de aplicaciones, corríjalo si es necesario y vuelva a intentarlo.

    Se puede configurar el grupo de aplicaciones para una versión de ASP.NET que no coincide con el proyecto de Visual Studio. Actualice la versión de ASP.NET en el grupo de aplicaciones y reiníciela. Para obtener información detallada, consulte [IIS 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Además, si las credenciales de contraseña han cambiado, puede que tenga que actualizarlas en el grupo de aplicaciones o el sitio Web.  En el grupo de aplicaciones, actualice las credenciales en **Configuración avanzada > procesar modelo > identidad**. En el sitio web, actualice las credenciales en **configuración básica > conectar como..** .. Reinicie el grupo de aplicaciones.

* Compruebe que la carpeta de la aplicación web tiene los permisos adecuados.

    Asegúrese de proporcionar a IIS_IUSRS, IUSR o el usuario específico asociado al [grupo de aplicaciones](/iis/manage/configuring-security/application-pool-identities) derechos de lectura y ejecución para la carpeta de la aplicación Web. Corrija el problema y reinicie el grupo de aplicaciones.

* Asegúrese de que la versión correcta de ASP.NET está instalada en IIS.

    Las versiones no coincidentes de ASP.NET en IIS y en el proyecto de Visual Studio pueden producir este problema. Es posible que tenga que establecer la versión de .NET Framework en Web. config. Para instalar ASP.NET en IIS, use el [instalador de plataforma web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte también [iis 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.net Core, [hospedar en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Resolver errores de autenticación si solo usa la dirección IP

     De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Si el sitio web está configurado en IIS para requerir autenticación, se produce un error en la autenticación. Para corregir este problema, puede especificar el nombre del equipo remoto en lugar de la dirección IP.

## <a name="other-causes"></a>Otras causas

Si la configuración de IIS no está causando el problema, siga estos pasos:

- Reinicie Visual Studio con privilegios de administrador y vuelva a intentarlo.

    Algunos escenarios de depuración de ASP.NET, como el uso de Web Deploy requieren privilegios elevados para Visual Studio.

- Si se están ejecutando varias instancias de Visual Studio, vuelva a abrir el proyecto en una instancia de Visual Studio (con privilegios de administrador) e inténtelo de nuevo.

- Si usa un archivo de hosts con direcciones locales, pruebe a usar la dirección de bucle invertido en lugar de la dirección IP de la máquina.

    Si no usa direcciones locales, asegúrese de que el archivo de hosts incluye la misma dirección URL del proyecto que en las propiedades del proyecto, **propiedades > servidores > web** o **Propiedades > depurar**, dependiendo del tipo de proyecto.

## <a name="more-troubleshooting-steps"></a>Más pasos para solucionar problemas

* Abra la página localhost en el explorador del servidor.

     Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.

     Para obtener más información sobre la implementación en IIS, vea [iis 8,0 con ASP.NET 3,5 y ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) y, para ASP.net Core, [hospedar en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Cree una aplicación ASP.NET básica en el servidor (o use un archivo Web. config básico).

    Si no puede hacer que la aplicación funcione con el depurador, intente crear una aplicación ASP.NET básica localmente en el servidor e intente depurar la aplicación básica. (Puede que desee usar la plantilla predeterminada de ASP.NET MVC). Si puede depurar una aplicación básica, esto puede ayudarle a identificar las diferencias entre las dos configuraciones. Busque diferencias en la configuración del archivo Web. config, como las reglas de reescritura de direcciones URL.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)