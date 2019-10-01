---
title: Configuración de pruebas unitarias con un archivo .runsettings
ms.date: 06/14/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 25d0f49939a42d9a9b8cc56f03ed37ab83aa98f2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251828"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configuración de pruebas unitarias con un archivo *.runsettings*

En Visual Studio las pruebas unitarias se pueden configurar mediante un archivo *.runsettings*. Por ejemplo, se puede cambiar la versión de .NET en la que se ejecutan las pruebas, el directorio de los resultados de las pruebas o los datos recopilados durante una serie de pruebas.

Los parámetros de ejecución son opcionales. Si no es necesaria una configuración especial, no se necesita un archivo *.runsettings*. Un uso común de un archivo *.runsettings* es para personalizar el [análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Especificar un archivo de parámetros de ejecución

Los archivos de parámetros de ejecución se pueden usar para configurar pruebas que se ejecuten desde la [línea de comandos](vstest-console-options.md), en el IDE o en un [flujo de trabajo de compilación](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) mediante Azure Test Plans o Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Para especificar un archivo de parámetros de ejecución en el IDE, seleccione **Prueba** > **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas** y, luego, el archivo *.runsettings*.

![Selección del menú del archivo de configuración de pruebas en Visual Studio 2017](media/select-test-settings-file.png)

El archivo aparece en el menú Configuración de pruebas, y puede seleccionarlo o anular la selección. Mientras está seleccionado, el archivo de parámetros de ejecución se aplica siempre que seleccione **Analizar cobertura de código**.

::: moniker-end

::: moniker range=">=vs-2019"

Para especificar un archivo de parámetros de ejecución en el IDE, en el **Explorador de pruebas**, seleccione la flecha del botón **Configuración** y, después, **Seleccionar archivo de configuración**. Busque y seleccione el archivo *.runsettings*.

![Selección del menú del archivo de configuración de pruebas en Visual Studio 2019](media/vs-2019/select-test-settings-file.png)

El archivo aparece en el menú Configuración del Explorador de pruebas, y puede seleccionarlo o anular la selección. Mientras está seleccionado, el archivo de parámetros de ejecución se aplica siempre que seleccione **Analizar cobertura de código**.

::: moniker-end

### <a name="command-line"></a>Línea de comandos

Para ejecutar pruebas desde la línea de comandos, utilice *vstest.console.exe* y especifique el archivo de configuración mediante el parámetro **/Settings**.

1. Abra el símbolo del sistema de Visual Studio Developer:

   ::: moniker range="vs-2017"

   En el menú **Inicio** de Windows, elija **Visual Studio 2017** > **Símbolo del sistema para desarrolladores de VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   En el menú **Inicio** de Windows, elija **Visual Studio 2019** > **Símbolo del sistema para desarrolladores de VS 2019**.

   ::: moniker-end

2. Escriba un comando similar a:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   o

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Para obtener más información, vea [Opciones de la línea de comandos para VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Personalización de pruebas

Para personalizar las pruebas mediante un archivo *.runsettings*, siga estos pasos:

1. Agregue un archivo XML a la solución de Visual Studio y cámbiele el nombre por *test.runsettings*.

   > [!TIP]
   > El nombre de archivo no importa, siempre que use la extensión *.runsettings*.

2. Reemplace el contenido del archivo por el XML del ejemplo que hay a continuación y personalícelo como sea necesario.

::: moniker range="vs-2017"

3. En el menú **Prueba**, elija **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas**. Vaya al archivo *.runsettings* que ha creado y haga clic en **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Para seleccionar el archivo de parámetros de ejecución, en el **Explorador de pruebas**, seleccione la flecha del botón **Configuración** y, después, seleccione **Seleccionar archivo de configuración**. Vaya al archivo *.runsettings* que ha creado y haga clic en **Aceptar**.

::: moniker-end

   > [!TIP]
   > Puede crear más de un archivo *.runsettings* en la solución y seleccionar uno como archivo de configuración de pruebas activo según sea necesario.

## <a name="example-runsettings-file"></a>Archivo de ejemplo *.runsettings*

El siguiente XML muestra el contenido de un archivo *.runsettings* típico. Cada elemento del archivo es opcional, porque cada valor tiene un valor predeterminado.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the test settings menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
           <!-- Change to "false" to only add video attachments to failed tests -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true" xmlns="" />
        </Configuration>
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Elementos de un archivo *.runsettings*

En las secciones siguientes se detallan los elementos de un archivo *.runsettings*.

### <a name="run-configuration"></a>Configuración de ejecución

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

El elemento **RunConfiguration** puede incluir los siguientes elementos:

|Nodo|Default|Valores|
|-|-|-|
|**ResultsDirectory**||Directorio en el que se colocan los resultados de las pruebas.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` para orígenes de .NET Core, `FrameworkUap10` para orígenes basados en UWP, `Framework45` para .NET Framework 4.5 y versiones superiores, `Framework40` para .NET Framework 4.0 y `Framework35` para .NET Framework 3.5.<br /><br />Este valor especifica qué versión del marco de pruebas unitarias se usa para detectar y ejecutar las pruebas. Puede ser diferente de la versión de la plataforma .NET que especifique en las propiedades de compilación del proyecto de prueba unitaria.<br /><br />Si omite el elemento `TargetFrameworkVersion` del archivo *.runsettings*, la plataforma determinará de forma automática la versión de Framework en función de los archivos binarios compilados.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|False|false, true|
|**TestAdaptersPaths**||Una o varias rutas de acceso al directorio donde se encuentran los TestAdapters|
|**MaxCpuCount**|1|Este valor controla el grado de ejecución de pruebas paralelas cuando se ejecutan pruebas unitarias, mediante los núcleos disponibles en la máquina. El motor de ejecución de pruebas se inicia como un proceso distinto en cada núcleo disponible y proporciona a cada núcleo un contenedor con las pruebas que se van a ejecutar. Un contenedor puede ser un ensamblado, un archivo DLL o un artefacto relevante. El contenedor de pruebas es la unidad de programación. En cada contenedor, las pruebas se ejecutan según el marco de pruebas. Si hay muchos contenedores, a medida que los procesos finalizan la ejecución de las pruebas en un contenedor, se les proporciona el siguiente contenedor disponible.<br /><br />El valor de MaxCpuCount puede ser:<br /><br />n, donde 1 <= n <= número de núcleos: se inician hasta n procesos<br /><br />n, donde n = cualquier otro valor: el número de procesos que se inician puede ser como máximo el número de núcleos disponibles|
|**TestSessionTimeout**||Permite a los usuarios terminar una sesión de prueba cuando esta supera un tiempo de espera especificado. La configuración de un tiempo de espera garantiza que los recursos se utilicen de manera conveniente y que las sesiones de prueba se limiten a un tiempo establecido. Esta opción está disponible en **Visual Studio 2017, versión 15.5** y posteriores.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptadores de datos de diagnóstico (recopiladores de datos)

El elemento **DataCollectors** especifica la configuración de los adaptadores de datos de diagnóstico. Los adaptadores de datos de diagnóstico recopilan información adicional sobre el entorno y la aplicación en pruebas. Cada adaptador tiene una configuración predeterminada, por lo que solo tiene que proporcionar valores si no quiere usar los predeterminados.

#### <a name="code-coverage-adapter"></a>Adaptador de cobertura de código

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

El recopilador de datos de cobertura de código crea un registro de las partes del código de aplicación que se han empleado en las pruebas. Para obtener más información sobre la personalización de los valores de cobertura de código, vea [Personalizar el análisis de la cobertura de código](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Recopilador de datos de vídeo

El recopilador de datos de vídeo captura una grabación de pantalla cuando se ejecutan las pruebas. Esta grabación es útil para solucionar problemas de pruebas de interfaz de usuario. El recopilador de datos de vídeo está disponible en **Visual Studio 2017, versión 15.5** y posteriores.

Para personalizar cualquier otro tipo de adaptador de datos de diagnóstico, use un [archivo de configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
</TestRunParameters>
```

Los parámetros de la serie de pruebas proporcionan una manera de definir las variables y los valores que están disponibles para las pruebas en tiempo de ejecución. Obtener acceso a los parámetros mediante la propiedad <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Para usar parámetros de serie de pruebas, agregue un campo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> privado y una propiedad <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pública a la clase de prueba.

### <a name="mstest-run-settings"></a>Parámetros de ejecución de MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Estos valores son específicos del adaptador de pruebas que ejecuta métodos de prueba con el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

|Configuración|Default|Valores|
|-|-|-|
|**ForcedLegacyMode**|False|En Visual Studio 2012, el adaptador MSTest se optimizó para que fuera más rápido y escalable. Es posible que parte del comportamiento, como el orden en que se ejecutan las pruebas, no sea exactamente igual que en ediciones anteriores de Visual Studio. Establezca este valor en **true** para utilizar el adaptador de pruebas más antiguo.<br /><br />Por ejemplo, es posible usar este valor si tiene un archivo *app.config* especificado para una prueba unitaria.<br /><br />Se recomienda que considere la refactorización de las pruebas para poder usar el adaptador más reciente.|
|**IgnoreTestImpact**|False|La característica de impacto de pruebas asigna prioridades a las pruebas afectadas por cambios recientes, cuando se ejecuta en MSTest o desde Microsoft Test Manager. Esta configuración desactiva la característica. Para obtener más información, vea [¿Qué pruebas se deben ejecutar desde una compilación anterior?](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Puede especificar un archivo de configuración de pruebas para usarlo con el adaptador MSTest aquí. También puede especificarlo [en el menú Configuración](#ide).<br /><br />Si especifica este valor, también debe establecer **ForcedlegacyMode** en **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|False|Una vez completada una serie de pruebas, se cierra MSTest. Cualquier proceso que se inicie como parte de la prueba también se elimina. Si quiere mantener activo el ejecutor de pruebas, establezca este valor en **true**. Por ejemplo, podría usar esta configuración para mantener el explorador en ejecución entre pruebas de IU codificadas.|
|**DeploymentEnabled**|true|Si el valor se establece en **false**, los elementos de implementación especificados en el método de prueba no se copian al directorio de implementación.|
|**CaptureTraceOutput**|true|Puede escribir en el seguimiento de depuración desde su método de prueba mediante <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Para conservar el directorio de implementación después de una serie de pruebas, establezca este valor en **false**.|
|**MapInconclusiveToFailed**|False|Si una prueba finaliza un estado no concluyente, se le asigna el estado Omitido en el **Explorador de pruebas**. Si quiere que las pruebas no concluyentes se muestren como Error, establezca el valor en **true**.|
|**InProcMode**|False|Si quiere que las pruebas se ejecuten en el mismo proceso que el adaptador MSTest, establezca este valor en **true**. Este valor proporciona una pequeña mejora del rendimiento. Pero si una prueba finaliza con una excepción, el resto de pruebas no se ejecutarán.|
|**AssemblyResolution**|False|Puede especificar rutas de acceso a ensamblados adicionales cuando busque y ejecute pruebas unitarias. Por ejemplo, puede utilizar estas rutas de acceso para los ensamblados de dependencias que no estén en el mismo directorio que el ensamblado de pruebas. Para especificar una ruta de acceso, use un elemento **Directory Path**. Las rutas de acceso pueden incluir variables de entorno.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Vea también

- [Configuración de una serie de pruebas](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test task (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts) [Tarea de prueba de Visual Studio (Azure Test Plans)]
