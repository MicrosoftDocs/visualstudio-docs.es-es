---
title: No se puede conectar con el Monitor de depuración remota de Microsoft Visual Studio | Microsoft Docs
ms.date: 08/24/2017
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
ms.openlocfilehash: 872f7c594344af2c59ebe7f8d1fbd1a640dd2190
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728825"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>No se puede conectar al Monitor de depuración remota de Microsoft Visual Studio
Este mensaje puede deberse a que el monitor de depuración remota no está correctamente configurado en el equipo remoto o a que no se puede obtener acceso al equipo remoto debido a problemas de red o a la presencia de un firewall.

> [!IMPORTANT]
> Si cree que ha recibido este mensaje debido a un error del producto, [notifique este problema](../ide/how-to-report-a-problem-with-visual-studio.md) a Visual Studio. Si necesita más ayuda, vea [Talk to Us](../ide/talk-to-us.md) para obtener información sobre las distintas formas de ponerse en contacto con Microsoft.

## <a name="specificerrors"></a>¿Cuál es el mensaje de error detallado?

El mensaje `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` es genérico. Normalmente, se incluye un mensaje más específico en la cadena de error que puede ayudarle a identificar la causa del problema o a buscar una corrección más exacta. Estos son algunos de los mensajes de error más comunes que se anexan al mensaje de error principal:

