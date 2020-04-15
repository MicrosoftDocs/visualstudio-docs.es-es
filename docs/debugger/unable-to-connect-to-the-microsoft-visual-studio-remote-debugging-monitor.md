---
title: No se puede conectar con el Monitor de depuración remota de Microsoft Visual Studio . Microsoft Docs
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d509292bc3c7a909289abf0c73babccfead31532
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385394"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>No se puede conectar al Monitor de depuración remota de Microsoft Visual Studio
Este mensaje puede producirse porque el monitor de depuración remota no está configurado correctamente en el equipo remoto o porque el equipo remoto es inaccesible debido a problemas de red o a la presencia de un firewall.

> [!IMPORTANT]
> Si cree que ha recibido este mensaje debido a un error de producto, informe de [este problema](../ide/how-to-report-a-problem-with-visual-studio.md) a Visual Studio. Si necesita más ayuda, vea [Talk to Us](../ide/feedback-options.md) para obtener información sobre las distintas formas de ponerse en contacto con Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>¿Cuál es el mensaje de error detallado?

El `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` mensaje es genérico. Normalmente, se incluye un mensaje más específico en la cadena de error y que puede ayudarle a identificar la causa del problema o buscar una solución más exacta. Aquí están algunos de los mensajes de error más comunes que se anexan al mensaje de error principal:

