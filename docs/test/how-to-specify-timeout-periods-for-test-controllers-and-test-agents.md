---
title: Periodos de tiempo de espera para controladores de pruebas y agentes de pruebas
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring
- agetns, timeouts
- controllers, configuring
- controllers, timeouts
ms.assetid: 777d0db5-0073-458a-a2a3-58b1c1f24c60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f4e82261b9b36ced471dfa3e93be085e22c4d64
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653321"
---
# <a name="how-to-specify-timeout-periods-for-test-controllers-and-test-agents"></a>Procedimiento para especificar periodos de tiempo de espera para controladores de pruebas y agentes de pruebas

Tanto el controlador de pruebas como el agente de prueba tienen varias configuraciones de tiempo de espera que especifican cuánto tiempo deben esperar las respuestas el uno del otro, o de un origen de datos antes de que se genere un error. En ciertas circunstancias, podría ser necesario editar los valores de tiempo de espera para satisfacer las necesidades de su topología u otros problemas del entorno. Para editar los valores de tiempo de espera, edite el archivo de configuración XML asociado al controlador de pruebas o al agente de prueba, como se explica en los procedimientos siguientes.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Para editar diversas configuraciones de tiempo de espera de un controlador de pruebas o de un agente de prueba, modifique los siguientes archivos de configuración usando los nombres y valores de clave de las tablas:

- Controlador de pruebas: *QTController.exe.config*

    |Nombre de clave|DESCRIPCIÓN|Valor|
    |-|-----------------|-|
    |AgentConnectionTimeoutInSeconds|Número de segundos que se va a esperar la solicitud de ping del agente antes de que la conexión se considere perdida.|"n" segundos.|
    |AgentSyncTimeoutInSeconds|Al iniciar una ejecución de pruebas de sincronización, número de segundos que se va a esperar para que todos los agentes se sincronicen antes de anular la ejecución.|"n" segundos.|
    |AgentInitializeTimeout|Número de segundos que se va a esperar para que todos los agentes y sus recopiladores de datos se inicialicen al principio de una ejecución de pruebas, antes de anular la ejecución de pruebas. Este valor debe ser bastante grande si se usan recopiladores de datos.|"n" segundos. Predeterminado: "120" (dos minutos).|
    |AgentCleanupTimeout|Número de segundos que se va a esperar para que todos los agentes y sus recopiladores de datos se limpien, antes de completar la ejecución de pruebas. Este valor debe ser bastante grande si se usan recopiladores de datos.|"n" segundos. Predeterminado: "120" (dos minutos).|

- Agente de pruebas: *QTAgentService.exe.config*

    |Nombre de clave|DESCRIPCIÓN|Valor|
    |-|-----------------|-|
    |ControllerConnectionPeriodInSeconds|Número de segundos entre los intentos de conectarse al controlador.|"n" segundos. Predeterminado: "30" (treinta segundos).|
    |RemotingTimeoutSeconds|Tiempo máximo que puede durar una llamada de comunicación remota en segundos.|"n" segundos. Predeterminado: "600" (diez minutos).|
    |StopTestRunCallTimeoutInSeconds|Número de segundos que se va a esperar la llamada para detener la ejecución de pruebas.|"n" segundos. Predeterminado: "120" (dos minutos).|
    |GetCollectorDataTimeout|Número de segundos que se va a esperar el recopilador de datos.|"n" segundos. Predeterminado: "300" (cinco minutos).|

## <a name="to-specify-agent-timeout-options-for-a-test-controller"></a>Para especificar opciones de tiempo de espera de agente para un controlador de pruebas

1. Abra el archivo de configuración XML *QTCcontroller.exe.config* que se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Busque la etiqueta `<appSettings>`.

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

3. Edite un valor existente para una de las claves de tiempo de espera del controlador de pruebas. Por ejemplo, puede cambiar el valor predeterminado de la clave `AgentConnectionTimeoutInSeconds` de dos minutos a tres minutos:

    ```xml
    <add key="AgentConnectionTimeoutInSeconds" value="180"/>
    ```

    O bien

    Agregue una clave adicional y especifique un valor de tiempo de espera. Por ejemplo, puede agregar la clave `AgentInitializeTimeout` en la sección `<appSettings>` y especificar un valor de cinco minutos:

    ```xml
    <appSettings>
            <add key="AgentInitializeTimeout" value="300"/>
    </appSettings>
    ```

## <a name="to-specify-agent-timeout-options-for-a-test-agent"></a>Para especificar opciones de tiempo de espera de agente para un agente de pruebas

1. Abra el archivo de configuración XML *QTAgentService.exe.config* que se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

2. Busque la etiqueta `<appSettings>`.

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

3. Edite un valor existente para una de las claves de tiempo de espera del agente de prueba. Por ejemplo, puede cambiar el valor predeterminado de la clave `ControllerConnectionPeriodInSeconds` de treinta segundos a un minuto:

    ```xml
    <add key="ControllerConnectionPeriodInSeconds" value="60"/>
    ```

    O bien

    Agregue una clave adicional y especifique un valor de tiempo de espera. Por ejemplo, puede agregar la clave `RemotingTimeoutSeconds` en la sección `<appSettings>` y especificar un valor de quince minutos:

    ```xml
    <appSettings>
            <add key=" RemotingTimeoutSeconds " value="900"/>
    </appSettings>
    ```

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
- [Modificar la configuración de registro de pruebas de carga](../test/modify-load-test-logging-settings.md)
- [Configurar los puertos para los controladores de prueba y los agentes de prueba](../test/configure-ports-for-test-controllers-and-test-agents.md)
- [Cómo: Enlazar un controlador de pruebas o un agente de pruebas a un adaptador de red](../test/how-to-bind-a-test-controller-or-test-agent-to-a-network-adapter.md)