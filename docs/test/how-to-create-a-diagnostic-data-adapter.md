---
title: Procedimiento para crear un adaptador de datos de diagnóstico
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd5d4d14267be51dfea20c43630ff9f31f6d13ac
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928624"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>Procedimiento Crear un adaptador de datos de diagnóstico

Para crear un *adaptador de datos de diagnóstico*, debe crear una biblioteca de clases mediante Visual Studio y, luego, agregar a la biblioteca de clases las API del adaptador de datos de diagnóstico proporcionadas por Visual Studio Enterprise. Al administrar los eventos que se generan durante la ejecución de pruebas, envíe la información que quiera como una secuencia o un archivo al elemento <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> proporcionado por el marco de trabajo. Las secuencias o los archivos enviados a <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink> se almacenan como datos adjuntos a los resultados de pruebas cuando una prueba finaliza. Si crea un error a partir de estos resultados de pruebas o al usar [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], los archivos también se vinculan al error.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Puede crear un adaptador de datos de diagnóstico que afecte a la máquina donde se ejecutan las pruebas, o a una máquina que forme parte del entorno que esté usando para ejecutar la aplicación que se prueba. Por ejemplo, puede recopilar archivos en la máquina de pruebas donde estas se ejecutan, o puede recopilar archivos en la máquina que desempeña el rol de servidor web para la aplicación.

Puede asignar al adaptador de datos de diagnóstico un nombre descriptivo que se muestre al crear la configuración de pruebas mediante Visual Studio o Microsoft Test Manager (en desuso en Visual Studio 2017). La configuración de pruebas permite definir qué rol de máquina ejecutará adaptadores de datos de diagnóstico concretos en el entorno. También puede configurar sus adaptadores de datos de diagnóstico al crear la configuración de pruebas. Por ejemplo, puede crear un adaptador de datos de diagnóstico que recopile los registros personalizados del servidor web. Al crear la configuración de pruebas, puede seleccionar que se ejecute este adaptador de datos de diagnóstico en la máquina o máquinas que están realizando este rol de servidor web, y puede modificar la configuración de pruebas para que solo se recopilen los tres últimos registros que se crearon. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

Cuando ejecuta las pruebas, se generan eventos de modo que el adaptador de datos de diagnóstico pueda realizar tareas en ese punto de la prueba.

> [!IMPORTANT]
> Estos eventos se pueden generar en subprocesos diferentes, sobre todo si las pruebas se ejecutan en varias máquinas. Por tanto, debe tener en cuenta los posibles problemas de subprocesamiento y debe tener cuidado de no dañar inadvertidamente los datos internos del adaptador personalizado. Asegúrese de que su adaptador de datos de diagnóstico es seguro para subprocesos.

A continuación se muestra una lista parcial de eventos clave que puede usar al crear el adaptador de datos de diagnóstico. Para obtener una lista completa de los eventos del adaptador de datos de diagnóstico, vea la clase abstracta <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>.

|evento|Descripción|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|Inicio de la ejecución de pruebas|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|Final de la ejecución de pruebas|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|Inicio de cada prueba en la ejecución de pruebas|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|Final de cada prueba en la ejecución de pruebas|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|Inicio de cada paso de prueba en una prueba|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|Final de cada paso de prueba en una prueba|

> [!NOTE]
> Cuando se completa una prueba manual, no se envían más eventos de recolección de datos al adaptador de datos de diagnóstico. Cuando se ejecute de nuevo una prueba, tendrá un nuevo identificador de caso de prueba. Si un usuario restablece una prueba durante un proceso de prueba (que genera el evento <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset>) o cambia un resultado del paso de pruebas, no se envía ningún evento de recolección de datos al adaptador de datos de diagnóstico, pero el identificador de caso de prueba sigue siendo el mismo. Para determinar si una caso de prueba se ha restablecido, debe hacer un seguimiento del identificador de caso de prueba del adaptador de datos de diagnóstico.

Utilice el siguiente procedimiento para crear un adaptador de datos de diagnóstico que recopile un archivo de datos basado en la información que se configura al crear la configuración de pruebas.

Para obtener un proyecto de adaptador de datos de diagnóstico de ejemplo completo que incluya un editor de configuración personalizado, vea [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/quickstart-create-a-load-test-project.md).

## <a name="create-and-install-a-diagnostic-data-adapter"></a>Crear e instalar un adaptador de datos de diagnóstico

1. Cree un proyecto de **Biblioteca de clases**.

2. Agregue el ensamblado **Microsoft.VisualStudio.QualityTools.ExecutionCommon**.

   1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y elija el comando **Agregar referencia**.

   2. Elija **.NET** y busque **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**.

   3. Elija **Aceptar**.

