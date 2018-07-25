---
title: Tiempos de espera para adaptadores de datos de diagnóstico en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, increasing time-outs
ms.assetid: 39fff4fc-9233-4f67-96ac-e81bbaf7ca82
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fca48c45af5ec93519e1688ec54677c233d2fe17
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178324"
---
# <a name="how-to-prevent-time-outs-for-diagnostic-data-adapters"></a>Cómo: Evitar los tiempos de espera para los adaptadores de datos de diagnóstico

Si utiliza adaptadores de datos de diagnóstico en la configuración de pruebas, se puede producir un tiempo de espera al iniciar la ejecución debido a una de las siguientes razones:

-   El servicio del controlador de pruebas no se está ejecutando en el equipo del controlador. Tal vez tenga que reiniciar el servicio. Para obtener más información sobre cómo determinar el controlador de pruebas y administrar los controladores de pruebas, vea [Administrar controladores de pruebas y agentes de pruebas con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

-   Si recopila datos en un equipo remoto, el firewall podría bloquear Microsoft Test Manager. El equipo que ejecuta Microsoft Test Manager debe aceptar las conexiones entrantes del controlador de pruebas. Se produce un tiempo de espera cuando Microsoft Test Manager no recibe un mensaje del controlador porque el firewall lo bloquea. Debe comprobar la configuración del firewall en el equipo que ejecuta Microsoft Test Manager.

-   El controlador de pruebas no puede resolver el nombre del equipo que ejecuta Microsoft Test Manager. Esto se podría producir si DNS proporciona la dirección equivocada para este equipo. Tendrá que ponerse en contacto con el administrador de red para resolver este problema.

Al hacer una prueba larga que debe recoger muchos datos, es posible que se agote el tiempo de recopilación. Puede utilizar el siguiente procedimiento para resolver este problema.

Puede aumentar el tiempo de espera si actualiza el archivo de configuración de Microsoft Test Manager o el archivo de configuración del agente de pruebas cuyo tiempo de espera se agota.

El archivo de configuración de Microsoft Test Manager se denomina **mtm.exe.config**. Se encuentra en el directorio siguiente: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

Para actualizar un agente de prueba, debe actualizar los siguientes archivos de configuración en el equipo del agente de prueba. Todos estos archivos se encuentran en el mismo directorio del equipo del agente de pruebas: *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE*.

-   QTAgent.exe.config

-   QTAgent32.exe.config

-   QTDCAgent.exe.config

-   QTDCAgent32.exe.config

Si ejecuta pruebas manuales y recopila los datos de un entorno, cuando se crea un error o se completa el caso de prueba, los datos recopilados por adaptadores de datos de diagnóstico se transfieren al equipo que está ejecutando las pruebas manuales. Si ha recopilado muchos datos o tiene una conexión de red lenta, llevará más tiempo que el valor predeterminado de 60 segundos. Por ejemplo, si ha configurado el adaptador de IntelliTrace para recopilar eventos de IntelliTrace e información de llamadas de muchos procesos, la transferencia de estos datos podría superar el tiempo de espera predeterminado. Para aumentar este valor, puede usar el siguiente procedimiento para actualizar **mtm.exe.config**.

Si la actividad de Test Runner o el agente de prueba agotan el tiempo de espera, se muestra un mensaje de error. El mensaje de error del agente de prueba indicará el equipo del agente de prueba que agotó el tiempo de espera. Utilice el siguiente procedimiento para actualizar los archivos de configuración, en función del mensaje de error que haya recibido.

## <a name="to-increase-the-time-outs-for-your-diagnostic-data-adapters"></a>Para aumentar los tiempos de espera de los adaptadores de datos de diagnóstico

1.  Abra una ventana del Explorador de Windows (o el Explorador de archivos).

     Para ello, haga clic con el botón derecho en **Inicio** y seleccione **Explorar**.

    > [!NOTE]
    > Es posible que necesite privilegios de administrador para actualizar el archivo.

2.  Busque el directorio *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* del equipo que contiene el archivo que debe actualizar.

3.  Haga clic con el botón derecho en el archivo y seleccione **Abrir con**. Seleccione un editor.

     El archivo se abre en el editor. Este archivo incluye muchos parámetros. La mayor parte se puede cambiar con Microsoft Test Manager. Sin embargo, la configuración de tiempo de espera se debe cambiar manualmente tal como se describe en los siguientes pasos.

4.  Debe modificar la sección de configuración de ejecución de pruebas para aumentar los valores de tiempo de espera. Esta sección tiene el siguiente formato:

    ```text
    <!-- Begin: Test execution settings -->

        <!-- How long test runner will wait for an event raised to all local data collectors to complete.  Default is 300. -->
        <add key="DataCollectorEventTimeoutInSeconds" value="300"/>

        <!-- How long test runner will wait for test run operations, such as starting or stopping a test run, to complete.  Default is 60. -->
        <add key="RunOperationTimeoutInSeconds" value="60"/>

        <!-- End: Test execution settings -->
    ```

5.  Para aumentar el tiempo que los adaptadores de datos de diagnóstico esperan hasta que se completan los eventos, aumente el valor de la clave **DataCollectorEventTimeoutInSeconds**.

6.  Si el mensaje de error de tiempo de espera hace referencia a la actividad de Test Runner, debe aumentar el valor de la clave **RunOperationTimeoutInSeconds**.

7.  Para aumentar el tiempo de espera para transferir datos de un error o cuando una prueba finaliza en el equipo que ejecuta las pruebas, agregue el siguiente tiempo de espera a **mtm.exe.config** en la sección appSettings del archivo:

    ```text
    <!-- How long test runner waits for data collected by diagnostic data adapters to be transferred to the computer. Default is 60 seconds. -->
    <add key="GetCollectorDataTimeout" value="300"/>
    ```

    > [!NOTE]
    > El valor del tiempo de espera está en segundos.

8.  Guarde los cambios que ha realizado en el archivo y vuelva a ejecutar las pruebas que agotaron el tiempo de espera previamente.

## <a name="see-also"></a>Vea también

- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)