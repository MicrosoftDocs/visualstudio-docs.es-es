---
title: Solución de problemas de controladores de pruebas y agentes de pruebas
ms.date: 10/20/2016
ms.topic: troubleshooting
helpviewer_keywords:
- load tests, test controllers
- load tests, troubleshooting
- load tests, test agents
- troubleshooting, test controllers and agents in load tests
ms.assetid: 77329348-3a5d-43de-b6cb-90f93296a081
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51d7e15ec71eec7134dfc49b3515385970e593a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565960"
---
# <a name="strategies-for-troubleshooting-test-controllers-and-test-agents-in-load-tests"></a>Estrategias para solucionar problemas de controladores de pruebas y agentes de pruebas en pruebas de carga

En este artículo se tratan algunos problemas comunes que pueden aparecer cuando se trabaja con controladores y agentes de pruebas en Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="unable-to-collect-performance-counters-on-test-agent-computer"></a>No se pueden recopilar contadores de rendimiento en el equipo de agente de pruebas

Al ejecutar una prueba de carga, puede recibir errores al intentar conectarse a un equipo de agente de prueba y recopilar los contadores de rendimiento. El servicio de registro remoto es el servicio responsable de proporcionar los datos del contador de rendimiento a un equipo remoto. En algunos sistemas operativos, el servicio Registro remoto no se inicia automáticamente. Para corregir este problema, inicie manualmente el servicio Registro remoto.

> [!NOTE]
> Puede acceder al servicio Registro remoto en el **Panel de control**. Elija **Herramientas administrativas** y, luego, **Servicios**.

Otro motivo de este problema es no disponer de los permisos adecuados para leer los contadores de rendimiento. En las ejecuciones de pruebas locales, la cuenta del usuario que ejecuta la prueba debe ser miembro del grupo Usuarios avanzados, o superior, o del grupo Usuarios del monitor de sistema. En las ejecuciones de pruebas remotas, la cuenta en la que se configura la ejecución del controlador debe ser miembro del grupo Usuarios avanzados, o superior, o del grupo Usuarios del monitor del sistema.

## <a name="set-the-logging-level-on-a-test-controller-computer"></a>Establecer el nivel del registro en un equipo de controlador de pruebas

Puede controlar el nivel de registro de un equipo de controlador de pruebas. Resulta útil cuando se intenta diagnosticar un problema cuando se ejecuta una prueba de carga en un entorno.

### <a name="to-set-the-logging-level-on-a-test-controller-computer"></a>Para establecer el nivel del registro de un equipo de controlador de pruebas

1. Detenga el servicio de controlador de pruebas. En un símbolo del sistema, escriba `net stop vsttcontroller`.

2. Abra el archivo *QTController.exe.config*. Este archivo se encuentra en el directorio de instalación del controlador.

3. Edite la entrada del modificador `EqtTraceLevel` de la sección de diagnósticos del sistema del archivo. Su código debería ser similar a este:

    ```xml
    <system.diagnostics>
        <trace autoflush="true" indentsize="4">
            <listeners>
                <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="d:\VSTestHost.log" />
            </listeners>
        </trace>
        <switches>
            <!-- You must use integral values for "value":
                    0 = off,
                    1 = error,
                    2 = warn,
                    3 = info,
                    4 = verbose. -->
            <add name="EqtTraceLevel" value="4" />
        </switches>
    </system.diagnostics>
    ```

4. Guarde el archivo.

5. Inicie el servicio del controlador. En un símbolo del sistema, escriba `net start vsttcontroller`.

Este proceso se aplica al controlador de pruebas, y al servicio y al proceso del agente de prueba. Al diagnosticar los problemas, es útil habilitar el registro en los tres procesos. El procedimiento para establecer el nivel de registro es el mismo para los tres procesos, tal y como se especificó anteriormente para el controlador de pruebas. Para establecer los niveles de registro del servicio del agente de prueba y del proceso del agente, use los siguientes archivos de configuración:

- *QTController.exe.config* Servicio del controlador.

- *QTAgentService.exe.config* Servicio del agente.