- [El depurador no se puede conectar al equipo remoto. El depurador no pudo resolver el nombre de equipo especificado](#cannot_connect)
- [El depurador remoto rechazó la solicitud de conexión](#rejected)
- [Acceso no válido a la ubicación de memoria](#invalid_access)
- [No hay ningún servidor con el nombre especificado en ejecución en el equipo remoto](#no_server)
- [El nombre solicitado era válido, pero no se encontró ningún dato del tipo solicitado](#valid_name)
- [El Visual Studio Remote Debugger en el equipo de destino no se puede volver a conectar a este equipo](#cant_connect_back)
- [Acceso denegado](#access_denied)
- [Se produjo un error específico del paquete de seguridad](#security_package)

## <a name="cannot_connect"></a>El depurador no se puede conectar al equipo remoto. El depurador no pudo resolver el nombre de equipo especificado

Siga estos pasos:

1. Asegúrese de especificar un nombre de equipo y un número de Puerto válidos en el cuadro de diálogo **asociar al proceso** o en las propiedades del proyecto (para establecer las propiedades, vea [estos pasos](#server_incorrect)). El nombre del equipo debe tener el formato siguiente:

    `computername:port`

    > [!NOTE]
    > El número de puerto debe coincidir con el [número de puerto del Depurador remoto](../debugger/remote-debugger-port-assignments.md), que *se debe estar ejecutando* en el equipo de destino.

2. Si el nombre del equipo no funciona, pruebe en su lugar la dirección IP y el número de puerto.

3. Asegúrese de que la versión del Depurador remoto que se ejecuta en el equipo de destino coincide con la versión de Visual Studio. Para obtener la versión correcta del Depurador remoto, vea [depuración remota](../debugger/remote-debugging.md).

    > [!TIP]
    > Si está adjuntando al proceso y se conecta correctamente pero no ve el proceso que desea, active la **casilla Mostrar los procesos de todos los usuarios**. Se mostrarán los procesos si está conectado con una cuenta de usuario diferente.

4. Si estos pasos no resuelven este error, consulte [el equipo remoto no es accesible](#dns).

## <a name="rejected"></a>El depurador remoto rechazó la solicitud de conexión

En el cuadro de diálogo **asociar al proceso** o en las propiedades del proyecto, asegúrese de que el nombre del equipo remoto y el número de Puerto coinciden con el nombre y el número de puerto que se muestran en la ventana del Depurador remoto. Si es incorrecto, corríjalo y vuelva a intentarlo.

Si estos valores son correctos y el mensaje menciona el modo de **autenticación de Windows** , compruebe que el depurador remoto se encuentra en el modo de autenticación correcto (**Herramientas > opciones**).

## <a name="invalid_access"></a>Acceso no válido a la ubicación de memoria

Se ha producido un error interno. Reinicie Visual Studio e inténtelo de nuevo.

## <a name="no_server"></a>No hay ningún servidor con el nombre especificado en ejecución en el equipo remoto

Visual Studio no se pudo conectar al depurador remoto. Este mensaje puede producirse por varias razones:

- Es posible que el depurador remoto se esté ejecutando en una cuenta de usuario diferente. Consulte [estos pasos](#user_accounts)

- El puerto está bloqueado en el firewall. Asegúrese de que el Firewall [no está bloqueando la solicitud](#firewall), especialmente si usa un firewall de terceros.

- La versión del Depurador remoto no coincide con Visual Studio. Para obtener la versión correcta del Depurador remoto, vea [depuración remota](../debugger/remote-debugging.md).

## <a name="valid_name"></a>El nombre solicitado era válido, pero no se encontró ningún dato del tipo solicitado

El equipo remoto existe, pero Visual Studio no se pudo conectar al depurador remoto. Este mensaje puede producirse por varias razones:

- Un problema de DNS impide la conexión. Vea [estos pasos](#dns).

- Es posible que el depurador remoto se esté ejecutando en una cuenta de usuario diferente. Siga [estos pasos](#user_accounts).

- El puerto está bloqueado en el firewall. Asegúrese de que el Firewall [no está bloqueando la solicitud](#firewall), especialmente si usa un firewall de terceros.

- La versión del Depurador remoto no coincide con Visual Studio. Para obtener la versión correcta del Depurador remoto, vea [depuración remota](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>El Visual Studio Remote Debugger en el equipo de destino no se puede volver a conectar a este equipo

Es posible que el depurador remoto se esté ejecutando en una cuenta de usuario diferente. En el depurador remoto, Abra **herramientas > permisos** para agregar el usuario a los permisos del Depurador remoto. Para obtener más información, vea [el depurador remoto se está ejecutando en una cuenta de usuario diferente](#user_accounts).

Si el mensaje de error también menciona un firewall, es posible que el firewall en el equipo local impida la comunicación desde el equipo remoto a Visual Studio. Vea [estos pasos](#firewall).

## <a name="access_denied"></a> Acceso denegado

Puede ver este error si intenta depurar en un equipo remoto de 64 bits desde un equipo de 32 bits (no compatible).

## <a name="security_package"></a>Se produjo un error específico del paquete de seguridad

Puede tratarse de un problema heredado específico de Windows XP y Windows 7. Vea esta [información](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Causas y recomendaciones

### <a name="dns"></a> Falta de accesibilidad al equipo remoto

Si no puede conectarse con el nombre del equipo remoto, pruebe a usar la dirección IP en su lugar. Puede usar `ipconfig` en una línea de comandos en el equipo remoto para obtener la dirección IPv4. Si está utilizando un archivo de hosts, compruebe que está configurado correctamente.

Si se produce un error, compruebe que el equipo remoto es accesible en la red ([haga ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) en el equipo remoto). No se admite la depuración remota a través de Internet, excepto en algunos escenarios de Microsoft Azure.

### <a name="server_incorrect"></a>El nombre del servidor es incorrecto o el software de terceros está interfiriendo con el depurador remoto

En Visual Studio, examine las propiedades del proyecto y asegúrese de que el nombre del servidor es correcto. Vea los temas de [ C# y Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) y. [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus) En el caso de ASP.NET, Abra **propiedades/web/servers** o **Properties/Debug** según el tipo de proyecto.

> [!NOTE]
> Si está adjuntando al proceso, no se utiliza la configuración remota en las propiedades del proyecto.

Si el nombre del servidor es correcto, es posible que el software antivirus o un firewall de terceros estén bloqueando el depurador remoto. Al depurar localmente, esto puede ocurrir porque Visual Studio es una aplicación de 32 bits, por lo que usa la versión de 64 bits del Depurador remoto para depurar aplicaciones de 64 bits. Los procesos de 32 bits y de 64 bits se comunican con la red local dentro del equipo local. Nada de tráfico de red sale del equipo, pero es posible que el software de seguridad de terceros bloquee la comunicación.

### <a name="user_accounts"></a> Ejecución del depurador remoto bajo una cuenta de usuario diferente

De forma predeterminada, el depurador remoto solo acepta conexiones del usuario que inició el depurador remoto y los miembros del grupo administradores. A los usuarios adicionales se les deben conceder permisos explícitamente.

Puede resolver este problema de una de las siguientes formas:

- Agregue el usuario de Visual Studio a los permisos del Depurador remoto (en la ventana del Depurador remoto, elija **herramientas > permisos**).

- En el equipo remoto, reinicie el depurador remoto con la misma cuenta de usuario y la misma contraseña que usa en el equipo de Visual Studio.

    > [!NOTE]
    > Si está ejecutando el depurador remoto en un servidor remoto, haga clic con el botón derecho en la aplicación del Depurador remoto y elija **Ejecutar como administrador** (o bien, puede ejecutar el depurador remoto como servicio). Si no lo está ejecutando en un servidor remoto, inícielo normalmente.

- Puede iniciar el depurador remoto desde la línea de comandos con el parámetro **/allow \<username>** : `msvsmon /allow <username@computer>`.

- Como alternativa, puede permitir que cualquier usuario realice la depuración remota. En la ventana del depurador remoto, vaya al cuadro de diálogo **Herramientas > Opciones**. Al seleccionar   **Sin autenticación**, podrá activar **Permitir que cualquier usuario depure**. Sin embargo, debe probar esta opción solo si se produce un error en las otras opciones, o si está en una red privada.

### <a name="firewall"></a> Falta de permisos para conexiones entrantes al depurador remoto por parte del firewall del equipo remoto
 El firewall del equipo de Visual Studio y el firewall del equipo remoto deben configurarse para permitir la comunicación entre Visual Studio y el depurador remoto. Para obtener información sobre los puertos que usa el depurador remoto, vea [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Para obtener información sobre de cómo configurar el firewall de Windows, vea [Configure the Windows Firewall for Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>La versión del depurador remoto no coincide con la versión de Visual Studio
 La versión de Visual Studio que se ejecuta localmente debe coincidir con la versión del monitor de depuración remota que se ejecuta en el equipo remoto. Para solucionar este problema, descargue e instale la versión correspondiente del monitor de depuración remota. Para obtener la versión correcta del Depurador remoto, vea [depuración remota](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Los equipos locales y remotos tienen distintos modos de autenticación
 Los equipos locales y remotos deben usar el mismo modo de autenticación. Para solucionar este problema, asegúrese de que ambos equipos usan el mismo modo de autenticación. Puede cambiar el modo de autenticación. En la ventana del Depurador remoto, vaya al cuadro de diálogo **herramientas > opciones** .

 Para más información sobre la autenticación, vea [Información general de la autenticación de Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>El software antivirus está bloqueando las conexiones
 Software antivirus de Windows permite las conexiones del depurador remoto, pero algunos programas antivirus de terceros pueden bloquearlas. Consulte la documentación de su software antivirus para averiguar cómo permitir estas conexiones.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>La directiva de seguridad de red está bloqueando la comunicación entre el equipo remoto y Visual Studio
 Revise la seguridad de la red para asegurarse de que no está bloqueando la comunicación. Para obtener más información acerca de la Directiva de seguridad de red de Windows, consulte Configuración de la [Directiva de seguridad](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>La red está demasiado ocupada para admitir la depuración remota
 Puede que necesite realizar la depuración remota en otro momento o volver a programar un trabajo de la red correspondiente a otra hora distinta.

## <a name="more-help"></a>Más ayuda
 Para obtener ayuda sobre el depurador remoto, abre la página de ayuda del Depurador remoto (**ayuda > uso** en el depurador remoto).

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)