3. Agregue el ensamblado **Microsoft.VisualStudio.QualityTools.Common**.

   1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Referencias** y seleccione el comando **Agregar referencia**.

   2. Elija **/.NET** y busque **Microsoft.VisualStudio.QualityTools.Common.dll**.

   3. Elija **Aceptar**.

4. Agregue las directivas `using` siguientes al archivo de clase:

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. Agregue <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute> a la clase para que el adaptador de datos de diagnóstico lo identifique como un adaptador de datos de diagnóstico, y reemplace **Compañía**, **Producto** y **Versión** por la información apropiada del adaptador de datos de diagnóstico:

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. Agregue el atributo <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> a la clase, reemplazando los parámetros por la información apropiada para el adaptador de datos de diagnóstico:

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    Este nombre descriptivo se muestra en la actividad de configuración de pruebas.

   > [!NOTE]
   > También puede agregar <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute> para especificar el `Type` de su editor de configuración personalizado para este adaptador de datos y para especificar opcionalmente el archivo de ayuda que se va a usar para el editor.
   >
   > También puede aplicar <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute> para especificar que siempre debe estar habilitado.

7. La clase del adaptador de datos de diagnóstico debe heredar de la clase <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> del siguiente modo:

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. Agregue las variables locales como se indica a continuación:

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. Agregue el método <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> y un método **Dispose**. En el método `Initialize`, puede inicializar el receptor de datos, los datos de la configuración de pruebas y registrar los controladores de eventos que desee usar del siguiente modo:

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. Use el código de controlador de eventos y el método privado siguientes para recopilar el archivo de registro generado durante la prueba:

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     Estos archivos se adjuntan a los resultados de pruebas. Si crea un error a partir de estos resultados de pruebas o al usar [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)], los archivos también se adjuntarán al error.

     Si quiere usar un editor propio para recopilar datos que se van a usar en la configuración de pruebas, vea [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/quickstart-create-a-load-test-project.md).

11. Para recopilar un archivo de registro cuando finalice una prueba en función de lo que el usuario haya configurado en la configuración de pruebas, debe crear un archivo *App.config* y agregarlo a la solución. Este archivo tiene el siguiente formato y debe contener el URI para que el adaptador de datos de diagnóstico lo identifique. Sustituya "Compañía/NombreDeProducto/Versión" por valores reales.

    > [!NOTE]
    > Si no necesita configurar ninguna información para el adaptador de datos de diagnóstico, no necesita crear ningún archivo de configuración.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > El elemento de configuración predeterminado puede contener cualquier dato que necesite. Si el usuario no configura el adaptador de datos de diagnóstico en la configuración de pruebas, los datos predeterminados se pasarán al adaptador de datos de diagnóstico cuando se ejecute. Puesto que no es probable que el código XML que agrega a la sección `<DefaultConfigurations>` forme parte del esquema declarado, puede omitir cualquier error de XML que genere.
    >
    > Hay otros ejemplos de archivos de configuración en la ruta de acceso siguiente en función del directorio de la instalación: *Archivos de programa\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     Para obtener más información sobre cómo establecer la configuración de pruebas para que use un entorno al ejecutar las pruebas, vea [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)].

     Para obtener más información sobre la instalación del archivo de configuración, vea [Cómo: Instalar un adaptador de datos de diagnóstico personalizado](../test/quickstart-create-a-load-test-project.md)

12. Compile la solución para crear el ensamblado del adaptador de datos de diagnóstico.

13. Para obtener información sobre cómo instalar el editor personalizado, vea [Cómo: Instalar un adaptador de datos de diagnóstico personalizado](../test/quickstart-create-a-load-test-project.md).

14. Para obtener más información sobre cómo establecer la configuración de pruebas para que use un entorno al ejecutar las pruebas, vea [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)].

15. Para seleccionar el adaptador de datos de diagnóstico, antes debe seleccionar una configuración de pruebas existente o crear una en Visual Studio o Microsoft Test Manager (en desuso en Visual Studio 2017). El adaptador se muestra en la pestaña **Datos y diagnósticos** de la configuración de pruebas con el nombre descriptivo que se ha asignado a la clase.

16. Active esta configuración de pruebas. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

17. Ejecute las pruebas usando la configuración de pruebas y con el adaptador de datos de diagnóstico seleccionado.

    El archivo de datos que especificó se adjunta a los resultados de pruebas.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)
- [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)]
- [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)]
- [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/quickstart-create-a-load-test-project.md)