- *QTDCAgent(32).exe.config* Proceso del adaptador de datos del agente para arquitectura de 32 bits.

- *QTDCAgent(64).exe.config* Proceso del adaptador de datos del agente para arquitectura de 64 bits.

- *QTAgent(32).exe.config* Proceso de prueba del agente para arquitectura de 32 bits.

- *QTAgent(64).exe.config* Proceso de prueba del agente para arquitectura de 64 bits.

## <a name="bind-a-test-controller-to-a-network-adapter"></a>Enlazar un controlador de pruebas a un adaptador de red

Al intentar configurar un agente de prueba, podría recibir el siguiente error:

**Error 8110. No se puede conectar con el equipo de controlador especificado ni acceder al objeto de controlador.**

Si se instala el controlador de pruebas en un equipo con varios adaptadores de red, se puede producir este error.

> [!NOTE]
> También es posible instalar los agentes de prueba correctamente y no detectar este problema hasta que se ejecute una prueba.

Para corregir este error, debe enlazar el controlador de pruebas a uno de los adaptadores de red. Debe establecer la propiedad `BindTo` en el controlador de pruebas y, a continuación, cambiar el agente de prueba para que haga referencia al controlador de pruebas mediante la dirección IP en vez del nombre. Los pasos se facilitan en los procedimientos siguientes.

### <a name="to-obtain-the-ip-address-of-the-network-adapter"></a>Para obtener la dirección IP del adaptador de red

1. Elija **Inicio** y, luego, **Ejecutar**.

     Se muestra el cuadro de diálogo **Ejecutar**.

2. Escriba `cmd` y, luego, elija **Aceptar**.

     Se abrirá un símbolo del sistema.

3. Escriba `ipconfig /all`.

     Se muestran las direcciones IP de los adaptadores de red. Anote la dirección IP del adaptador de red al que desee enlazar el controlador.

### <a name="to-bind-a-test-controller-to-a-network-adapter"></a>Para enlazar un controlador de pruebas a un adaptador de red

1. Detenga el servicio de controlador de pruebas. En un símbolo del sistema, escriba `net stop vsttcontroller`.

2. Abra el archivo *QTController.exe.config*. Este archivo se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

3. Agregue una entrada para la propiedad `BindTo` a la configuración de la aplicación. Especifique la dirección IP del adaptador de red al que desee enlazar el controlador. Su código debería ser similar a este:

    ```xml
    <appSettings>
        <add key="LogSizeLimitInMegs" value="20" />
        <add key="AgentSyncTimeoutInSeconds" value="120" />
        <add key="ControllerServicePort" value="6901" />
        <add key="ControllerUsersGroup" value="TeamTestControllerUsers" />
        <add key="ControllerAdminsGroup" value="TeamTestControllerAdmins" />
        <add key="CreateTraceListener" value="no" />
        <add key="BindTo" value="<YOUR IP ADDRESS>" />
    </appSettings>
    ```

4. Guarde el archivo.

5. Inicie el servicio de controlador de pruebas. En un símbolo del sistema, escriba `net start vsttcontroller`.

### <a name="to-connect-a-test-agent-to-a-bound-controller"></a>Para conectar un agente de prueba a un controlador enlazado

- Vuelva a ejecutar el proceso de instalación del agente de prueba. Esta vez, especifique la dirección IP del controlador de pruebas en lugar de su nombre.

Este proceso se aplica al controlador de pruebas, y al servicio y al proceso del agente de prueba. El valor de la propiedad `BindTo` se debe establecer para cada proceso que se ejecute en un equipo que tenga más de un adaptador de red. El procedimiento para establecer la propiedad `BindTo` es el mismo para los tres procesos, tal y como se especificó anteriormente para el controlador de pruebas. Para establecer los niveles de registro del servicio del agente de pruebas y el proceso del agente de pruebas, use los archivos de configuración que se especifican en [Establecer el nivel del registro en un equipo de controlador de pruebas](#set-the-logging-level-on-a-test-controller-computer).

## <a name="see-also"></a>Vea también

- [Controladores y agentes de prueba](../test/configure-test-agents-and-controllers-for-load-tests.md)
