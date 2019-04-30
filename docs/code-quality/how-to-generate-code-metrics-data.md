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
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823587"
---
# <a name="how-to-generate-code-metrics-data"></a>Procedimiento Generar datos de métricas de código

Puede generar datos de métricas de código de tres maneras:

- Instalando [analizadores de FxCop](#fxcop-analyzers-code-metrics-rules) y habilitar las reglas de métricas (mantenimiento) cuatro del código contiene.

- Si elige la [ **analizar** > **calcular métricas del código** ](#calculate-code-metrics-menu-command) comando de menú dentro de Visual Studio.

- Desde el [línea de comandos](#command-line-code-metrics) para C# y proyectos de Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Reglas de métricas de código de analizadores de FxCop

El [paquete FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) incluye varias métricas del código [analizador](roslyn-analyzers-overview.md) reglas:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Estas reglas están deshabilitadas de forma predeterminada, pero puede habilitarlas desde [ **el Explorador de soluciones** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) o en un [conjunto de reglas](using-rule-sets-to-group-code-analysis-rules.md) archivo. Por ejemplo, para habilitar la regla CA1502 como una advertencia, el archivo .ruleset contendría la siguiente entrada:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuración

Puede configurar los umbrales en el que las reglas de métricas de código en los analizadores de FxCop fire del paquete.

1. Crear un archivo de texto Por ejemplo, puede asignarle el nombre *CodeMetricsConfig.txt*.

2. Agregue los umbrales deseados al archivo de texto en el formato siguiente:

   ```txt
   CA1502: 10
   ```

   En este ejemplo, la regla [CA1502](ca1502-avoid-excessive-complexity.md) está configurado para desencadenar cuando la complejidad ciclomática de un método es mayor que 10.

3. En el **propiedades** ventana de Visual Studio o en el archivo de proyecto, marque la acción de compilación del archivo de configuración como [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Por ejemplo:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calcular el comando de menú de las métricas del código

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
>
> - Actualización a [2019 de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

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

Visual Studio 2015 incluye una herramienta de métricas de código de línea de comandos que también se denomina *Metrics.exe*. Esta versión anterior de la herramienta realizó un análisis binario, es decir, un análisis basado en ensamblados. El nuevo *Metrics.exe* herramienta analiza el código fuente en su lugar. Dado que el nuevo *Metrics.exe* herramienta es métricas del código de línea de comandos, basado en código de origen son diferentes a los generados por el IDE de Visual Studio y las versiones anteriores de los resultados *Metrics.exe*.

La nueva herramienta de métricas de código de línea de comandos calcula las métricas incluso en presencia de errores de código fuente, siempre que se pueden cargar la solución y proyecto.

#### <a name="metric-value-differences"></a>Diferencias de valor de métrica

El `LinesOfCode` métrica es más precisas y confiables en la nueva herramienta de métricas de código de línea de comandos. Es independiente de las diferencias de generación de código y no cambia cuando cambia el conjunto de herramientas o en tiempo de ejecución. La nueva herramienta cuenta reales líneas de código, incluidos los comentarios y las líneas en blanco.

Otras métricas como `CyclomaticComplexity` y `MaintainabilityIndex` utilizar las fórmulas de la mismas que en versiones anteriores de *Metrics.exe*, pero la nueva herramienta cuenta el número de `IOperations` (instrucciones de origen lógico) en lugar de nivel intermedio instrucciones de lenguaje (IL). Los números será ligeramente diferentes a los generados por el IDE de Visual Studio y las versiones anteriores de *Metrics.exe*.

## <a name="see-also"></a>Vea también

- [Utilice la ventana de resultados de las métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
