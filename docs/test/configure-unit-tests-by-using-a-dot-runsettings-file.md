---
title: Configuración de pruebas unitarias con un archivo .runsettings
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f638d60b7bd4416bb7a19cc960cac1159c755ab3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86972301"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configuración de pruebas unitarias con un archivo *.runsettings*

En Visual Studio las pruebas unitarias se pueden configurar mediante un archivo *.runsettings*. Por ejemplo, se puede cambiar la versión de .NET en la que se ejecutan las pruebas, el directorio de los resultados de las pruebas o los datos recopilados durante una serie de pruebas. Un uso común de un archivo *.runsettings* es para personalizar el [análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

Los archivos de parámetros de ejecución se pueden usar para configurar pruebas que se ejecuten desde la [línea de comandos](vstest-console-options.md), el IDE o un [flujo de trabajo de compilación](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) mediante Azure Test Plans o Team Foundation Server (TFS).

Los parámetros de ejecución son opcionales. Si no es necesaria una configuración especial, no se necesita un archivo *.runsettings*.

## <a name="create-a-run-settings-file-and-customize-it"></a>Creación y personalización de un archivo de parámetros de ejecución

1. Agregue un archivo de parámetros de ejecución a la solución. En el **Explorador de soluciones**, en el menú contextual de la solución, seleccione **Agregar** > **Nuevo elemento** y seleccione **Archivo XML**. Guarde el archivo con un nombre como *test.runsettings*.

   > [!TIP]
   > El nombre de archivo no importa, siempre que use la extensión *.runsettings*.

2. Agregue el contenido que se muestra en el [archivo de ejemplo *.runsettings](#example-runsettings-file) y, después, personalícelo de acuerdo con sus necesidades tal como se describe en las secciones siguientes.

3. Especifique el archivo *.runsettings que quiera mediante uno de los métodos siguientes:

   - [IDE de Visual Studio](#specify-a-run-settings-file-in-the-ide)
   - [Línea de comandos](#specify-a-run-settings-file-from-the-command-line)
   - [Cree el flujo de trabajo](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) mediante Azure Test Plans o Team Foundation Server (TFS).

4. Ejecute las pruebas unitarias para usar los parámetros de ejecución personalizados.

::: moniker range="vs-2017"

Si quiere desactivar y activar los parámetros personalizados en el IDE, anule la selección del archivo o selecciónelo en el menú **Prueba** > **Configuración de pruebas**.

![Menú de configuración de pruebas con archivo de configuración personalizado en Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Si quiere desactivar y activar los parámetros personalizados en el IDE, anule la selección del archivo o selecciónelo en el menú **Prueba**.

::: moniker-end

> [!TIP]
> Puede crear más de un archivo *.runsettings* en la solución y seleccionar uno como archivo de configuración de pruebas activo según sea necesario.

## <a name="specify-a-run-settings-file-in-the-ide"></a>Especificar un archivo de parámetros de ejecución en el IDE

Los métodos disponibles dependerán de la versión de Visual Studio.

::: moniker range="vs-2017"
Para especificar un archivo de parámetros de ejecución en el IDE, seleccione **Prueba** > **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas** y, luego, el archivo *.runsettings*.

![Selección del menú del archivo de configuración de pruebas en Visual Studio 2017](media/select-test-settings-file.png)

El archivo aparece en el menú Configuración de pruebas, y puede seleccionarlo o anular la selección. Mientras está seleccionado, el archivo de parámetros de ejecución se aplica siempre que seleccione **Analizar cobertura de código**.
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019, versión 16.4 y posteriores

Hay tres formas de especificar un archivo de parámetros de ejecución en la versión 16.4 de Visual Studio 2019 y posteriores.

- [Detección automática de los parámetros de ejecución](#autodetect-the-run-settings-file)
- [Establecimiento manual de los parámetros de ejecución](#manually-select-the-run-settings-file)
- [Establecimiento de una propiedad de compilación](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>Detección automática del archivo de parámetros de ejecución

Para detectar automáticamente el archivo de parámetros de ejecución, colóquelo en la raíz de la solución.

Si está habilitada la detección automática de archivos de parámetros de ejecución, la configuración de este archivo se aplica a todas las pruebas ejecutadas. Puede activar la detección automática de los archivos runsettings siguiendo uno de estos dos métodos:
  
- Seleccione **Herramientas** > **Opciones** > **Probar** > **Detectar archivos runsettings automáticamente**.

   ![Opción Auto Detect runsettings File (Detectar archivos runsettings automáticamente) en Visual Studio 2019](media/vs-2019/auto-detect-runsettings-tools-window.png)
      
- Seleccione **Probar** > **Configurar parámetros de ejecución** > **Detectar archivos runsettings automáticamente**.
    
   ![Menú Auto Detect runsettings Files (Detectar archivos runsettings automáticamente) en Visual Studio 2019](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>Selección manual del archivo de parámetros de ejecución

En el IDE, seleccione **Probar** > **Configurar parámetros de ejecución** > **Seleccionar archivo runsettings en toda la solución** y, después, seleccione el archivo *.runsettings*.

   - Este archivo reemplaza *.runsettings* en la raíz de la solución, si hay alguno, y se aplica a todas las pruebas ejecutadas.  
   - Esta selección del archivo solo se conserva localmente.

![Menú Seleccionar archivo runsettings en toda la solución de prueba en Visual Studio 2019](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>Establecimiento de una propiedad de compilación

Agregue una propiedad de compilación a un proyecto mediante el archivo de proyecto o un archivo Directory.Build.props. El archivo de parámetros de ejecución de un proyecto se especifica mediante la propiedad **RunSettingsFilePath**.

- Los parámetros de ejecución de nivel de proyecto se admiten actualmente en proyectos C#, VB, C++ y F#.
- Un archivo especificado para un proyecto invalida cualquier otro archivo de parámetros de ejecución especificado en la solución.
- [Estas propiedades de MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-reserved-and-well-known-properties?view=vs-2019) se pueden usar para especificar la ruta de acceso al archivo "runsettings". 

Ejemplo de cómo especificar un archivo *.runsettings* para un proyecto:
    
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019, versión 16.3 y anteriores

Para especificar un archivo de parámetros de ejecución en el IDE, seleccione **Prueba** > **Seleccionar archivo de configuración**. Busque y seleccione el archivo *.runsettings*.

![Selección del menú del archivo de configuración de pruebas en Visual Studio 2019](media/vs-2019/select-settings-file.png)

El archivo aparece en el menú Prueba, y puede seleccionarlo o anular su selección. Mientras está seleccionado, el archivo de parámetros de ejecución se aplica siempre que seleccione **Analizar cobertura de código**.
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>Especificación de un archivo de parámetros de ejecución desde la línea de comandos

Para ejecutar pruebas desde la línea de comandos, utilice *vstest.console.exe* y especifique el archivo de configuración mediante el parámetro **/Settings**.

1. Abra el [Símbolo del sistema para desarrolladores](/dotnet/framework/tools/developer-command-prompt-for-vs) de Visual Studio.

2. Escriba un comando similar a:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   o

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Para obtener más información, vea [Opciones de la línea de comandos para VSTest.Console.exe](vstest-console-options.md).

## <a name="the-runsettings-file"></a>Archivo *.runsettings

El archivo *.runsettings es un archivo XML que contiene distintos elementos de configuración dentro del elemento **RunSettings**. En las secciones siguientes se detallan los distintos elementos. Para obtener un ejemplo completo, vea [Archivo de ejemplo *.runsettings](#example-runsettings-file).

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

Cada elemento de configuración es opcional porque tiene su valor predeterminado.

## <a name="runconfiguration-element"></a>Elemento RunConfiguration

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
|**MaxCpuCount**|1|Este valor controla el grado de ejecución de pruebas paralelas cuando se ejecutan pruebas unitarias, mediante los núcleos disponibles en la máquina. El motor de ejecución de pruebas se inicia como un proceso distinto en cada núcleo disponible y proporciona a cada núcleo un contenedor con las pruebas que se van a ejecutar. Un contenedor puede ser un ensamblado, un archivo DLL o un artefacto relevante. El contenedor de pruebas es la unidad de programación. En cada contenedor, las pruebas se ejecutan según el marco de pruebas. Si hay muchos contenedores, a medida que los procesos finalizan la ejecución de las pruebas en un contenedor, se les proporciona el siguiente contenedor disponible.<br /><br />El valor de MaxCpuCount puede ser:<br /><br />n, donde 1 <= n <= número de núcleos: se inician hasta n procesos<br /><br />n, donde n = cualquier otro valor: el número de procesos iniciados puede ser como máximo el número de núcleos disponibles. Por ejemplo, establezca n = 0 para permitir que la plataforma decida automáticamente el número óptimo de procesos que se van a iniciar en función del entorno.|
|**ResultsDirectory**||Directorio en el que se colocan los resultados de las pruebas. La ruta de acceso es relativa al directorio que contiene el archivo .runsettings.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` para orígenes de .NET Core, `FrameworkUap10` para orígenes basados en UWP, `Framework45` para .NET Framework 4.5 y versiones superiores, `Framework40` para .NET Framework 4.0 y `Framework35` para .NET Framework 3.5.<br /><br />Este valor especifica qué versión del marco de pruebas unitarias se usa para detectar y ejecutar las pruebas. Puede ser diferente de la versión de la plataforma .NET que especifique en las propiedades de compilación del proyecto de prueba unitaria.<br /><br />Si omite el elemento `TargetFrameworkVersion` del archivo *.runsettings*, la plataforma determinará de forma automática la versión de Framework en función de los archivos binarios compilados.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|False|false, true|
|**TestAdaptersPaths**||Una o varias rutas de acceso al directorio donde se encuentran los TestAdapters|
|**TestSessionTimeout**||Permite a los usuarios terminar una sesión de prueba cuando esta supera un tiempo de espera especificado. La configuración de un tiempo de espera garantiza que los recursos se utilicen de manera conveniente y que las sesiones de prueba se limiten a un tiempo establecido. Esta opción está disponible en **Visual Studio 2017, versión 15.5** y posteriores.|
|**DotnetHostPath**||Especifique una ruta de acceso personalizada al host dotnet que se usa para ejecutar testhost. Esto resulta útil al compilar un dotnet propio, por ejemplo, al compilar el repositorio dotnet/runtime. Si se especifica esta opción, se omitirá la búsqueda de testhost.exe y siempre se usará testhost.dll. 

## <a name="datacollectors-element-diagnostic-data-adapters"></a>Elemento DataCollectors (adaptadores de datos de diagnóstico)

El elemento **DataCollectors** especifica la configuración de los adaptadores de datos de diagnóstico. Los adaptadores de datos de diagnóstico recopilan información adicional sobre el entorno y la aplicación en pruebas. Cada adaptador tiene una configuración predeterminada, por lo que solo tiene que proporcionar valores si no quiere usar los predeterminados.

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>Recopilador de datos CodeCoverage

El recopilador de datos de cobertura de código crea un registro de las partes del código de aplicación que se han empleado en las pruebas. Para obtener información detallada sobre la personalización de los valores de cobertura de código, vea [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
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
  </CodeCoverage>
</Configuration>
```

### <a name="videorecorder-data-collector"></a>Recopilador de datos VideoRecorder

El recopilador de datos de vídeo captura una grabación de pantalla cuando se ejecutan las pruebas. Esta grabación es útil para solucionar problemas de pruebas de interfaz de usuario. El recopilador de datos de vídeo está disponible en **Visual Studio 2017, versión 15.5** y posteriores. Para obtener un ejemplo de la configuración de este recopilador de datos, vea [Archivo de ejemplo *.runsettings](#example-runsettings-file).

Para personalizar cualquier otro tipo de adaptador de datos de diagnóstico, use un [archivo de configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="blame-data-collector"></a>Recopilador de datos de Blame

Esta opción puede ayudarle a aislar una prueba problemática que hace que el host de prueba se bloquee. Al ejecutar el recopilador, se crea un archivo de salida (*Sequence.xml*) en *TestResults*, donde se captura el orden de ejecución de la prueba antes del bloqueo. 

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

Los parámetros de la serie de pruebas proporcionan una manera de definir las variables y los valores que están disponibles para las pruebas en tiempo de ejecución. Acceda a los parámetros mediante la propiedad <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> de MSTest (o [TestContext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html) de NUnit):

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

Para usar parámetros de serie de pruebas, agregue una propiedad <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> pública a la clase de prueba.

## <a name="loggerrunsettings-element"></a>Elemento LoggerRunSettings

En la sección `LoggerRunSettings` se definen uno o varios registradores para la ejecución de pruebas. Los registradores más comunes son la consola, el archivo de resultados de pruebas de Visual Studio (TRX) y HTML.

```xml
<LoggerRunSettings>
    <Loggers>        
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>Elemento MSTest

Estos valores son específicos del adaptador de pruebas que ejecuta métodos de prueba con el atributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> .

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

|Configuración|Default|Valores|
|-|-|-|
|**ForcedLegacyMode**|False|En Visual Studio 2012, el adaptador MSTest se optimizó para que fuera más rápido y escalable. Es posible que parte del comportamiento, como el orden en que se ejecutan las pruebas, no sea exactamente igual que en ediciones anteriores de Visual Studio. Establezca este valor en **true** para utilizar el adaptador de pruebas más antiguo.<br /><br />Por ejemplo, es posible usar este valor si tiene un archivo *app.config* especificado para una prueba unitaria.<br /><br />Se recomienda que considere la refactorización de las pruebas para poder usar el adaptador más reciente.|
|**IgnoreTestImpact**|False|La característica de impacto de pruebas asigna prioridades a las pruebas afectadas por cambios recientes, cuando se ejecuta en MSTest o desde Microsoft Test Manager (en desuso en Visual Studio 2017). Esta configuración desactiva la característica. Para obtener más información, vea [¿Qué pruebas se deben ejecutar desde una compilación anterior?](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Puede especificar un archivo de configuración de pruebas para usarlo con el adaptador MSTest aquí. También puede especificarlo [en el menú Configuración](#specify-a-run-settings-file-in-the-ide).<br /><br />Si especifica este valor, también debe establecer **ForcedlegacyMode** en **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|False|Una vez completada una serie de pruebas, se cierra MSTest. Cualquier proceso que se inicie como parte de la prueba también se elimina. Si quiere mantener activo el ejecutor de pruebas, establezca este valor en **true**. Por ejemplo, podría usar esta configuración para mantener el explorador en ejecución entre pruebas de IU codificadas.|
|**DeploymentEnabled**|true|Si el valor se establece en **false**, los elementos de implementación especificados en el método de prueba no se copian al directorio de implementación.|
|**CaptureTraceOutput**|true|Puede escribir en el seguimiento de depuración desde su método de prueba mediante <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Para conservar el directorio de implementación después de una serie de pruebas, establezca este valor en **false**.|
|**MapInconclusiveToFailed**|False|Si una prueba finaliza un estado no concluyente, se le asigna el estado Omitido en el **Explorador de pruebas**. Si quiere que las pruebas no concluyentes se muestren como Error, establezca el valor en **true**.|
|**InProcMode**|False|Si quiere que las pruebas se ejecuten en el mismo proceso que el adaptador MSTest, establezca este valor en **true**. Este valor proporciona una pequeña mejora del rendimiento. Pero si una prueba finaliza con una excepción, el resto de pruebas no se ejecutarán.|
|**AssemblyResolution**|False|Puede especificar rutas de acceso a ensamblados adicionales cuando busque y ejecute pruebas unitarias. Por ejemplo, puede utilizar estas rutas de acceso para los ensamblados de dependencias que no estén en el mismo directorio que el ensamblado de pruebas. Para especificar una ruta de acceso, use un elemento **Directory Path**. Las rutas de acceso pueden incluir variables de entorno.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>Archivo de ejemplo *.runsettings*

El siguiente XML muestra el contenido de un archivo *.runsettings* típico. Copie el código y edítelo para satisfacer sus necesidades.

Cada elemento del archivo es opcional, porque cada valor tiene un valor predeterminado.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
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
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>
  
  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>      
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

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

## <a name="specify-environment-variables-in-the-runsettings-file"></a>Especificación de variables de entorno en el archivo *.runsettings*

Las variables de entorno se pueden establecer en el archivo *.runsettings*, que puede interactuar directamente con el host de prueba. Especificar variables de entorno en el archivo *.runsettings* es necesario para admitir proyectos no triviales que requieren configurar variables de entorno como, por ejemplo, *DOTNET_ROOT*. Estas variables se establecen al generar el proceso del host de prueba, y están disponibles en el host.

### <a name="example"></a>Ejemplo

El siguiente código es un archivo *.runsettings* de ejemplo que pasa variables de entorno:

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

El nodo **RunConfiguration** debe contener un nodo **EnvironmentVariables**. Una variable de entorno se puede especificar como un nombre de elemento y su valor.

> [!NOTE]
> Dado que estas variables de entorno siempre deben estar establecidas cuando el host de prueba se inicia, las pruebas siempre deben ejecutarse en un proceso independiente. Para ello, se establecerá la marca */InIsolation* cuando haya variables de entorno, para que el host de prueba siempre se invoque.

## <a name="see-also"></a>Vea también

- [Configuración de una serie de pruebas](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md)
- [Visual Studio test task (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts) [Tarea de prueba de Visual Studio (Azure Test Plans)]

