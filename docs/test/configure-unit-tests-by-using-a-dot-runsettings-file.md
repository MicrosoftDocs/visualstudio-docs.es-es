---
title: "Configuración de pruebas unitarias con un archivo *.runsettings* | Microsoft Docs"
ms.date: 02/28/2018
ms.technology: vs-devops-test
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f10870096697341081904c4dac9540d72823e52f
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Configuración de pruebas unitarias con un archivo *.runsettings*

En Visual Studio las pruebas unitarias se pueden configurar mediante un archivo *.runsettings*. Por ejemplo, se puede cambiar la versión de .NET Framework en la que se ejecutan las pruebas, el directorio de los resultados de las pruebas o los datos recopilados durante una serie de pruebas.

> [!NOTE]
> El nombre de archivo no importa, siempre que use la extensión ".runsettings".

Si no es necesaria una configuración especial, no se necesita un archivo *.runsettings*. El uso más común de un archivo *.runsettings* es para personalizar el [análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

## <a name="customize-tests"></a>Personalización de pruebas

1. Agregue un archivo XML a la solución de Visual Studio y cámbiele el nombre para que sea *test.runsettings*.

1. Reemplace el contenido del archivo por el XML del ejemplo que hay a continuación y personalícelo como sea necesario.

1. En el menú **Prueba**, elija **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas**.

Puede crear más de un archivo *.runsettings* en la solución y habilitarlo o deshabilitarlo en momentos diferentes en el menú **Configuración de pruebas**.

![Habilitar un archivo de parámetros de ejecución](../test/media/runsettings-1.png)

## <a name="example-runsettings-file"></a>Archivo de ejemplo *.runsettings*

A continuación se muestra un archivo *.runsettings* típico. Cada elemento del archivo es opcional, porque cada valor tiene una configuración predeterminada.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
  
     <!--TestSessionTimeout is only available with Visual Studio 2017 version 15.5 and higher -->
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

      <!--Video data collector is only available with Visual Studio 2017 version 15.5 and higher -->
      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
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
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

El archivo *.runsettings* también se usa para configurar el [análisis de cobertura de código](../test/customizing-code-coverage-analysis.md).

En el resto de este artículo se describe el contenido del archivo.

## <a name="edit-your-runsettings-file"></a>Edición del archivo *.runsettings*

En las secciones siguientes se detallan los elementos de un archivo *.runsettings*.

### <a name="test-run-configuration"></a>Configuración de serie de pruebas

|Nodo|Default|Valores|
|----------|-------------|------------|
|`ResultsDirectory`||Directorio en el que se colocan los resultados de las pruebas.|
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Este valor especifica qué versión del marco de pruebas unitarias se usa para detectar y ejecutar las pruebas. Puede ser diferente de la versión de la plataforma .NET que especifique en las propiedades de compilación del proyecto de prueba unitaria.|
|`TargetPlatform`|x86|x86, x64|
|`TreatTestAdapterErrorsAsWarnings`|False|false, true|
|`TestAdaptersPaths`||Una o varias rutas de acceso al directorio donde se encuentran los TestAdapters|
|`MaxCpuCount`|1|Este valor controla el grado de ejecución de pruebas paralelas cuando se ejecutan pruebas unitarias, mediante los núcleos disponibles en el equipo. El motor de ejecución de pruebas se inicia como un proceso distinto en cada núcleo disponible y proporciona a cada núcleo un contenedor con las pruebas que se van a ejecutar. Un contenedor puede ser un ensamblado, un archivo DLL o un artefacto relevante. El contenedor de pruebas es la unidad de programación. En cada contenedor, las pruebas se ejecutan según el marco de pruebas. Si hay muchos contenedores, a medida que los procesos finalizan la ejecución de las pruebas en un contenedor, se les proporciona el siguiente contenedor disponible.<br /><br /> El valor de MaxCpuCount puede ser:<br /><br /> n, donde 1 <= n <= número de núcleos: se iniciarán hasta n procesos<br /><br /> n, donde n = cualquier otro valor: el número de procesos que se iniciarán será como máximo el número de núcleos disponibles en la máquina|
|`TestSessionTimeout`||Permite a los usuarios terminar una sesión de prueba cuando esta supera un tiempo de espera especificado. La configuración de un tiempo de espera garantiza que los recursos se utilicen de manera conveniente y que las sesiones de prueba se limiten a un tiempo establecido. Esta opción está disponible en **Visual Studio 2017, versión 15.5** y posteriores.

### <a name="diagnostic-data-adapters-data-collectors"></a>Adaptadores de datos de diagnóstico (recopiladores de datos)

El elemento `DataCollectors` especifica la configuración de los adaptadores de datos de diagnóstico. Los adaptadores de datos de diagnóstico recopilan información adicional sobre el entorno y la aplicación en pruebas. Cada adaptador tiene una configuración predeterminada, por lo que solo tiene que proporcionar valores si no quiere usar los predeterminados.

#### <a name="code-coverage-adapter"></a>Adaptador de cobertura de código

El recopilador de datos de cobertura de código crea un registro de las partes del código de aplicación que se han empleado en las pruebas. Para obtener más información sobre la personalización de los valores de cobertura de código, vea [Personalizar el análisis de la cobertura de código](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Recopilador de datos de vídeo

El recopilador de datos de vídeo captura una grabación de pantalla cuando se ejecutan las pruebas. Esta grabación es útil para solucionar problemas de pruebas de interfaz de usuario. El recopilador de datos de vídeo está disponible en la **Visual Studio 2017, versión 15.5** y posteriores.

Para personalizar cualquier otro tipo de adaptador de datos de diagnóstico, debe usar un archivo de configuración de pruebas. Para obtener más información, consulte [Especificar la configuración de prueba para las pruebas en Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests).

### <a name="testrunparameters"></a>TestRunParameters

TestRunParameters proporciona una manera de definir las variables y los valores que están disponibles para las pruebas en tiempo de ejecución. Se puede tener acceso a estas variables mediante el objeto [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx).

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
```

Para usar TestContext, agregue un campo [TestContext](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testcontext(v=vs.140).aspx) privado y una propiedad `TestContext` pública a la clase de prueba.

### <a name="mstest-run-settings"></a>Parámetros de ejecución de MSTest

Estos valores son específicos del adaptador de pruebas que ejecuta métodos de prueba con el atributo `[TestMethod]` .

|Configuración|Default|Valores|
|-------------------|-------------|------------|
|ForcedLegacyMode|False|En Visual Studio 2012, el adaptador MSTest se optimizó para que fuera más rápido y escalable. Es posible que parte del comportamiento, como el orden en que se ejecutan las pruebas, no sea exactamente igual que en ediciones anteriores de Visual Studio. Establezca este valor en `true` para utilizar el adaptador de pruebas más antiguo.<br /><br /> Por ejemplo, es posible usar este valor si tiene un archivo *app.config* especificado para una prueba unitaria.<br /><br /> Se recomienda que considere la refactorización de las pruebas para poder usar el adaptador más reciente.|
|IgnoreTestImpact|False|La característica de impacto de pruebas asigna prioridades a las pruebas afectadas por cambios recientes, cuando se ejecuta en MSTest o desde Microsoft Test Manager. Esta configuración desactiva la característica. Para obtener más información, consulte [Cómo: Recopilar datos para comprobar qué pruebas se deben ejecutar después de realizar cambios en el código](http://msdn.microsoft.com/Library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|
|SettingsFile||Puede especificar un archivo de configuración de pruebas para usarlo con el adaptador MSTest aquí. También puede especificar un archivo de configuración de pruebas en el menú **Prueba**, **Configuración de pruebas**, **Seleccionar archivo de configuración de pruebas**.<br /><br /> Si especifica este valor, también debe establecer **ForcedlegacyMode** en **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|False|Una vez completada una serie de pruebas, se cierra MSTest. Cualquier proceso que se inicie como parte de la prueba también se elimina. Si desea mantener activo el ejecutor de pruebas, establezca esta configuración en true.<br /><br /> Por ejemplo, podría usar esta configuración para mantener el explorador en ejecución entre pruebas de IU codificadas.|
|DeploymentEnabled|true|Si el valor se establece en false, los elementos de implementación especificados en el método de prueba no se copian al directorio de implementación.|
|CaptureTraceOutput|true|Puede escribir en el seguimiento de depuración desde su método de prueba mediante Trace.WriteLine. Con esta configuración, puede desactivar estos seguimientos de depuración.|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Puede conservar el directorio de implementación después de una serie de pruebas estableciendo este valor en false.|
|MapInconclusiveToFailed|False|Si una prueba devuelve un estado no concluyente, se le asigna normalmente el estado Omitido en el Explorador de pruebas. Si quiere que las pruebas no concluyentes se muestren como Error, use esta configuración.|
|InProcMode|False|Si desea que las pruebas se ejecuten en el mismo proceso que el adaptador MSTest, establezca este valor en true. Este valor proporciona una pequeña mejora del rendimiento. Pero si una prueba finaliza con una excepción, el resto de pruebas no podrán continuar.|
|AssemblyResolution|False|Puede especificar rutas de acceso a ensamblados adicionales cuando busque y ejecute pruebas unitarias. Por ejemplo, puede utilizar estas rutas de acceso para los ensamblados de dependencias que no residan en el mismo directorio que el ensamblado de pruebas. Para especificar una ruta de acceso, use un elemento "Directory Path". Las rutas de acceso pueden contener variables de entorno.<br /><br /> `<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>Vea también

[Personalizar el análisis de cobertura de código](../test/customizing-code-coverage-analysis.md)
