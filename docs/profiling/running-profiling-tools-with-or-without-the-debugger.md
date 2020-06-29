---
title: Ejecución de herramientas de generación de perfiles con o sin el depurador | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285930"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ejecutar herramientas de generación de perfiles con o sin el depurador

Visual Studio ofrece varias herramientas de generación de perfiles y medición del rendimiento. Algunas herramientas, como Uso de CPU y Uso de memoria, pueden ejecutarse con o sin el depurador, y en las configuraciones de compilación de depuración o de versión. Las herramientas del Generador de perfiles de rendimiento, como Escala de tiempo de la aplicación, pueden ejecutarse en compilaciones de depuración o de versión. Las herramientas integradas del depurador, como la ventana Herramientas de diagnóstico y la pestaña Eventos solo se ejecutan durante las sesiones de depuración.

>[!NOTE]
>Puede usar las herramientas de rendimiento sin depurador con Windows 7 y versiones posteriores. Se necesita Windows 8 o versiones posteriores para ejecutar las herramientas de generación de perfiles integradas del depurador.

El Generador de perfiles de rendimiento sin depurador y las Herramientas de diagnóstico integradas en el depurador proporcionan información y experiencias diferentes. Las herramientas integradas del depurador muestran los puntos de interrupción y los valores de variable. Las herramientas sin depurador ofrecen resultados más cercanos a la experiencia del usuario final.

Para ayudarlo a decidir qué herramientas y resultados debe utilizar, tenga en cuenta lo siguiente:

- Los problemas de rendimiento externo, como problemas de la capacidad de respuesta de la red o de E/S de archivos, no se diferenciarán demasiado en las herramientas con o sin depurador.
- En el caso de problemas causados por llamadas con gran consumo de CPU, puede haber diferencias de rendimiento considerables entre las compilaciones de versión y de depuración. Compruebe si el problema existe en las compilaciones de versión.
- Si el problema se produce solo durante las compilaciones de depuración, probablemente no necesitará ejecutar las herramientas sin depurador. En el caso de problemas de compilaciones de versión, deberá decidir si las herramientas del depurador le ayudarán en la investigación.
- Las compilaciones de versión proporcionan optimizaciones como la inclusión de llamadas a funciones y constantes, la eliminación de rutas de acceso a código sin usar y el almacenamiento de variables de manera que no las pueda usar el depurador. Los números de rendimiento de las herramientas integradas del depurador son menos precisos, porque las compilaciones de depuración carecen de estas optimizaciones.
- El propio depurador cambia los tiempos de rendimiento, ya que realiza operaciones de depurador necesarias como interceptar excepciones y modular eventos de carga.
- Los números de rendimiento de la compilación de versión de las herramientas del Generador de perfiles de rendimiento son más precisos y exactos. Los resultados de la herramienta integrada del depurador son más útiles si se comparan con otras medidas relacionadas con la depuración.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Recopilar datos de generación de perfiles durante la depuración

Al comenzar la depuración en Visual Studio seleccionando **Depurar** > **Iniciar depuración** o presionando **F5**, la ventana **Herramientas de diagnóstico** aparece de forma predeterminada. Para abrirla manualmente, seleccione **Depurar** > **Ventanas** > **Mostrar herramientas de diagnóstico**. En la ventana **Herramientas de diagnóstico** se muestra información sobre el uso de CPU, la memoria de proceso y los eventos.

![Instantánea de la ventana Herramientas de diagnóstico](../profiling/media/diagnostictoolswindow.png "Ventana Herramientas de diagnóstico")

- Use el icono **Configuración** en la barra de herramientas para seleccionar si quiere ver el **Uso de memoria**, el **Análisis de UI**, y el **Uso de CPU**.

- Seleccione **Configuración** en la lista desplegable **Configuración** para abrir las **páginas de propiedades de las Herramientas de diagnóstico** con más opciones.

- Si ejecuta Visual Studio Enterprise, puede habilitar o deshabilitar IntelliTrace en **Herramientas** > **Opciones** > **IntelliTrace**.

La sesión de diagnóstico termina cuando se detiene la depuración.

### <a name="the-events-tab"></a>La pestaña Eventos

Durante una sesión de depuración, en la pestaña Eventos de la ventana Herramientas de diagnóstico se enumeran los eventos de diagnóstico que se producen. Los prefijos de categoría: *Punto de interrupción*, *Archivo* y otros, le permiten examinar rápidamente la lista en busca de una categoría u omitir las categorías que no le interesan.

Use la lista desplegable **Filtro** para filtrar los eventos dentro y fuera de la vista activando o desactivando categorías de eventos concretas.

![Captura de pantalla de filtro de eventos de diagnóstico](../profiling/media/diagnosticeventfilter.png "Filtro de eventos de diagnóstico")

Use el cuadro de búsqueda para encontrar una cadena concreta en la lista de eventos. Estos son los resultados de una búsqueda de la cadena *name* que coincide con cuatro eventos:

![Captura de pantalla de la búsqueda de eventos de diagnóstico](../profiling/media/diagnosticseventsearch.png "Búsqueda de eventos de diagnóstico")

