---
title: "Preguntas más frecuentes sobre Live Unit Testing | Microsoft Docs"
ms.date: 2017-10-03
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
ms.assetid: 61baf3bb-646f-4c5a-b7c0-a6bdff68f21c
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: 6845c97f906e19ed86b0baec5fa23b6bdca73632
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Preguntas más frecuentes sobre Live Unit Testing

## <a name="live-unit-testing-is-improved-and-enhanced-regularly-how-can-i-find-information-about-the-latest-new-features-and-enhancements"></a>Live Unit Testing se mejora con regularidad. ¿Cómo puedo encontrar información sobre las últimas características y mejoras?

**Respuesta:**

Para obtener información sobre las características nuevas y mejoras que se han realizado en Live Unit Testing a partir de Visual Studio 2017 versión 15.3, vea [What's New in Live Unit Testing](live-unit-testing-whats-new.md) (Novedades en Live Unit Testing).


## <a name="what-test-frameworks-does-live-unit-testing-support-and-what-are-the-minimum-supported-versions"></a>¿Qué marcos de pruebas admite Live Unit Testing y cuáles son las versiones mínimas compatibles?  

**Respuesta:**

Live Unit Testing funciona con los tres marcos de pruebas unitarias conocidos enumerados en la tabla siguiente. La versión mínima admitida de sus adaptadores y marcos también aparece en la tabla. Los marcos de pruebas unitarias están disponibles en NuGet.org.
 
<table> 
<tr>
   <th>Marco de prueba</th>
   <th>Versión mínima del adaptador de Visual Studio</th>
   <th>Versión mínima del marco</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio version 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td> 
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter version 3.5.1</td>  
   <td>NUnit version 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

Si tiene proyectos de prueba basados en versiones anteriores de MSTest que hacen referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` y no quiere usar los paquetes de MSTest NuGet más recientes, actualice a la versión 15.4 de Visual Studio 2017. 

En algunos casos, es posible que tenga que restaurar explícitamente los paquetes NuGet a los que los proyectos de la solución hacen referencia para que Live Unit Testing funcione. Puede hacerlo compilando explícitamente la solución (seleccione **Compilar**, **Recompilar solución** en el menú de Visual Studio de nivel superior) o restaurando los paquetes en la solución (haga doble clic en la solución y seleccione **Restaurar paquetes de NuGet**) antes de habilitar Live Unit Testing. 


## <a name="does-live-unit-testing-work-with-net-core"></a>¿Funciona Live Unit Testing con .NET Core?  

**Respuesta:**

Sí. Live Unit Testing funciona con .NET Core y .NET Framework. Recientemente se ha agregado compatibilidad con .NET Core en la versión 15.3 de Visual Studio 2017. Si quiere obtener compatibilidad de Live Unit Testing para .NET Core, actualice a esta versión de Visual Studio. 

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>¿Por qué Live Unit Testing no funciona cuando lo activo? 

**Respuesta:** 

La **Ventana de salida** (cuando se selecciona la lista desplegable Live Unit Testing) debe indicarle por qué Live Unit Testing no funciona. Live Unit Testing puede que no funcione por uno de los siguientes motivos: 

- Si no se han restaurado los paquetes NuGet a los que los proyectos hacen referencia en la solución, Live Unit Testing no funcionará. Este problema debería resolverse realizando una compilación explícita de la solución o restaurando los paquetes NuGet de la solución antes de activar Live Unit Testing. 

- Si en los proyectos usa pruebas basadas en MSTest, asegúrese de quitar la referencia a `Microsoft.VisualStudio.QualityTools.UnitTestFramework` y agregar referencias a los paquetes NuGet de MSTest más recientes, `MSTest.TestAdapter` (se requiere la versión 1.1.11 como mínimo) y `MSTest.TestFramework` (se requiere la versión 1.1.11 como mínimo). Para más información, consulte la sección "Marcos de pruebas admitidos" del tema [Live Unit Testing con Visual Studio 2017](live-unit-testing.md#supported-test-frameworks).
 
- Al menos un proyecto de la solución debe tener una referencia a NuGet o una referencia directa al marco de prueba xUnit, NUnit o MSTest. Este proyecto también debe hacer referencia a un paquete NuGet del adaptador de prueba de Visual Studio correspondiente. También se puede hacer referencia al adaptador de prueba de Visual Studio a través de un archivo `.runsettings`. El archivo `.runsettings` debe tener una entrada como la siguiente: 

   ```xml
    <RunSettings> 
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration> 
    </RunSettings> 
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>¿Por qué Live Unit Testing muestra una cobertura incorrecta después de actualizar el adaptador de prueba al que se hace referencia en los proyectos de Visual Studio a la versión admitida?

**Respuesta:**

- Si varios proyectos de la solución hacen referencia al paquete del adaptador de prueba de NuGet, todos ellos deben actualizarse a la versión admitida.

- Asegúrese de que el archivo .props de MSBuild importado del paquete del adaptador de prueba también se actualiza correctamente. Compruebe la versión/ruta de la importación del paquete NuGet, que normalmente se encuentra en la parte superior del archivo del proyecto, como la siguiente:

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>¿Puedo personalizar mis compilaciones de Live Unit Testing? 

**Respuesta:**

Si la solución requiere la compilación de pasos personalizados para la instrumentación (Live Unit Testing) que no son necesarios para la compilación no instrumentada "normal", entonces puede agregar código al proyecto o a los archivos .targets que compruebe la propiedad `BuildingForLiveUnitTesting` y realice pasos personalizados anteriores y posteriores a la compilación. También puede optar por quitar ciertos pasos de compilación (como la publicación o generación de paquetes) o por agregar dichos pasos (por ejemplo, copiar requisitos previos) a una compilación de Live Unit Testing basada en esta propiedad de proyecto. Esto no afectará a la compilación normal de ninguna manera, sino solo a las compilaciones de Live Unit Testing. 

Por ejemplo, puede haber un destino que genere paquetes NuGet durante una compilación normal. Probablemente no desee que los paquetes NuGet se generen después de cada edición que realice. Por tanto, puede deshabilitar ese destino en la compilación de Live Unit Testing haciendo algo parecido a lo siguiente:   

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'"> 
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/> 
</Target> 
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>Mensajes de error con &lt;OutputPath&gt; o &lt;OutDir&gt;

**¿Por qué aparece el siguiente error cuando Live Unit Testing intenta compilar mi solución: "...appears to unconditionally set `<OutputPath>` or `<OutDir>`. Live Unit Testing will not execute tests from the output assembly"?** (...parece que establece incondicionalmente... o Live Unit Testing no ejecutará pruebas desde el ensamblado de salida?)

**Respuesta:**

Esto puede ocurrir si el proceso de compilación de la solución invalida incondicionalmente `<OutputPath>` o `<OutDir>` para que no sea un subdirectorio de `<BaseOutputPath>`. En tales casos, Live Unit Testing no funcionará porque también los invalida para asegurarse de que los artefactos de compilación se colocan en una carpeta bajo `<BaseOutputPath>`. Si es necesario invalidar la ubicación donde desea que se coloquen los artefactos de compilación en una compilación normal, invalide `<OutputPath>` basado condicionalmente en `<BaseOutputPath>`. 

Por ejemplo, si la compilación invalida `<OutputPath>` tal como se muestra a continuación: 

```xml 
<Project> 
  <PropertyGroup> 
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath> 
  </PropertyGroup> 
</Project> 
```

reemplácelo por lo siguiente: 

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
  
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>Establecimiento de la ubicación de los artefactos de compilación de Live Unit Testing

**Quiero que los artefactos de una compilación de Live Unit Testing vayan a una ubicación específica y no a la ubicación predeterminada bajo la carpeta `.vs`. ¿Cómo puedo cambiarlo?**
 
**Respuesta:**

Establezca la variable de entorno de usuario `LiveUnitTesting_BuildRoot` en la ruta de acceso donde desea que se coloquen los artefactos de compilación de Live Unit Testing.  

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>¿Cuál es la diferencia entre ejecutar pruebas desde la ventana Explorador de pruebas y ejecutar pruebas en Live Unit Testing? 

**Respuesta:**

Hay varias diferencias: 

- La ejecución o depuración de pruebas desde la ventana Explorador de pruebas ejecuta binarios normales, mientras que Live Unit Testing ejecuta binarios instrumentados. Si desea depurar binarios instrumentados, la incorporación de una llamada de método [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) al método de prueba hace que el depurador se inicie siempre que se ejecute el método (incluso cuando lo ejecuta Live Unit Testing); después, puede asociar y depurar el binario instrumentado. Sin embargo, nuestro deseo es que la instrumentación sea transparente para el usuario en la mayoría de los escenarios y que no tenga que depurar binarios instrumentados. 

- Live Unit Testing no crea un nuevo dominio de aplicación para ejecutar pruebas, sino que estas se ejecutan desde la ventana Explorador de pruebas para crear un nuevo dominio de aplicación. 

- Live Unit Testing ejecuta pruebas en cada ensamblado de prueba secuencialmente, mientras que si se ejecutan varias pruebas desde la ventana Explorador de pruebas y se ha seleccionado el botón **Ejecutar pruebas en paralelo**, se ejecutarán en paralelo. 

- La detección y ejecución de pruebas en Live Unit Testing usa la versión 2 de `TestPlatform`, mientras que la ventana Explorador de pruebas usa la versión 1. No obstante, no debería observar diferencias en la mayoría de los casos.  

- De forma predeterminada, el Explorador de pruebas actualmente ejecuta pruebas en un contenedor uniproceso (STA), mientras que Live Unit Testing ejecuta pruebas en un contenedor multiproceso (MTA). Para ejecutar pruebas de MSTest en STA en Live Unit Testing, decore el método de prueba o la clase contenedora con el atributo `<STATestMethod>` o `<STATestClass>` que puede encontrarse en el paquete NuGet `MSTest.STAExtensions 1.0.3-beta`. Para NUnit y xUnit, decore el método de prueba con el atributo `<RequiresThread(ApartmentState.STA)>` y `<STAFact>`, respectivamente.
 
## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>¿Cómo se pueden excluir pruebas para que no participen en Live Unit Testing?

**Respuesta:**

Consulte la sección "Inclusión y exclusión de proyectos de prueba y métodos de prueba" del tema [Live Unit Testing con Visual Studio 2017](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods) para la configuración específica del usuario. Esto es muy útil cuando desea ejecutar un conjunto específico de pruebas para una sesión de edición determinada o para conservar sus propias preferencias personales.
  
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

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>¿Por qué los encabezados PE de Win32 son diferentes en ensamblados instrumentados generados por Live Unit Testing? 

**Respuesta:**

Este problema se ha corregido y no existe en la versión 15.3 de Visual Studio 2017. Actualice a esta versión de Visual Studio.

En el caso de las versiones anteriores de Visual Studio 2017, hay un error conocido que puede provocar que las compilaciones de Live Unit Testing no inserten los datos de encabezado PE de Win32 siguientes: 

- Versión de archivo (especificada por @System.Reflection.AssemblyFileVersionAttribute en el código). 

- Icono de Win32 (especificado por `/win32icon:` en la línea de comandos). 

- Manifiesto de Win32 (especificado por `/win32manifest:` en la línea de comandos). 

Las pruebas que se basan en estos valores pueden producir errores cuando las ejecuta Live Unit Testing.

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>¿Por qué Live Unit Testing continúa generando mi solución todo el tiempo incluso si no estoy realizando ninguna edición? 

**Respuesta:**

Esto puede suceder si el proceso de compilación de la solución genera código fuente que forma parte de la propia solución y los archivos de destino de compilación no tienen entradas y salidas adecuadas especificadas. Los destinos deben disponer de una lista de entradas y salidas para que MSBuild pueda realizar las comprobaciones actualizadas adecuadas y determinar si es necesaria una nueva compilación. 

Live Unit Testing inicia una compilación siempre que detecta que los archivos de origen han cambiado. Dado que la compilación de la solución genera archivos de origen, Live Unit Testing entrará en un bucle de compilación infinito. No obstante, si las entradas y salidas del destino se comprueban cuando Live Unit Testing inicia la segunda compilación (después de detectar los archivos de origen recién generados desde la compilación anterior), saldrá del bucle porque las comprobaciones de las entradas y salidas indicarán que todo está actualizado.   

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>¿Cómo funciona Live Unit Testing con la característica Carga de solución ligera? 

**Respuesta:**

Live Unit Testing en estos momentos no funciona bien con la característica de carga de solución ligera. Solo funciona después de cargar al menos un proyecto de prueba. Hasta entonces, no funcionará porque Live Unit Testing depende de al menos uno de los proyectos de prueba que hacen referencia al adaptador de prueba (MSTest, xUnit o NUnit) que se está cargando.

Nota: La carga de solución ligera ya no está disponible en la versión 15.5 de Visual Studio 2017 ni en versiones posteriores. En la versión 15.5 de Visual Studio y versiones posteriores, las soluciones de gran tamaño que contiene código administrado se cargan mucho más rápido que antes, incluso sin la carga de solución ligera.
 
## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>¿Por qué Live Unit Testing no captura la cobertura de un proceso nuevo creado por una prueba?
 
**Respuesta:**

Este es un problema conocido y se corregirá en una actualización posterior de Visual Studio 2017. 

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>¿Por qué no sucede nada después de realizar operaciones de inclusión y exclusión de pruebas en el conjunto de Live Test? 

**Respuesta:**

Este problema se ha corregido y no existe en la versión 15.3 de Visual Studio 2017. Actualice a esta versión de Visual Studio. 

Para las versiones anteriores de Visual Studio 2017, es un problema conocido. Para solucionar este problema de forma alternativa, debe realizar una edición en cualquier archivo después de haber incluido o excluido las pruebas.  

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing e iconos del editor 

**¿Por qué no veo ningún icono en el editor aunque Live Unit Testing parece que ejecuta pruebas según los mensajes de la ventana de salida?** 

**Respuesta:**

Esto sucede si, por alguna razón, los ensamblados en los que está trabajando Live Unit Testing no están instrumentados. Por ejemplo, Live Unit Testing no es compatible con proyectos que establecen `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>`. En este caso, el proceso de compilación necesita actualizarse para quitar esta configuración o cambiarla a `true` para que Live Unit Testing funcione.  

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>¿Cómo puedo recopilar registros más detallados para archivar informes de errores? 

**Respuesta:**

Puede hacer varias cosas para recopilar registros más detallados: 

- Vaya a **Herramientas**, **Opciones**, **Live Unit Testing** y cambie la opción de registro a **Detallado**. Esto hace que se muestren registros más detallados en la ventana de salida. 

- Establezca la variable de entorno de usuario `LiveUnitTesting_BuildLog` en el nombre del archivo que desea utilizar para capturar el registro de MSBuild. A continuación, a partir de ese archivo, se pueden recuperar los mensajes de registro de MSBuild detallados procedentes de las compilaciones de Live Unit Testing.

- Establezca la variable de entorno de usuario `LiveUnitTesting_TestPlatformLog` en `1` para capturar el registro de la plataforma de prueba. A continuación, a partir de `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]`, se pueden recuperar los mensajes de registro detallados de la plataforma de prueba procedentes de las ejecuciones de Live Unit Testing.

- Cree una variable de entorno de usuario denominada `VS_UTE_DIAGNOSTICS` y establézcala en 1 (o en cualquier valor) y reinicie Visual Studio. Ahora debería ver una gran cantidad de información de registro en la pestaña **Salida - Pruebas** en Visual Studio. 
  
## <a name="see-also"></a>Vea también

[Live Unit Testing ](live-unit-testing.md)
 
