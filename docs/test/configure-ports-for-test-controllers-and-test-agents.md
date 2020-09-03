---
title: Configurar los puertos para los controladores de pruebas y los agentes de pruebas
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- firewalls, configuring for test agents
- firewalls, configuring for test controllers
- test agents, firewalls
- test controllers, firewalls
- agents, firewalls
- controllers, firewalls
ms.assetid: 211edbd7-9fe4-4251-ba85-8bec4363261b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7889feffc41d6bb64b85b4ea95a17a4a986d22df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288824"
---
# <a name="configure-ports-for-test-controllers-and-test-agents"></a>Configuración de los puertos para los controladores de pruebas y los agentes de pruebas

Puede cambiar los puertos de entrada predeterminados que usan por el controlador y el agente de pruebas y el cliente. Esto podría ser necesario si intenta usar el controlador, el agente de prueba o el cliente junto con algún otro software en conflicto con la configuración de los puertos. Otra razón para cambiar los puertos es la restricción del firewall entre el controlador de prueba y el cliente. En este caso podría configurar el puerto para habilitarlo para un firewall manualmente de forma que el controlador de prueba pueda enviar los resultados al cliente.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

La siguiente ilustración muestra los puntos de conexión entre el controlador de prueba, el agente de prueba y el cliente. Describe qué puertos se usan para las conexiones entrantes y salientes, así como las restricciones de seguridad empleadas en estos puertos.

![Puertos y seguridad del controlador y el agente de pruebas](../test/media/test-controller-agent-firewall.png)

## <a name="incoming-connections"></a>Conexiones entrantes

El puerto predeterminado utilizado por el controlador de prueba es 6901 y el puerto predeterminado del agente es 6910. El cliente utiliza un puerto aleatorio de forma predeterminada que se utiliza para recibir los resultados del controlador de pruebas. Para todas las conexiones entrantes, el controlador autentica la entidad de la llamada y comprueba que pertenece al grupo de seguridad concreto.

- **Controlador de pruebas** Las conexiones de entrada están en el puerto TCP 6901. Si es necesario, puede configurar el puerto de entrada. Para más información, vea [Configurar los puertos entrantes](#configure-the-incoming-ports).

    El controlador de pruebas necesita realizar la conexión de salida a los agentes de prueba y al cliente.

    > [!NOTE]
    > El controlador de pruebas necesita que la conexión **Compartir archivos e impresoras** de entrada esté abierta.

- **Agente de prueba** Las conexiones entrantes están en el puerto TCP 6910. Si es necesario, puede configurar el puerto de entrada. Para más información, vea [Configurar los puertos entrantes](#configure-the-incoming-ports).

   El agente de prueba necesita realizar la conexión de salida al controlador de prueba.

- **Cliente** De forma predeterminada, para las conexiones entrantes se usa un puerto TCP aleatorio. Si es necesario, puede configurar el puerto de entrada. Para más información, vea [Configurar los puertos entrantes](#configure-the-incoming-ports).

   Podría obtener las notificaciones del firewall cuando el controlador de prueba intenta conectar la primera vez al cliente.

   En Windows Server 2008, las notificaciones de firewall están deshabilitadas de manera predeterminada y debe agregarlas manualmente en los programas cliente (*devenv.exe*, *mstest.exe* y *mlm.exe*) para que acepten las conexiones de entrada.

## <a name="outgoing-connections"></a>Conexiones salientes

Los puertos TCP aleatorios se utilizan para todas las conexiones de salida.

- **Controlador de pruebas** El controlador de pruebas necesita realizar la conexión de salida a los agentes y al cliente.

- **Agente de prueba** El agente de prueba necesita realizar la conexión de salida al controlador.

- **Cliente** El cliente necesita realizar la conexión de salida al controlador.

## <a name="configure-the-incoming-ports"></a>Configurar los puertos entrantes

Siga estas instrucciones para configurar los puertos para un controlador de pruebas y agentes de prueba.

- **Servicio de controlador** Modifique el valor del puerto editando el archivo *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*:

    ```xml
    <appSettings>
      <add key="ControllerServicePort" value="6901"/>
    </appSettings>
    ```

- **Servicio de agente** Modifique el valor del puerto editando el archivo *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTAgentService.exe.config*:

    ```xml
    <appSettings>
      <add key="AgentServicePort" value="6910"/>
    </appSettings>
    ```

- **Cliente** Use el editor del Registro para agregar los siguientes valores (**DWORD**). El cliente utilizará uno de los puertos del rango especificado para recibir los datos del controlador de prueba:

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeStart**

     **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VisualStudio\12.0\EnterpriseTools\QualityTools\ListenPortRange\PortRangeEnd**

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
