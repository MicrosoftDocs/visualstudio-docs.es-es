---
title: Generar métricas de código desde la línea de comandos o IDE
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e43273823c3baca77bfa50206c9b2186118cca8
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007363"
---
# <a name="how-to-generate-code-metrics-data"></a>Filtrar Generar datos de métricas de código

Puede generar resultados de métricas de código para una solución completa o uno o varios proyectos. Las métricas del código está disponible dentro del entorno de desarrollo interactivo (IDE) de Visual Studio y, para C# y proyectos de Visual Basic, en la línea de comandos.

Además, puede instalar un [paquete NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) que incluye cuatro métricas del código [analizador](roslyn-analyzers-overview.md) reglas: CA1501, CA1502, CA1505 y CA1506. Estas reglas están deshabilitadas de forma predeterminada, pero puede habilitarlas desde **el Explorador de soluciones** o en un [conjunto de reglas](using-rule-sets-to-group-code-analysis-rules.md) archivo.

## <a name="visual-studio-ide-code-metrics"></a>Métricas de código de Visual Studio IDE

Generar métricas de código para uno o todos los proyectos abiertos en el IDE mediante el **analizar** > **calcular métricas del código** menú.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generar los resultados de las métricas de código para una solución completa

Puede generar resultados de métrica del código para una solución completa en cualquiera de las maneras siguientes:

- En la barra de menús, elija **analizar** > **calcular métricas del código** > **para la solución**.

- En **el Explorador de soluciones**, haga clic en la solución y, a continuación, elija **calcular métricas del código**.

- En el **resultados de métrica del código** ventana, elija el **calcular métricas del código para solución** botón.

Los resultados se generan y **resultados de métrica del código** se muestra la ventana. Para ver los detalles de resultados, expanda el árbol en el **jerarquía** columna.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generar los resultados de las métricas de código para uno o varios proyectos

1. En **el Explorador de soluciones**, seleccione uno o varios proyectos.

1. En la barra de menús, elija **analizar** > **calcular métricas del código** > **para los proyectos seleccionados**.

Los resultados se generan y **resultados de métrica del código** se muestra la ventana. Para ver los detalles de resultados, expanda el árbol en el **jerarquía**.

::: moniker range="vs-2017"

> [!NOTE]
> El **calcular métricas del código** comando no funciona para los proyectos .NET Core y .NET Standard. Para calcular métricas del código para un proyecto .NET Core o .NET Standard, hacer lo siguiente:
>
> - calcular métricas del código desde el [línea de comandos](#command-line-code-metrics) en su lugar
> - actualizar a Visual Studio de 2019

::: moniker-end

## <a name="command-line-code-metrics"></a>Métricas del código de línea de comandos

Puede generar datos de métricas de código desde la línea de comandos para C# y proyectos de Visual Basic para aplicaciones de .NET Framework, .NET Core y .NET Standard. Para ejecutar las métricas del código desde la línea de comandos, instale el [paquete Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) o compilar el [Metrics.exe](#metricsexe) ejecutable usted mismo.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Paquete de Microsoft.CodeAnalysis.Metrics NuGet

La manera más fácil para generar datos de métricas de código desde la línea de comandos que se está instalando el [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) paquete NuGet. Después de instalar el paquete, ejecute `msbuild /t:Metrics` desde el directorio que contiene el archivo de proyecto. Por ejemplo:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Puede invalidar el nombre de archivo de salida mediante la especificación `/p:MetricsOutputFile=<filename>`. También puede obtener [estilo heredado](#previous-versions) mediante la especificación de los datos de métricas de código `/p:LEGACY_CODE_METRICS_MODE=true`. Por ejemplo:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Salida de las métricas de código

La salida XML generada tiene el formato siguiente:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrics.exe

Si no desea instalar el paquete de NuGet, puede generar y usar el *Metrics.exe* ejecutable directamente. Para generar el *Metrics.exe* ejecutable:

1. Clone el [dotnet/roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) repositorio.
2. Abra el símbolo del sistema para desarrolladores para Visual Studio como administrador.
3. Desde la raíz de la **analizadores de roslyn** repo, ejecute el siguiente comando: `Restore.cmd`
4. Cambie el directorio a *src\Tools*.
5. Ejecute el siguiente comando para compilar el **Metrics.csproj** proyecto:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un archivo ejecutable denominado *Metrics.exe* se genera en el *artifacts\bin* directorio bajo la raíz del repositorio.

#### <a name="metricsexe-usage"></a>Uso de Metrics.exe

Para ejecutar *Metrics.exe*, proporcionar un proyecto o solución y una salida XML de archivo como argumentos. Por ejemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modo heredado

Puede optar por crear *Metrics.exe* en *modo heredado*. La versión en modo heredado de la herramienta genera los valores de métricas que están más próximos a qué [versiones anteriores de la herramienta genera](#previous-versions). Además, en el modo heredado *Metrics.exe* genera métricas de código para el mismo conjunto de método que las versiones anteriores de las métricas de herramienta genera código para los tipos. Por ejemplo, no genera datos de métricas de código para los inicializadores de campo y propiedad. Modo heredado es útil para hacia atrás compatibilidad o si tiene código de comprobación de las validaciones basadas en métricas de código números. El comando para compilar *Metrics.exe* en modo heredado es:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obtener más información, consulte [Habilitar generación de las métricas del código en modo heredado](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Versiones anteriores

Las versiones anteriores de Visual Studio, incluidos Visual Studio 2015, incluyen una herramienta de métricas de código de línea de comandos que también se denomina *Metrics.exe*. Esta versión anterior de la herramienta realizó un análisis binario, es decir, un análisis basado en ensamblados. La nueva herramienta analiza el código fuente en su lugar. Dado que la nueva herramienta de métricas de código de línea de comandos es el origen basado en código, los resultados son diferentes a lo que generan las versiones anteriores de *Metrics.exe* y en el IDE de Visual Studio 2017.

La nueva herramienta de métricas de código de línea de comandos calcula las métricas incluso en presencia de errores de código fuente, siempre que se pueden cargar la solución y proyecto.

#### <a name="metric-value-differences"></a>Diferencias de valor de métrica

El `LinesOfCode` métrica es más precisas y confiables en la nueva herramienta de métricas de código de línea de comandos. Es independiente de las diferencias de generación de código y no cambia cuando cambia el conjunto de herramientas o en tiempo de ejecución. La nueva herramienta cuenta reales líneas de código, incluidos los comentarios y las líneas en blanco.

Otras métricas como `CyclomaticComplexity` y `MaintainabilityIndex` utilizar las fórmulas de la mismas que en versiones anteriores de *Metrics.exe*, pero la nueva herramienta cuenta el número de `IOperations` (instrucciones de origen lógico) en lugar de nivel intermedio instrucciones de lenguaje (IL). Los números será ligeramente diferentes de versiones anteriores de *Metrics.exe* y de los resultados de las métricas del código de IDE de Visual Studio 2017.

## <a name="see-also"></a>Vea también

- [Utilice la ventana de resultados de las métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
