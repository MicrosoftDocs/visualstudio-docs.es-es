---
title: Tamaño del archivo de registro de las pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, logging
ms.assetid: 417059bf-37ae-4e7a-b9b0-29bd71f1414f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 22cc77426abca46a95fd12c8954fd0965a194f5e
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894435"
---
# <a name="how-to-specify-the-maximum-size-for-the-log-file-for-load-tests"></a>Cómo: Especificar el tamaño máximo del archivo de registro de las pruebas de carga

De forma predeterminada, el tamaño máximo del archivo de registro que se utiliza para las pruebas de carga está establecido en 20 megabytes. Puede cambiar este valor modificando el archivo de configuración asociado con el servicio del controlador.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-log-file-size-for-load-test"></a>Especificar el tamaño máximo del archivo de registro de las pruebas de carga

1.  Abra el archivo de configuración XML *QTCcontroller.exe.config* que se encuentra en *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\QTCcontroller.exe.config*.

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

- [Modificar la configuración de registro de pruebas de carga](../test/modify-load-test-logging-settings.md)
- [Configurar los puertos para los controladores de prueba y los agentes de prueba](../test/configure-ports-for-test-controllers-and-test-agents.md)