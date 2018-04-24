---
title: Tamaño del archivo de registro de las pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: b7ce416a587a325565a274ddb8a9f8e9bd5730c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Cómo: Especificar el tamaño máximo del archivo de registro de las pruebas de carga

De forma predeterminada, el tamaño máximo del archivo de registro que se utiliza para las pruebas de carga está establecido en 20 megabytes. Puede cambiar este valor modificando el archivo de configuración asociado con el servicio del controlador.

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Especificar el tamaño máximo del archivo de registro para las pruebas de carga

1.  Abra el archivo de configuración XML *QTCcontroller.exe.config* que se encuentra en %ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config.

2.  Busque la entrada `<add key="LogSizeLimitInMegs" value="20"/>` bajo la etiqueta `<appSettings>`.

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

3.  Modifique `value ="20"` al tamaño permitido el máximo que desea especificar para el archivo de registro.

    > [!NOTE]
    > Con un valor de "0" se especifica que el archivo de registro solo se limita en tamaño por el espacio en disco disponible.

## <a name="see-also"></a>Vea también

- [Modificar la configuración de inicio de sesión de las pruebas de carga](../test/modify-load-test-logging-settings.md)
- [Configurar los puertos para los controladores de pruebas y los agentes de pruebas](../test/configure-ports-for-test-controllers-and-test-agents.md)