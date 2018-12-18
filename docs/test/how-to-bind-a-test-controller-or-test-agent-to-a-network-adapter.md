---
title: Enlace de un controlador de pruebas o un agente de pruebas a un adaptador de red en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- controllers, netwrok adapter
- agents, configuring
- agents, network adapter
- controllers, configuring
ms.assetid: 7eb9290a-f9f6-4e41-9caa-796fcfaf0610
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 222fe589a0d4282531b9ee73d476678d54747e7b
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896057"
---
# <a name="how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter"></a>Cómo: Enlazar un controlador de pruebas o un agente de pruebas a un adaptador de red

Si un equipo que tiene instalado el controlador de prueba o el software del agente de pruebas tiene varios adaptadores de red, debe especificar la dirección IP en lugar del nombre del equipo para identificar ese controlador de pruebas o agente de prueba.

> [!WARNING]
> Al intentar configurar un agente de prueba, podría recibir el siguiente error:
>
> **Error 8110. No se puede conectar con el equipo de controlador especificado ni acceder al objeto de controlador**
>
> Si se instala el controlador de pruebas en un equipo con varios adaptadores de red, se puede producir este error. También es posible instalar agentes correctamente y no detectar este problema hasta que se ejecute una prueba.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="bind-a-test-controller-to-a-specific-network-adapter"></a>Enlazar un controlador de pruebas a un adaptador de red concreto

### <a name="to-obtain-the-ip-addresses-of-the-network-adapters"></a>Para obtener las direcciones IP de los adaptadores de red

1.  En Microsoft Windows, elija **Inicio**, elija el cuadro **Iniciar búsqueda**, escriba **cmd** y, a continuación, presione **Entrar**.

2.  Escriba **ipconfig /all**.

     Se muestran las direcciones IP de los adaptadores de red. Anote la dirección IP del adaptador de red al que desee enlazar el controlador.

### <a name="to-bind-a-network-adapter-to-a-test-controller"></a>Para enlazar un adaptador de red a un controlador de pruebas, siga estos pasos:

1.  En Microsoft Windows, elija **Inicio**, elija el cuadro **Iniciar búsqueda**, escriba **services.msc** y, a continuación, presione **Entrar**.

     Se mostrará el cuadro de diálogo **Servicios**.

2.  En el panel de resultados, bajo la columna **Nombre**, haga clic con el botón derecho en el servicio **Visual Studio Test Controller** y, a continuación, elija **Detener**.

     O bien

     Abra un símbolo del sistema con privilegios elevados y ejecute el comando siguiente:

     `net stop vsttcontroller`

3.  Abra el archivo de configuración XML *QTCcontroller.exe.config* ubicado en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  busque la etiqueta `<appSettings>`.

    ```xml
    <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentConnectionTimeoutInSeconds" value="120"/>
      <add key="AgentSyncTimeoutInSeconds" value="300"/>
      <add key="ControllerServicePort" value="6901"/>
      <add key="ControllerUsersGroup" value="TeamTestControllerUsers"/>
      <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins"/>
      <add key="CreateTraceListener" value="no"/>
    </appSettings>
    ```

5.  Agregue la clave `BindTo` para especificar qué adaptador de red se va a usar en la sección `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Inicie el servicio de controlador de pruebas. Para ello, ejecute el comando siguiente en un símbolo del sistema:

    `net start vsttcontroller`

    > [!WARNING]
    > Debe ejecutar de nuevo la instalación del agente de prueba para conectar el agente de prueba al controlador. Esta vez, especifique la dirección IP del controlador en vez de su nombre.

     Este proceso se aplica al controlador, al servicio del agente y al proceso del agente. El valor de la propiedad `BindTo` se debe establecer para cada proceso que se ejecute en un equipo que tenga más de un adaptador de red. El procedimiento para establecer la propiedad `BindTo` es el mismo para los tres procesos, tal y como se especificó anteriormente en este tema para el controlador de pruebas.

### <a name="to-bind-a-network-interface-card-to-a-test-agent"></a>Para enlazar una tarjeta de interfaz de red a un agente de prueba, siga estos pasos:

1.  En Microsoft Windows, elija **Inicio**, elija el cuadro **Iniciar búsqueda**, escriba **services.msc** y, a continuación, presione **Entrar**.

    Se mostrará el cuadro de diálogo **Servicios**.

2.  En el panel de resultados, bajo la columna **Nombre**, haga clic con el botón derecho en el servicio **Visual Studio Test Agent** y, a continuación, elija **Detener**.

     O bien

     Abra un símbolo del sistema con privilegios elevados y ejecute el comando siguiente:

     **net stop vsttagent**

3.  Abra el archivo de configuración XML *QTAgentService.exe.config* ubicado en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edition>\Common7\IDE*.

4.  busque la etiqueta `<appSettings>`.

    ```xml
    <appSettings>
      <appSettings>
      <add key="LogSizeLimitInMegs" value="20"/>
      <add key="AgentServicePort" value="6910"/>
      <add key="ControllerConnectionPeriodInSeconds" value="30"/>
      <add key="StopTestRunCallTimeoutInSeconds" value="120"/>
      <add key="CreateTraceListener" value="no"/>
      <add key="GetCollectorDataTimeout" value="300"/>
    </appSettings>  </appSettings>
    ```

5.  Agregue la clave `BindTo` para especificar qué adaptador de red se va a usar en la sección `<appSettings>`.

    ```xml
            <add key="BindTo" value="<YOUR IP ADDRESS>"/>
    </appSettings>
    ```

6.  Inicie el servicio de agente de prueba. Para ello, ejecute el comando siguiente en un símbolo del sistema:

    `net start vsttagent`

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
- [Modificar la configuración de registro de pruebas de carga](../test/modify-load-test-logging-settings.md)
- [Configurar los puertos para los controladores de prueba y los agentes de prueba](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Cómo: Especificar el tamaño máximo del archivo de registro](../test/how-to-specify-the-maximum-size-for-the-log-file.md)
- [Cómo: Especificar periodos de tiempo de espera para controladores de pruebas y agentes de pruebas](../test/how-to-specify-timeout-periods-for-test-controllers-and-test-agents.md)