Para más información, consulte [Búsqueda y filtrado de la pestaña Eventos de la ventana de herramientas de diagnóstico](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Recopilar datos de generación de perfiles sin depurar

Para recopilar datos de rendimiento sin depuración, puede ejecutar las herramientas del Generador de perfiles de rendimiento.

1. Con un proyecto abierto en Visual Studio, establezca la configuración de la solución en  **Versión** y seleccione  **Depurador local de Windows**  (o  **Máquina local**) como destino de la implementación.

1. Seleccione **Depurar** > **Generador de perfiles de rendimiento**, o bien presione **Alt**+**F2**.

1. En la página de inicio de las herramientas de diagnóstico, elija una o varias herramientas para ejecutar. Solo se muestran las herramientas que se pueden aplicar para el tipo de proyecto, el sistema operativo y el lenguaje de programación. Haga clic en **Mostrar todas las herramientas** para ver también herramientas que están deshabilitadas para esta sesión de diagnóstico.

   ![Captura de pantalla de las herramientas de diagnóstico](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Para iniciar la sesión de diagnóstico, haga clic en **Iniciar**.

   Mientras se ejecuta la sesión, algunas herramientas muestran gráficos de datos en tiempo real en la página de las herramientas de diagnóstico, así como controles para pausar y reanudar la recopilación de datos.

    ![Captura de pantalla de la recopilación de datos en el centro de Rendimiento y diagnósticos](../profiling/media/diaghubcollectdata.png "Centro de recopilación de datos")

1. Para finalizar la sesión de diagnóstico, haga clic en **Detener recopilación**.

   Los datos analizados se muestran en la página **Informe**.

Puede guardar los informes y abrirlos desde la lista **Sesiones abiertas recientemente** de la página de inicio de Herramientas de diagnóstico.

![Captura de pantalla de la lista Sesiones abiertas recientemente de Herramientas de diagnóstico](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Recopilación de datos de generación de perfiles desde la línea de comandos

Para medir los datos de rendimiento desde la línea de comandos, puede usar VSDiagnostics.exe, que se incluye en Visual Studio o en las Herramientas remotas. Esta herramienta resulta útil para capturar seguimientos de rendimiento en sistemas en los que no está instalado Visual Studio, o para generar scripts de la colección de seguimientos de rendimiento. Cuando se usa VSDiagnostics.exe, se inicia una sesión de diagnóstico en la que se capturan y almacenan los datos de generación de perfiles hasta que se detiene la herramienta. En ese momento, esos datos se exportan a un archivo .diagsession, que puede abrir en Visual Studio para analizar los resultados.

### <a name="launch-an-application"></a>Inicio de una aplicación

1. Abra un símbolo del sistema y cambie al directorio con VSDiagnostics.exe:

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. Inicie VSDiagnostics.exe con el siguiente comando:

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   Debe incluir los siguientes argumentos:

   - \<id\>: identifica la sesión de recopilación. El identificador debe ser un número entre 1 y 255.
   - \<appToLaunch\>: el archivo ejecutable que se va a iniciar y para el que se van a generar perfiles.
   - \<configFile\>: el archivo de configuración del agente de recopilación que quiere iniciar.

3. Para detener la recopilación y ver los resultados, siga los pasos de la sección "Detención de la recopilación" más adelante en este artículo.

### <a name="attach-to-an-existing-application"></a>Asociación a una aplicación existente

1. Abra una aplicación, como Bloc de notas, y, luego, abra el **Administrador de tareas** para obtener su identificador de proceso (PID). En el Administrador de tareas, busque el PID en la pestaña  **Detalles** .
2. Abra un símbolo del sistema y cambie al directorio con el ejecutable del agente de recopilación. Normalmente, está aquí:

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. Inicie el archivo VSDiagnostics.exe con el siguiente comando.

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Debe incluir los siguientes argumentos:

   - \<id\>: identifica la sesión de recopilación. El identificador debe ser un número entre 1 y 255.
   - \<pid\>: el PID del proceso para el que quiere generar el perfil que, en este caso, es el PID del paso 1.
   - \<configFile\>: el archivo de configuración del agente de recopilación que quiere iniciar. Para más información, consulte  [Archivos de configuración de agentes](../profiling/profile-apps-from-command-line.md).

4. Para detener la recopilación y ver los resultados, siga los pasos de la sección siguiente.

### <a name="stop-collection"></a>Detención de la recopilación

1. Detenga la sesión de recopilación y envíe la salida a un archivo con el siguiente comando.

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. Vaya a la salida del archivo desde el comando anterior y ábrala en Visual Studio para examinar la información recopilada.

## <a name="agent-configuration-files"></a>Archivos de configuración de agentes

Los agentes de recopilación son componentes intercambiables que recopilan diferentes tipos de datos, según lo que se intente medir.
Por comodidad, puede almacenar esa información en un archivo de configuración de agente. El archivo de configuración es un archivo .json que contiene, como mínimo, el nombre del archivo .dll y su CLSID COM. Estos son los archivos de configuración de ejemplo que se pueden encontrar en la siguiente carpeta:

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

Consulte los vínculos siguientes para descargar y ver los archivos de configuración del agente:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

Las configuraciones de CpuUsage (base/alta/baja) corresponden a los datos recopilados de la herramienta de generación de perfiles  [Uso de CPU](../profiling/cpu-usage.md).
Las configuraciones de DotNetObjectAlloc (base/baja) corresponden a los datos recopilados de la  [herramienta de asignación de objetos .NET](../profiling/dotnet-alloc-tool.md).

Las configuraciones Base/Baja/Alta hacen referencia a la velocidad de muestreo. Por ejemplo, Baja es 100 muestras por segundo y Alta es 4000 muestras por segundo.
Para que la herramienta VSDiagnostics.exe funcione con un agente de recopilación, se necesita un archivo DLL y un CLSID COM para el agente adecuado. El agente también puede tener opciones de configuración adicionales. Si usa un agente sin un archivo de configuración, utilice el formato del siguiente comando:

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```
