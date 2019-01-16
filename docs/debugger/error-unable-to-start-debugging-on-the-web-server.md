---
title: 'Error: No se puede iniciar la depuración en el servidor Web | Microsoft Docs'
ms.date: 05/23/2017
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 804249700ff813de5a45e44787af4f39d4a82ad2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856688"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Error: No es posible iniciar la depuración en el servidor web

Al intentar depurar una aplicación de ASP.NET que se ejecutan en un servidor Web, puede aparecer este mensaje de error: `Unable to start debugging on the Web server`.

A menudo, este error se produce porque se ha producido un error o cambio de configuración que requiere una actualización para los grupos de aplicaciones, el restablecimiento de IIS o ambos. Puede restablecer IIS, abra un símbolo del sistema con privilegios elevados y escriba `iisreset`. 

## <a name="specificerrors"></a>¿Qué es el mensaje de error detallado?

El `Unable to start debugging on the Web server` mensaje es genérico. Normalmente, un mensaje más específico se incluye en la cadena de error y que puede ayudar a identificar la causa del problema o busque una corrección más exacta. Estos son algunos de los mensajes de error más comunes que se anexan al mensaje de error principales:

- [IIS no enumera un sitio Web que coincida con el lanzamiento de la dirección url](#IISlist)
- [El servidor web no está configurado correctamente](#web_server_config)
- [No se puede conectar al servidor Web](#unabletoconnect)
- [El servidor web no respondió a tiempo](#webservertimeout)
- [El Monitor de depuración remota de Microsoft Visual Studio (msvsmon.exe) no parece estar ejecutándose en el equipo remoto](#msvsmon)
- [El servidor remoto devolvió un error](#server_error)
- [No se pudo iniciar la depuración de ASP.NET](#aspnet)
- [El depurador no se puede conectar al equipo remoto](#cannot_connect)
- [Busque en la ayuda los errores de configuración comunes. Ejecución de la página Web fuera del depurador puede proporcionar más información.](#see_help)

## <a name="IISlist"></a> IIS no enumera un sitio Web que coincida con el lanzamiento de la dirección url

- Reinicie Visual Studio como administrador y vuelva a intentar la depuración. (Algunos escenarios de depuración de ASP.NET requieren privilegios elevados).

    Puede configurar Visual Studio que se ejecute siempre como administrador haciendo clic con el icono de método abreviado de Visual Studio, elija **Propiedades > Opciones avanzadas**y, a continuación, seleccione la opción siempre se ejecutan como administrador.

## <a name="web_server_config"></a> El servidor web no está configurado correctamente

- Consulte [Error: El servidor web no está configurado correctamente](../debugger/error-the-web-server-is-not-configured-correctly.md)

## <a name="unabletoconnect"></a> No se puede conectar al servidor Web

- ¿Está ejecutando Visual Studio y el servidor Web en el mismo equipo y depuración con **F5** (en lugar de **asociar al proceso**)? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor Web correcto y dirección URL de inicio. (Abra **Propiedades > Web > servidores** o **Propiedades > depurar** según el tipo de proyecto. Para un proyecto de formularios Web Forms, abra **páginas de propiedades > Opciones de Inicio > servidor**.)

- De lo contrario, reinicie el grupo de aplicaciones y, a continuación, restablezca IIS. Para obtener más información, consulte [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> El servidor web no respondió a tiempo

- Restablezca IIS e intente de nuevo la depuración. Varias instancias del depurador pueden asociarse al proceso de IIS; un restablecimiento de terminarlas. Para obtener más información, consulte [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> El Monitor de depuración remota de Microsoft Visual Studio (MSVSMON.EXE) no parece estar ejecutándose en el equipo remoto

- Si está depurando en un equipo remoto, asegúrese de que haya [instaladas y ejecuten el depurador remoto](../debugger/remote-debugging.md). Si el mensaje menciona un firewall, asegúrese de que el [corregir los puertos del firewall](../debugger/remote-debugger-port-assignments.md) están abiertos, especialmente si usa un firewall de terceros.
- Si usa un archivo de HOSTS, asegúrese de que esté configurado correctamente. Por ejemplo, si la depuración con **F5** (en lugar de **asociar al proceso**), debe incluir la misma dirección URL de proyecto como se muestra en las propiedades del proyecto, archivo de HOSTS **Propiedades > Web > servidores**  o **Propiedades > depurar**, según el tipo de proyecto.

## <a name="server_error"></a> El servidor remoto devolvió un error

Compruebe su [archivo de registro IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) para subcódigos de error y obtener información adicional y este IIS 7 [entrada de blog](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Además, estos son algunos de los códigos de error comunes y algunas sugerencias.
- (403) Prohibido. Hay varias causas posibles para este error, así que compruebe el archivo de registro y la configuración de seguridad IIS para el sitio web. Asegúrese de que el archivo web.config del servidor incluye `debug=true` en el elemento de compilación. Asegúrese de que la carpeta de aplicación Web tiene los permisos adecuados y que la configuración del grupo de aplicaciones es correcta (puede haber cambiado una contraseña). Consulte [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck). Si esta configuración es correcta y se depura localmente, compruebe también que se está conectando a la dirección URL y el tipo de servidor correcto (en **Propiedades > Web > servidores** o **Propiedades > depurar**, Dependiendo del tipo de proyecto).
- (503) Servidor no disponible. El grupo de aplicaciones puede haberse detenido debido a un error o cambio de configuración. Reinicie el grupo de aplicaciones.
- (404) No encontrado. Asegúrese de que el grupo de aplicaciones está configurado para la versión correcta de ASP.NET.

## <a name="aspnet"></a> No se pudo iniciar la depuración de ASP.NET

- Reinicie el grupo de aplicaciones y restablezca IIS. Para obtener más información, consulte [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck).
- Si va a realizar las operaciones de reescritura de dirección URL, probar un archivo web.config básica con ninguna dirección URL de reescritura. Consulte la **Nota** sobre la dirección URL, vuelva a escribir el módulo en [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> El depurador no se puede conectar al equipo remoto

Si se depura localmente, este error puede producirse porque Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectar con el servidor Web y la dirección URL correcta. (Abra **Propiedades > Web > servidores** o **Propiedades > depurar** según el tipo de proyecto.)

Además, si usa un archivo de HOSTS, asegúrese de que esté configurado correctamente. Por ejemplo, los HOSTS de archivo debe incluir la misma dirección URL de proyecto como se muestra en las propiedades del proyecto, **Propiedades > Web > servidores** o **Propiedades > depurar**, según el tipo de proyecto.

## <a name="see_help"></a> Busque en la ayuda los errores de configuración comunes. Ejecución de la página Web fuera del depurador puede proporcionar más información.

- ¿Se ejecuta Visual Studio y el servidor Web en el mismo equipo? Abra las propiedades del proyecto y asegúrese de que el proyecto está configurado para conectarse al servidor Web correcto y dirección URL de inicio. (Abra **Propiedades > Web > servidores** o **Propiedades > depurar** según el tipo de proyecto.)

- Si esto no funciona o depura de forma remota, siga los pasos de [Compruebe la configuración de IIS](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Compruebe la configuración de IIS

Después de realizar los pasos detallados aquí para resolver el problema y antes de intentar de nuevo depurar, es posible que también deba restablezca IIS. Para ello, abra un símbolo del sistema con privilegios elevados y escriba `iisreset`. 

* Detener y reiniciar los grupos de aplicaciones de IIS y vuelva a intentar. 

    El grupo de aplicaciones puede haberse detenido como resultado un error. O bien, otro cambio de configuración que ha realizado puede requerir que se detenga y reinicie el grupo de aplicaciones.
    
    > [!NOTE]
    > Si mantiene detener el grupo de aplicaciones, deberá desinstalar el módulo URL Rewrite desde el Panel de Control. Puede volver a instalarlo mediante el instalador de plataforma Web (WebPI). Esto puede ocurrir después de una actualización del sistema significativos.

* Compruebe la configuración del grupo de aplicaciones, corrija si es necesario y, a continuación, vuelva a intentar.

    El grupo de aplicaciones puede configurarse para una versión de ASP.NET que no coincide con el proyecto de Visual Studio. Actualice la versión ASP.NET en el grupo de aplicaciones y reinícielo. Para obtener información detallada, consulte [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Además, si han cambiado las credenciales de contraseña, deberá actualizarlos en el grupo de aplicaciones o sitio Web.  En el grupo de aplicaciones, actualice las credenciales en **configuración avanzada > modelo de proceso > identidad**. Para el sitio Web, actualizar las credenciales en **configuración básica > Conectar como...** . Reinicie el grupo de aplicaciones.
    
* Compruebe que la carpeta de aplicación Web tiene los permisos adecuados.

    Asegúrese de que se asigne a IIS_IUSRS, IUSR, o el usuario específico asociado con el [AppPool](/iis/manage/configuring-security/application-pool-identities) de lectura y ejecución de derechos para la carpeta de aplicación Web. Corrija el problema y reinicie el grupo de aplicaciones.

* Asegúrese de que está instalada la versión correcta de ASP.NET en IIS.

    No coinciden las versiones de ASP.NET en IIS y en el proyecto de Visual Studio pueden causar este problema. Es posible que deba establecer la versión de .NET framework en el archivo web.config. Para instalar ASP.NET en IIS, use el [instalador de plataforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Consulte también [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) o, para ASP.NET Core, [Host en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Resolver errores de autenticación si solo usa la dirección IP

     De manera predeterminada, se asume que las direcciones IP forman parte de Internet y la autenticación NTLM no se realiza a través de Internet. Si se configura el sitio web en IIS para requerir la autenticación, se produce un error en esta autenticación. Para corregir este problema, puede especificar el nombre del equipo remoto en lugar de la dirección IP.
     
## <a name="other-causes"></a>Otras causas

Si la configuración de IIS no está causando el problema, siga estos pasos:

- Reinicie Visual Studio con privilegios de administrador y vuelva a intentarlo.

    Algunos escenarios de depuración de ASP.NET como el uso de Web Deploy requieren privilegios elevados para Visual Studio.
    
- Si se ejecutan varias instancias de Visual Studio, vuelva a abrir el proyecto en una instancia de Visual Studio (con privilegios de administrador) y vuelva a intentarlo.

- Si está utilizando un archivo de HOSTS con direcciones locales, pruebe a usar la dirección de bucle invertido en lugar de la dirección IP del equipo.

    Si no usa las direcciones locales, asegúrese de que el archivo de HOSTS incluye la misma dirección URL de proyecto como se muestra en las propiedades del proyecto, **Propiedades > Web > servidores** o **Propiedades > depurar**, en función de su tipo de proyecto.

## <a name="more-troubleshooting-steps"></a>Más pasos para solucionar problemas

* Abrir la página de localhost en el explorador en el servidor.

     Si IIS no está instalado correctamente, debería obtener errores al escribir `http://localhost` en un explorador.
     
     Para obtener más información sobre la implementación en IIS, consulte [IIS 8.0 utilizando ASP.NET 3.5 y ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) y, para ASP.NET Core, [Host en Windows con IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Crear una aplicación ASP.NET básica en el servidor (o usar un archivo web.config básico).

    Si no se puede obtener la aplicación para que funcione con el depurador, intente crear una aplicación ASP.NET básica localmente en el servidor e intente depurar la aplicación básica. (Es posible que desee usar la plantilla predeterminada ASP.NET MVC.) Si se puede depurar una aplicación básica, que puede ayudarle a identificar cuál es la diferencia entre las dos configuraciones. Busque diferencias en la configuración en el archivo web.config, como las reglas de reescritura de direcciones URL.

## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)