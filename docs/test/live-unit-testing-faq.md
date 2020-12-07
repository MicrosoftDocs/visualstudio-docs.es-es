---
title: Preguntas más frecuentes sobre Live Unit Testing
description: Revise estas preguntas más frecuentes sobre Live Unit Testing, que incluyen información sobre los marcos de trabajo, la configuración y la personalización admitidos.
ms.custom: SEO-VS-2020
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: bb2c9a4cae25b388d5817b04ff54f6e6443b2f44
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329294"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Preguntas más frecuentes sobre Live Unit Testing

## <a name="supported-frameworks"></a>Marcos de trabajo admitidos

**¿Qué marcos admite Live Unit Testing y cuáles son las versiones mínimas compatibles?**

Live Unit Testing funciona con los tres marcos de pruebas unitarias conocidos que se enumeran en la tabla siguiente. La versión mínima admitida de sus adaptadores y marcos también aparece en la tabla. Los marcos de pruebas unitarias están disponibles en NuGet.org.

|Marco de prueba  |Versión mínima del adaptador de Visual Studio  |Versión mínima del marco  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio version 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter version 3.7.0 |NUnit version 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Si tiene proyectos de prueba basados en versiones anteriores de MSTest que hacen referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` y no quiere usar los paquetes de MSTest NuGet más recientes, actualice a Visual Studio 2019 o Visual Studio 2017.

En algunos casos, es posible que tenga que restaurar explícitamente los paquetes NuGet a los que los proyectos de la solución hacen referencia para que Live Unit Testing funcione. Para restaurar los paquetes, puede compilar explícitamente la solución (seleccione **Compilar** > **Recompilar solución** en el menú de Visual Studio de nivel superior), o puede hacer clic con el botón derecho en la solución y seleccionar **Restaurar paquetes NuGet** antes de habilitar Live Unit Testing.

## <a name="net-core-support"></a>Compatibilidad de .NET Core

**¿Funciona Live Unit Testing con .NET Core?**

Sí. Live Unit Testing funciona con .NET Core y .NET Framework.

## <a name="configuration"></a>Configuración

**¿Por qué Live Unit Testing no funciona cuando lo activo?**

La ventana de salida (cuando se selecciona la lista desplegable Live Unit Testing) debe indicar por qué Live Unit Testing no funciona. Live Unit Testing puede que no funcione por uno de los siguientes motivos:

- Si no se han restaurado los paquetes NuGet a los que los proyectos hacen referencia en la solución, Live Unit Testing no funcionará. Este problema debería resolverse realizando una compilación explícita de la solución o restaurando los paquetes NuGet de la solución antes de activar Live Unit Testing.

- Si en los proyectos usa pruebas basadas en MSTest, asegúrese de quitar la referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` y agregar referencias a los paquetes NuGet de MSTest más recientes, `MSTest.TestAdapter` (se requiere la versión 1.1.11 como mínimo) y `MSTest.TestFramework` (se requiere la versión 1.1.11 como mínimo). Para obtener más información, vea la sección "Marcos de prueba admitidos" del artículo [Live Unit Testing con Visual Studio](live-unit-testing.md#supported-test-frameworks).

- Al menos un proyecto de la solución debe tener una referencia a NuGet o una referencia directa al marco de prueba xUnit, NUnit o MSTest. Este proyecto también debe hacer referencia a un paquete NuGet del adaptador de prueba de Visual Studio correspondiente. También se puede hacer referencia al adaptador de prueba de Visual Studio a través de un archivo *.runsettings*. El archivo *.runsettings* debe tener una entrada como la del ejemplo siguiente:

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>Cobertura incorrecta después de la actualización

**¿Por qué Live Unit Testing muestra una cobertura incorrecta después de actualizar el adaptador de prueba al que se hace referencia en los proyectos de Visual Studio a la versión admitida?**

- Si varios proyectos de la solución hacen referencia al paquete del adaptador de prueba de NuGet, todos ellos deben actualizarse a la versión admitida.

- Asegúrese de que el archivo *.props* de MSBuild importado del paquete del adaptador de prueba también se actualiza correctamente. Compruebe la versión/ruta de la importación del paquete NuGet, que normalmente se encuentra en la parte superior del archivo del proyecto, como la siguiente:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>Personalizar compilaciones

**¿Puedo personalizar mis compilaciones de Live Unit Testing?**

Si la solución requiere la compilación de pasos personalizados para la instrumentación (Live Unit Testing) que no son necesarios para la compilación no instrumentada "normal", entonces puede agregar código al proyecto o a los archivos *.targets* que compruebe la propiedad `BuildingForLiveUnitTesting` y realice pasos personalizados anteriores y posteriores a la compilación. También puede optar por quitar ciertos pasos de compilación (como la publicación o generación de paquetes) o por agregar dichos pasos (por ejemplo, copiar requisitos previos) a una compilación de Live Unit Testing basada en esta propiedad de proyecto. Si personaliza la compilación en función de esta propiedad no se altera la compilación normal de ninguna forma y solo afecta a las compilaciones de Live Unit Testing.

Por ejemplo, puede haber un destino que genere paquetes NuGet durante una compilación normal. Probablemente no desee que los paquetes NuGet se generen después de cada edición que realice. Por tanto, puede deshabilitar ese destino en la compilación de Live Unit Testing haciendo algo parecido a lo siguiente:  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>Mensajes de error con \<OutputPath>, \<OutDir> o \<IntermediateOutputPath>

**¿Por qué aparece el siguiente error cuando Live Unit Testing intenta compilar mi solución: "...appears to unconditionally set `<OutputPath>` or `<OutDir>`. Live Unit Testing will not execute tests from the output assembly"?** (...parece que establece incondicionalmente... o Live Unit Testing no ejecutará pruebas desde el ensamblado de salida?)

Puede obtener este error si el proceso de compilación de la solución tiene una lógica personalizada que especifica dónde se deben generar los archivos binarios. De forma predeterminada, la ubicación de los archivos binarios depende de `<OutputPath>`, `<OutDir>` o `<IntermediateOutputPath>`, así como de `<BaseOutputPath>` o `<BaseIntermediateOutputPath>`.

Live Unit Testing invalida esas variables para asegurarse de que los artefactos de compilación se colocan en una carpeta de artefactos de Live Unit Testing, y se producirá un error si el proceso de compilación también invalida estas variables.

Hay principalmente dos planteamientos para que Live Unit Testing compile correctamente. En el caso de las configuraciones de compilación más sencillas, puede basar las rutas de salida en `<BaseIntermediateOutputPath>`. En el caso de las configuraciones de compilación más complejas, puede basar las rutas de salida en `<LiveUnitTestingBuildRootPath>`.

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>Reemplazo de `<OutputPath>`/`<IntermediateOutputPath>` basado condicionalmente en `<BaseOutputPath>`/ `<BaseIntermediateOutputPath>`.

> [!NOTE]
> Para usar este planteamiento, es necesario que cada proyecto pueda compilarse independientemente de los demás. No tiene un artefacto de referencia de proyecto de otro proyecto durante la compilación. No tiene un proyecto que cargue dinámicamente los ensamblados de otro proyecto durante la ejecución (por ejemplo, llamada a `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`).

Durante la compilación, Live Unit Testing invalida automáticamente las variables `<BaseOutputPath>`/`<BaseIntermediateOutputPath>` para dirigirse a la carpeta de artefactos de Live Unit Testing.

Por ejemplo, si la compilación invalida <OutputPath> tal como se muestra a continuación:

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

reemplácelo por el siguiente XML:

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

Esto garantiza que `<OutputPath>` se encuentra dentro de la carpeta `<BaseOutputPath>`.

No invalide `<OutDir>` directamente en el proceso de compilación; invalide `<OutputPath>` en su lugar para colocar los artefactos de compilación en una ubicación específica.

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>Reemplazo de las propiedades en función de la propiedad `<LiveUnitTestingBuildRootPath>`.

> [!NOTE]
> En este planteamiento, debe tener cuidado con los archivos agregados en la carpeta de artefactos que no se generan durante la compilación. En el ejemplo siguiente se muestra lo que se debe hacer al colocar la carpeta de paquetes en los artefactos. Dado que el contenido de esta carpeta no se genera durante la compilación, **no se debe cambiar** la propiedad de MSBuild.

Durante una compilación de Live Unit Testing, la propiedad `<LiveUnitTestingBuildRootPath>` se establece en la ubicación de la carpeta de artefactos de Live Unit Testing.

Por ejemplo, suponga que el proyecto tiene la estructura que se muestra aquí.

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
Durante la compilación de Live Unit Testing, la propiedad `<LiveUnitTestingBuildRootPath>` se establece en la ruta de acceso completa de `.vs\...\lut\0\b`. Si el proyecto define la propiedad `<ArtifactsRoot>` que se asigna al directorio de la solución, puede actualizar el proyecto de MSBuild de la manera siguiente:

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>Ubicación del artefacto de compilación

**Quiero que los artefactos de una compilación de Live Unit Testing vayan a una ubicación específica y no a la ubicación predeterminada bajo la carpeta *.vs*. ¿Cómo puedo cambiarlo?**

Establezca la variable de entorno de usuario `LiveUnitTesting_BuildRoot` en la ruta de acceso donde desea que se coloquen los artefactos de compilación de Live Unit Testing. 

## <a name="test-explorer-versus-live-unit-testing"></a>Explorador de pruebas o Live Unit Testing

**¿Cuál es la diferencia entre ejecutar pruebas desde la ventana Explorador de pruebas y ejecutar pruebas en Live Unit Testing?**

Hay varias diferencias:

- La ejecución o depuración de pruebas desde la ventana **Explorador de pruebas** ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados. Si desea depurar binarios instrumentados, la incorporación de una llamada de método [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) al método de prueba hace que el depurador se inicie siempre que se ejecute el método (incluso cuando lo ejecuta Live Unit Testing); después, puede asociar y depurar el binario instrumentado. Sin embargo, nuestro deseo es que la instrumentación sea transparente para el usuario en la mayoría de los escenarios y que no tenga que depurar binarios instrumentados.

- Live Unit Testing no crea un dominio de aplicación para ejecutar pruebas, sino que estas se ejecutan desde la ventana **Explorador de pruebas** para crear un dominio de aplicación.

- Live Unit Testing ejecuta pruebas secuencialmente en cada ensamblado de prueba. En el **Explorador de pruebas**, puede optar por ejecutar varias pruebas en paralelo.

- De forma predeterminada, el **Explorador de pruebas** ejecuta pruebas en un contenedor uniproceso (STA), mientras que Live Unit Testing ejecuta pruebas en un contenedor multiproceso (MTA). Para ejecutar pruebas de MSTest en STA en Live Unit Testing, decore el método de prueba o la clase contenedora con el atributo `<STATestMethod>` o `<STATestClass>` que puede encontrarse en el paquete NuGet `MSTest.STAExtensions 1.0.3-beta`. Para NUnit y xUnit, decore el método de prueba con el atributo `<RequiresThread(ApartmentState.STA)>` y `<STAFact>`, respectivamente.

## <a name="exclude-tests"></a>Exclusión de pruebas

**¿Cómo se pueden excluir pruebas para que no participen en Live Unit Testing?**

Vea la sección "Incluir y excluir proyectos de prueba y métodos de prueba" del artículo [Live Unit Testing con Visual Studio](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) para obtener la configuración específica del usuario. La inclusión o exclusión de pruebas es útil cuando se quiere ejecutar un conjunto específico de pruebas para una sesión de edición determinada o para conservar sus propias preferencias personales.

Para la configuración específica de la solución, puede aplicar el atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> mediante programación para excluir los métodos, las propiedades, las clases o las estructuras de la instrumentación que realiza Live Unit Testing. Además, también puede establecer la propiedad `<ExcludeFromCodeCoverage>` en `true` en el archivo de proyecto para excluir todo el proyecto de la instrumentación. Live Unit Testing seguirá ejecutando las pruebas que no se han instrumentado, pero su cobertura no se visualizará.

También puede comprobar si `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` se carga en el dominio de aplicación actual y deshabilitar pruebas en base a ello. Por ejemplo, puede hacer algo como lo siguiente con xUnit:

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Encabezados PE de Win32

**¿Por qué los encabezados PE de Win32 son diferentes en ensamblados instrumentados generados por Live Unit Testing?**

Este problema se ha corregido y no existe en la versión 15.3 y posteriores de Visual Studio 2017.

En el caso de las versiones anteriores de Visual Studio 2017, hay un error conocido que puede provocar que las compilaciones de Live Unit Testing no inserten los datos de encabezado PE de Win32 siguientes:

- Versión de archivo (especificada por @System.Reflection.AssemblyFileVersionAttribute en el código).

- Icono de Win32 (especificado por `/win32icon:` en la línea de comandos).

- Manifiesto de Win32 (especificado por `/win32manifest:` en la línea de comandos).

Las pruebas que se basan en estos valores pueden producir errores cuando las ejecuta Live Unit Testing.

::: moniker-end

## <a name="continuous-builds"></a>Compilaciones continuas

**¿Por qué Live Unit Testing continúa compilando mi solución todo el tiempo incluso si no estoy realizando ninguna edición?**

La solución se puede compilar incluso si no realiza ninguna edición si el proceso de compilación genera código fuente que forma parte de la propia solución y los archivos de destino de compilación no tienen entradas y salidas adecuadas especificadas. Los destinos deben disponer de una lista de entradas y salidas para que MSBuild pueda realizar las comprobaciones actualizadas adecuadas y determinar si es necesaria una nueva compilación.

Live Unit Testing inicia una compilación siempre que detecta que los archivos de origen han cambiado. Dado que la compilación de la solución genera archivos de origen, Live Unit Testing entra en un bucle de compilación infinito. Pero si las entradas y salidas del destino se comprueban cuando Live Unit Testing inicia la segunda compilación (después de detectar los archivos de origen recién generados desde la compilación anterior), sale del bucle de compilación porque las comprobaciones de las entradas y salidas indican que todo está actualizado.

## <a name="editor-icons"></a>Iconos del editor

**¿Por qué no veo ningún icono en el editor aunque Live Unit Testing parece que ejecuta pruebas según los mensajes de la ventana de salida?**

Es posible que no vea los iconos del editor si, por alguna razón, los ensamblados en los que está trabajando Live Unit Testing no están instrumentados. Por ejemplo, Live Unit Testing no es compatible con proyectos que establecen `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. En este caso, el proceso de compilación necesita actualizarse para quitar esta configuración o cambiarla a `true` para que Live Unit Testing funcione. 

## <a name="capture-logs"></a>Captura de registros

**¿Cómo puedo recopilar registros más detallados para archivar informes de errores?**

Puede hacer varias cosas para recopilar registros más detallados:

- Vaya a **Herramientas** > **Opciones** > **Live Unit Testing** y cambie la opción de registro a **Detallado**. El registro detallado hace que se muestren registros más detallados en la ventana de **salida**.

- Establezca la variable de entorno de usuario `LiveUnitTesting_BuildLog` en el nombre del archivo que desea utilizar para capturar el registro de MSBuild. A continuación, a partir de ese archivo, se pueden recuperar los mensajes de registro de MSBuild detallados procedentes de las compilaciones de Live Unit Testing.

- Establezca la variable de entorno de usuario `LiveUnitTesting_TestPlatformLog` en `1` para capturar el registro de la plataforma de prueba. A continuación, a partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`, se pueden recuperar los mensajes de registro detallados de la plataforma de prueba procedentes de las ejecuciones de Live Unit Testing.

- Cree una variable de entorno de usuario denominada `VS_UTE_DIAGNOSTICS` y establézcala en 1 (o en cualquier valor) y reinicie Visual Studio. Ahora debería ver una gran cantidad de información de registro en la pestaña **Salida - Pruebas** en Visual Studio.

## <a name="see-also"></a>Vea también

- [Live Unit Testing ](live-unit-testing.md)