- [El depurador no se puede conectar al equipo remoto. El depurador no pudo resolver el nombre de equipo especificado](#cannot_connect)
- [La solicitud de conexión fue rechazada por el depurador remoto](#rejected)
- [Acceso no válido a la ubicación de la memoria](#invalid_access)
- [No hay ningún servidor con el nombre especificado que se ejecute en el equipo remoto](#no_server)
- [El nombre solicitado era válido, pero no se encontraron datos del tipo solicitado](#valid_name)
- [El depurador remoto de Visual Studio en el equipo de destino no puede conectarse de nuevo a este equipo](#cant_connect_back)
- [Acceso denegado](#access_denied)
- [Se ha producido un error específico del paquete de seguridad](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>El depurador no se puede conectar al equipo remoto. El depurador no pudo resolver el nombre de equipo especificado

Siga estos pasos:

1. Asegúrese de escribir un nombre de equipo y un número de puerto válidos en el cuadro de diálogo **Asociar al proceso** o en las propiedades del proyecto (Para establecer propiedades, consulte estos [pasos](#server_incorrect)). El nombre del equipo debe tener el siguiente formato:

    `computername:port`

    > [!NOTE]
    > El número de puerto debe coincidir con el [número de puerto del depurador remoto,](../debugger/remote-debugger-port-assignments.md)que debe estar *ejecutándose* en el equipo de destino.

2. Si el nombre del equipo no funciona, pruebe la dirección IP y el número de puerto en su lugar.

3. Asegúrese de que la versión del depurador remoto que se ejecuta en el equipo de destino coincide con la versión de Visual Studio. Para obtener la versión correcta del depurador remoto, vea [Depuración remota](../debugger/remote-debugging.md).

    > [!TIP]
    > Si se está adjuntando al proceso y se conecta correctamente pero no ve el proceso que desea, active la **casilla Mostrar procesos de todos los usuarios**. Esto mostrará los procesos si está conectado con una cuenta de usuario diferente.

4. Si estos pasos no resuelven este error, consulte [La máquina remota no es accesible.](#dns)

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>La solicitud de conexión fue rechazada por el depurador remoto

En el cuadro de diálogo **Asociar al proceso** o en las propiedades del proyecto, asegúrese de que el nombre del equipo remoto y el número de puerto coincidan con el nombre y el número de puerto que se muestran en la ventana del depurador remoto. Si es incorrecto, solucione e inténtelo de nuevo.

Si estos valores son correctos y el mensaje menciona el modo de autenticación de **Windows,** compruebe que el depurador remoto está en el modo de autenticación correcto **(Herramientas > Opciones**).

## <a name="the-connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>La conexión con el punto de conexión remoto se ha terminado

Si está depurando una aplicación de Azure App Service, intente usar el comando [Adjuntar depurador](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) desde Cloud Explorer o el Explorador de servidores en lugar de Adjuntar **al proceso**.

Si está utilizando **Adjuntar al proceso** para depurar:

1. En el cuadro de diálogo **Asociar al proceso** o en las propiedades del proyecto, asegúrese de que el nombre del equipo remoto y el número de puerto coincidan con el nombre y el número de puerto que se muestran en la ventana del depurador remoto. Si es incorrecto, solucione e inténtelo de nuevo.

2. Compruebe el registro de la aplicación en el servidor (Visor de eventos en Windows) para obtener información más detallada que ayude a resolver el problema.

3. De lo contrario, intente reiniciar Visual Studio con privilegios de administrador y, a continuación, vuelva a intentarlo.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Acceso no válido a la ubicación de la memoria

Error interno. Reinicie Visual Studio e inténtelo de nuevo.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>No hay ningún servidor con el nombre especificado que se ejecute en el equipo remoto

Visual Studio no pudo conectarse al depurador remoto. Este mensaje puede ocurrir por varias razones:

- Es posible que el depurador remoto se ejecute con una cuenta de usuario diferente. Vea [estos pasos](#user_accounts)

- El puerto está bloqueado en el firewall. Asegúrese de que el firewall [no está bloqueando su solicitud,](#firewall)especialmente si está utilizando un firewall de terceros.

- La versión del depurador remoto no coincide con Visual Studio. Para obtener la versión correcta del depurador remoto, vea [Depuración remota](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>El nombre solicitado era válido, pero no se encontraron datos del tipo solicitado

El equipo remoto existe, pero Visual Studio no pudo conectarse al depurador remoto. Este mensaje puede ocurrir por varias razones:

- Un problema de DNS impide la conexión. Consulte [estos pasos](#dns).

- Es posible que el depurador remoto se ejecute con una cuenta de usuario diferente. Siga [estos pasos](#user_accounts).

- El puerto está bloqueado en el firewall. Asegúrese de que el firewall [no está bloqueando su solicitud,](#firewall)especialmente si está utilizando un firewall de terceros.

- La versión del depurador remoto no coincide con Visual Studio. Para obtener la versión correcta del depurador remoto, vea [Depuración remota](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>El depurador remoto de Visual Studio en el equipo de destino no puede conectarse de nuevo a este equipo

Es posible que el depurador remoto se ejecute con una cuenta de usuario diferente. En el depurador remoto, abra **Herramientas > Permisos** para agregar el usuario a los permisos del depurador remoto. Para obtener más información, consulte El depurador remoto se ejecuta con una cuenta de [usuario diferente.](#user_accounts)

Si el mensaje de error también menciona un firewall, el firewall del equipo local puede impedir la comunicación desde el equipo remoto a Visual Studio. Consulte [estos pasos](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a>Acceso denegado

Es posible que vea este error si intenta depurar en un equipo remoto de 64 bits desde un equipo de 32 bits (no compatible).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Se ha producido un error específico del paquete de seguridad

Esto puede ser un problema heredado específico de Windows XP y Windows 7. Consulte esta [información](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causas y recomendaciones

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a> Falta de accesibilidad al equipo remoto

Si no puede conectarse con el nombre del equipo remoto, intente usar la dirección IP en su lugar. Puede utilizar `ipconfig` en una línea de comandos en el equipo remoto para obtener la dirección IPv4. Si está utilizando un archivo HOSTS, compruebe que está configurado correctamente.

Si se produce un error, compruebe que el equipo remoto es accesible en la red[(haga ping en](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) el equipo remoto). No se admite la depuración remota a través de Internet, excepto en algunos escenarios de Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>El nombre del servidor es incorrecto o el software de terceros está interfiriendo con el depurador remoto

En Visual Studio, examine las propiedades del proyecto y asegúrese de que el nombre del servidor es correcto. Consulte los temas de [C- y Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) y [C++.](../debugger/remote-debugging-cpp.md#remote_cplusplus) Para ASP.NET, abra **Propiedades / Web / Servidores** o Propiedades / **Depurar** dependiendo del tipo de proyecto.

> [!NOTE]
> Si va a adjuntar al proceso, no se utiliza la configuración remota de las propiedades del proyecto.

Si el nombre del servidor es correcto, es posible que el software antivirus o un firewall de terceros estén bloqueando el depurador remoto. Al depurar localmente, esto puede suceder porque Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del depurador remoto para depurar aplicaciones de 64 bits. Los procesos de 32 bits y 64 bits se comunican mediante la red local dentro del equipo local. Nada de tráfico de red sale del equipo, pero es posible que el software de seguridad de terceros bloquee la comunicación.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>El depurador remoto se ejecuta con una cuenta de usuario diferente

El depurador remoto, de forma predeterminada, solo aceptará conexiones del usuario que inició el depurador remoto y los miembros del grupo Administradores. Los usuarios adicionales deben tener permisos explícitamente concedidos.

Puede resolver este problema de una de las siguientes formas:

- Agregue el usuario de Visual Studio a los permisos del depurador remoto (en la ventana del depurador remoto, elija **Herramientas > Permisos**).

- En el equipo remoto, reinicie el depurador remoto con la misma cuenta de usuario y contraseña que usa en el equipo de Visual Studio.

    > [!NOTE]
    > Si está ejecutando el depurador remoto en un servidor remoto, haga clic con el botón secundario en la aplicación Depurador remoto y elija **Ejecutar como administrador** (o puede ejecutar el depurador remoto como servicio). Si no lo está ejecutando en un servidor remoto, simplemente inícielo normalmente.

- Puede iniciar el depurador remoto desde la línea de comandos con el parámetro **/allow \<username>**: `msvsmon /allow <username@computer>`.

- Como alternativa, puede permitir que cualquier usuario realice la depuración remota. En la ventana del depurador remoto, vaya al cuadro de diálogo **Herramientas > Opciones**. Al seleccionar   **Sin autenticación**, podrá activar **Permitir que cualquier usuario depure**. Sin embargo, debe probar esta opción solo si las otras opciones fallan o si está en una red privada.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>El firewall del equipo remoto no permite conexiones entrantes al depurador remoto
 El firewall del equipo de Visual Studio y el firewall del equipo remoto deben configurarse para permitir la comunicación entre Visual Studio y el depurador remoto. Para obtener información sobre los puertos que usa el depurador remoto, vea [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Para obtener información sobre de cómo configurar el firewall de Windows, vea [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versión del depurador remoto no coincide con la versión de Visual Studio
 La versión de Visual Studio que se ejecuta localmente debe coincidir con la versión del monitor de depuración remota que se ejecuta en el equipo remoto. Para solucionar este problema, descargue e instale la versión correspondiente del monitor de depuración remota. Para obtener la versión correcta del depurador remoto, vea [Depuración remota](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Los equipos locales y remotos tienen distintos modos de autenticación
 Los equipos locales y remotos deben usar el mismo modo de autenticación. Para solucionar este problema, asegúrese de que ambos equipos usan el mismo modo de autenticación. Puede cambiar el modo de autenticación. En la ventana del depurador remoto, vaya al cuadro de diálogo **Opciones de >** herramientas.

 Para más información sobre la autenticación, vea [Información general de la autenticación de Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>El software antivirus está bloqueando las conexiones
 Software antivirus de Windows permite las conexiones del depurador remoto, pero algunos programas antivirus de terceros pueden bloquearlas. Consulte la documentación de su software antivirus para averiguar cómo permitir estas conexiones.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La directiva de seguridad de red está bloqueando la comunicación entre el equipo remoto y Visual Studio
 Revise la seguridad de la red para asegurarse de que no está bloqueando la comunicación. Para obtener más información acerca de la directiva de seguridad de red de Windows, consulte Configuración de [directiva](/windows/device-security/security-policy-settings/security-policy-settings)de seguridad .

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La red está demasiado ocupada para admitir la depuración remota
 Puede que necesite realizar la depuración remota en otro momento o volver a programar un trabajo de la red correspondiente a otra hora distinta.

## <a name="more-help"></a>Más ayuda
 Para obtener más ayuda del depurador remoto, abra la página Ayuda del depurador remoto **(Ayuda > Uso** en el depurador remoto).

## <a name="see-also"></a>Consulte también
- [Depuración remota](../debugger/remote-debugging.md)
