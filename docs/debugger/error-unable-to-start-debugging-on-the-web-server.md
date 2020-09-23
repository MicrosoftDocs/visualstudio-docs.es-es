---
title: No es posible iniciar la depuración en el servidor web | Microsoft Docs
ms.date: 05/23/2018
ms.topic: error-reference
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
ms.openlocfilehash: 5a0aa657abefa0638e62039cae8b6d15a33fdf51
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851429"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: No es posible iniciar la depuración en el servidor web

Al intentar depurar una aplicación ASP.NET que se ejecuta en un servidor web, es posible que reciba este mensaje de error: `Unable to start debugging on the Web server`.

A menudo, aparece porque se ha producido un error o un cambio de configuración que requiere una actualización de los grupos de aplicaciones, un restablecimiento de IIS o ambos. Para restablecer IIS, abra un símbolo del sistema con privilegios elevados y escriba `iisreset`.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>¿Cuál es el mensaje de error detallado?

El mensaje `Unable to start debugging on the Web server` es genérico. Normalmente, se incluye un mensaje más específico en la cadena de error que puede ayudarle a identificar la causa del problema o a buscar una corrección más exacta. Estos son algunos de los mensajes de error más comunes que se anexan al mensaje de error principal:

- [IIS no muestra un sitio web que coincida con la dirección URL de inicio](#IISlist)
- [El servidor web no está configurado correctamente](#web_server_config)
- [No se puede conectar al servidor web](#unabletoconnect)
- [El servidor web no ha respondido a tiempo](#webservertimeout)
- [El Monitor de depuración remota de Microsoft Visual Studio (msvsmon.exe) no parece estar ejecutándose en el equipo remoto](#msvsmon)
- [Error en el servidor remoto](#server_error)
- [No se pudo iniciar la depuración de ASP.NET](#aspnet)
- [El depurador no se puede conectar al equipo remoto](#cannot_connect)
- [Busque en la ayuda los errores de configuración comunes. Al ejecutar la página web fuera del depurador, se puede obtener más información.](#see_help)
- [Operación no admitida. Error desconocido: *número_de_error*](#operation_not_supported)

## <a name="iis-does-not-list-a-website-that-matches-the-launch-url"></a><a name="IISlist"></a> IIS no muestra un sitio web que coincida con la dirección URL de inicio

- Reinicie Visual Studio como administrador y vuelva a intentar la depuración. (Algunos escenarios de depuración de ASP.NET requieren privilegios elevados).

    Puede configurar Visual Studio para que se ejecute siempre como administrador; para ello, haga clic con el botón derecho en el icono de acceso directo de Visual Studio, elija **Propiedades > Avanzadas** y después Ejecutar siempre como administrador.

## <a name="the-web-server-is-not-configured-correctly"></a><a name="web_server_config"></a> El servidor web no está configurado correctamente

- Consulte [Error: El servidor web no está configurado correctamente](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unable-to-connect-to-the-webserver"></a><a name="unabletoconnect"></a> No se puede conectar al servidor web

- ¿Ejecuta Visual Studio y el servidor web en el mismo equipo, y depura con **F5** (en lugar de **Asociar al proceso**)? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor web y la dirección URL de inicio correctos. (Abra **Propiedades > Web > Servidores** o **Propiedades > Depurar** en función del tipo de proyecto. Para un proyecto de Web Forms, abra **Páginas de propiedades > Opciones de inicio > Servidor**).

- De lo contrario, reinicie el grupo de aplicaciones y, después, restablezca IIS. Para obtener más información, vea [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-web-server-did-not-respond-in-a-timely-manner"></a><a name="webservertimeout"></a> El servidor web no ha respondido a tiempo

- Restablezca IIS e intente la depuración. Se pueden asociar varias instancias del depurador al proceso de IIS, que se determinan mediante un restablecimiento. Para obtener más información, vea [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-microsoft-visual-studio-remote-debugging-monitormsvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a><a name="msvsmon"></a> El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto

- Si va a realizar la depuración en un equipo remoto, asegúrese de que ha instalado [ y de que ejecuta el depurador remoto](../debugger/remote-debugging.md). Si el mensaje menciona un firewall, asegúrese de que estén abiertos los [puertos correctos en el firewall](../debugger/remote-debugger-port-assignments.md), especialmente si usa uno de terceros.
- Si usa un archivo HOSTS, asegúrese de que está configurado correctamente. Por ejemplo, si realiza la depuración mediante **F5** (en lugar de **Asociar al proceso**), el archivo HOSTS debe incluir la misma dirección URL del proyecto que en las propiedades del proyecto (**Propiedades > Web > Servidores** o **Propiedades > Depurar**) en función del tipo de proyecto.

## <a name="the-remote-server-returned-an-error"></a><a name="server_error"></a> Error en el servidor remoto

Compruebe el [archivo de registro de IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) para obtener los subcódigos de error e información adicional, y esta [entrada de blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403) de IIS 7.

Además, estos son algunos de los códigos de error comunes y algunas sugerencias.
- (403) Prohibido. Hay muchas causas posibles de este error, por lo que debe comprobar el archivo de registro y la configuración de seguridad de IIS del sitio web. Asegúrese de que el archivo web.config del servidor incluye `debug=true` en el elemento de compilación. Asegúrese de que la carpeta de la aplicación web tiene los permisos adecuados y que la configuración del grupo de aplicaciones es correcta (es posible que haya cambiado una contraseña). Vea [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck). Si estos valores son correctos y realiza la depuración localmente, compruebe también que se conecta al tipo de servidor y la dirección URL correctos (en **Propiedades > Web > Servidores** o **Propiedades > Depurar**) en función del tipo de proyecto.
- (503) Servidor no disponible. Es posible que el grupo de aplicaciones se haya detenido debido a un error o un cambio de configuración. Reinicie el grupo de aplicaciones.
- (404) No encontrado. Asegúrese de que el grupo de aplicaciones está configurado para la versión correcta de ASP.NET.

## <a name="could-not-start-aspnet-debugging"></a><a name="aspnet"></a> No se pudo iniciar la depuración de ASP.NET

- Reinicie el grupo de aplicaciones y restablezca IIS. Para obtener más información, vea [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).
- Si va a realizar reescrituras de direcciones URL, pruebe un archivo web.config básico sin reescritura de direcciones URL. Vea la **Nota** sobre el módulo URL Rewrite en [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="the-debugger-cannot-connect-to-the-remote-computer"></a><a name="cannot_connect"></a> El depurador no se puede conectar al equipo remoto

Si va a realizar la depuración de forma local, abra las propiedades del proyecto en Visual Studio y asegúrese de que el proyecto está configurado para conectarse al servidor web y la dirección URL correctos. (Abra **Propiedades > Web > Servidores** o **Propiedades > Depurar** en función del tipo de proyecto).

Este error se puede producir al realizar la depuración de forma local porque Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Compruebe el grupo de aplicaciones en IIS para asegurarse de que **Habilitar aplicaciones de 32 bits** esté establecida en `true`, reinicie IIS e inténtelo de nuevo.

Además, si usa un archivo HOSTS, asegúrese de que está configurado correctamente. Por ejemplo, el archivo HOSTS debe incluir la misma dirección URL del proyecto que en las propiedades del proyecto, **Propiedades > Web > Servidores** o **Propiedades > Depurar**, en función del tipo de proyecto.

## <a name="see-help-for-common-configuration-errors-running-the-webpage-outside-of-the-debugger-may-provide-further-information"></a><a name="see_help"></a> Busque en la ayuda los errores de configuración comunes. Al ejecutar la página web fuera del depurador, se puede obtener más información.

- ¿Ejecuta Visual Studio y el servidor web en el mismo equipo? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor web y la dirección URL de inicio correctos. (Abra **Propiedades > Web > Servidores** o **Propiedades > Depurar** en función del tipo de proyecto).

- Si eso no funciona o realiza la depuración de forma remota, siga los pasos descritos en [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="operation-not-supported-unknown-error-errornumber"></a><a name="operation_not_supported"></a> Operación no admitida. Error desconocido: *número_de_error*

Si va a realizar reescrituras de direcciones URL, pruebe un archivo web.config básico sin reescritura de direcciones URL. Vea la **Nota** sobre el módulo URL Rewrite en [Comprobación de la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Comprobación de la configuración de IIS

Después de seguir los pasos detallados aquí para resolver la incidencia y, antes de volver a intentar la depuración, es posible que también necesite restablecer IIS. Puede hacerlo si abre un símbolo del sistema con privilegios elevados y escribe `iisreset`.

* Detenga y reinicie los grupos de aplicaciones de IIS y vuelva a intentarlo.

    Es posible que el grupo de aplicaciones se haya detenido como resultado de un error. O bien, otro cambio de configuración que haya realizado puede requerir que detenga y reinicie el grupo de aplicaciones.

    > [!NOTE]
    > Si el grupo de aplicaciones se detiene, es posible que tenga que desinstalar el módulo URL Rewrite desde el panel de control. Puede volver a instalarlo mediante el Instalador de plataforma web (WebPI). Esta incidencia se puede producir después de una actualización importante del sistema.

* Compruebe la configuración del grupo de aplicaciones, corríjala si es necesario y vuelva a intentarlo.

    Se puede configurar el grupo de aplicaciones para una versión de ASP.NET que no coincida con el proyecto de Visual Studio. Actualice la versión de ASP.NET en el grupo de aplicaciones y reinícielo. Para obtener información detallada, vea [IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Además, si las credenciales de contraseña han cambiado, es posible que tenga que actualizarlas en el grupo de aplicaciones o el sitio web.  En el grupo de aplicaciones, actualice las credenciales en **Configuración avanzada > Modelo de proceso > Identidad**. Para el sitio web, actualice las credenciales en **Configuración básica > Conectar como...** . Reinicie el grupo de aplicaciones.

* Compruebe que la carpeta de la aplicación web tiene los permisos adecuados.

    Asegúrese de proporcionar derechos de lectura y ejecución para la carpeta de la aplicación web a IIS_IUSRS, IUSR o al usuario específico asociado al [grupo de aplicaciones](/iis/manage/configuring-security/application-pool-identities). Corrija la incidencia y reinicie el grupo de aplicaciones.

* Asegúrese de que en IIS está instalada la versión correcta de ASP.NET.

    Las versiones no coincidentes de ASP.NET en IIS y en el proyecto de Visual Studio pueden producir esta incidencia. Es posible que tenga que establecer la versión del marco en web.config. Para instalar ASP.NET en IIS, use el [Instalador de plataforma web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Vea también [IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.NET Core, [Hospedaje en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Resolver errores de autenticación si solo usa la dirección IP

     De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Si el sitio web está configurado en IIS para requerir autenticación, se produce un error en la autenticación. Para corregir este problema, puede especificar el nombre del equipo remoto, en lugar de la dirección IP.

## <a name="other-causes"></a>Otras causas

Si la configuración de IIS no es el origen de la incidencia, siga estos pasos:

- Reinicie Visual Studio con privilegios de administrador y vuelva a intentarlo.

    Algunos escenarios de depuración de ASP.NET, como el uso de Web Deploy requieren privilegios elevados para Visual Studio.

- Si se ejecuta varias instancias de Visual Studio, vuelva a abrir el proyecto en una (con privilegios de administrador) e inténtelo de nuevo.

- Si usa un archivo HOSTS con direcciones locales, pruebe a usar la dirección de bucle invertido en lugar de la dirección IP del equipo.

    Si no usa direcciones locales, asegúrese de que el archivo HOSTS incluya la misma dirección URL del proyecto que en las propiedades del proyecto, **Propiedades > Web > Servidores** o **Propiedades > Depurar**, en función del tipo de proyecto.

## <a name="more-troubleshooting-steps"></a>Más pasos para solucionar problemas

* Abrir la página de localhost en el explorador en el servidor.

     Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.

     Para obtener más información sobre la implementación en IIS, vea [IIS 8.0 con ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) y, para ASP.NET Core, [Hospedaje en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Cree una aplicación ASP.NET básica en el servidor (o use un archivo web.config básico).

    Si no consigue que la aplicación funcione con el depurador, intente crear una aplicación ASP.NET básica localmente en el servidor y depurarla. (Es posible que le interese usar la plantilla ASP.NET MVC predeterminada). Si puede depurar una aplicación básica, esto puede ayudarle a identificar las diferencias entre las dos configuraciones. Busque diferencias en la configuración del archivo web.config, como las reglas de reescritura de direcciones URL.

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)