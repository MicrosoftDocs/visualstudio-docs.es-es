---
title: Generar métricas de código desde el IDE o la línea de comandos
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649312"
---
# <a name="how-to-generate-code-metrics-data"></a>Cómo: Generar datos de métricas de código

Puede generar datos de métricas de código de tres maneras:

- Mediante la instalación de [analizadores FxCop](#fxcop-analyzers-code-metrics-rules) y la habilitación de las cuatro reglas de métricas de código (mantenimiento) que contiene.

- Al elegir el comando de menú [ **Analizar** > métricas](#calculate-code-metrics-menu-command) de código dentro de Visual Studio.

- Desde la línea de [comandos](#command-line-code-metrics) para los proyectos de Visual Basic y de C.

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop analiza las reglas de métricas de código

El [paquete NuGet de FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) incluye varias reglas del [analizador](roslyn-analyzers-overview.md) de métricas de código:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Estas reglas están deshabilitadas de forma predeterminada, pero puede habilitarlas desde el [**Explorador**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) de soluciones o en un archivo de conjunto de [reglas.](using-rule-sets-to-group-code-analysis-rules.md) Por ejemplo, para habilitar la regla CA1502 como advertencia, el archivo .ruleset contendría la siguiente entrada:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Configuración

Puede configurar los umbrales en los que se desencadenan las reglas de métricas de código en el paquete de analizadores FxCop.

1. Crear un archivo de texto Por ejemplo, puede llamarlo *CodeMetricsConfig.txt*.

2. Agregue los umbrales deseados al archivo de texto en el siguiente formato:

   ```txt
   CA1502: 10
   ```

   En este ejemplo, la regla [CA1502](ca1502.md) se configura para activarse cuando la complejidad ciclomática de un método es mayor que 10.

3. En la ventana **Propiedades** de Visual Studio o en el archivo de proyecto, marque la acción de compilación del archivo de configuración como [**AdditionalFiles**](../ide/build-actions.md#build-action-values). Por ejemplo:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Calcular el comando de menú Métricas de código

Genere métricas de código para uno o todos los proyectos abiertos en el IDE mediante el menú **Analizar métricas** > de**código de cálculo.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Generar resultados de métricas de código para una solución completa

Puede generar resultados de métricas de código para una solución completa de cualquiera de las siguientes maneras:

- En la barra de menús, elija **Analizar métricas** > **Calculate Code Metrics** > de código de cálculo**para la solución**.

- En **el Explorador**de soluciones , haga clic con el botón secundario en la solución y, a continuación, elija Calcular **métricas**de código .

- En la ventana Resultados de **métricas** de código, elija el botón Calcular métricas de **código para solución.**

Se generan los resultados y se muestra la ventana Resultados de **métricas** de código. Para ver los detalles de los resultados, expanda el árbol en la columna **Jerarquía.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Generar resultados de métricas de código para uno o más proyectos

1. En **el Explorador**de soluciones , seleccione uno o varios proyectos.

1. En la barra de menús, elija **Analizar métricas** > **Calculate Code Metrics** > de código de cálculo**para proyectos seleccionados**.

Se generan los resultados y se muestra la ventana Resultados de **métricas** de código. Para ver los detalles de los resultados, expanda el árbol en la **jerarquía**.

::: moniker range="vs-2017"

> [!NOTE]
> El comando **Calcular métricas** de código no funciona para proyectos de .NET Core y .NET Standard. Para calcular métricas de código para un proyecto de .NET Core o .NET Standard, puede:
>
> - Calcule las métricas de código desde la línea de [comandos](#command-line-code-metrics) en su lugar
>
> - Actualización a [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Métricas de código de línea de comandos

Puede generar datos de métricas de código desde la línea de comandos para proyectos de Visual Basic y de C. para aplicaciones de .NET Framework, .NET Core y .NET Standard. Para ejecutar métricas de código desde la línea de comandos, instale el [paquete NuGet Microsoft.CodeAnalysis.Metrics](#microsoftcodeanalysismetrics-nuget-package) o compile el archivo ejecutable [Metrics.exe](#metricsexe) usted mismo.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Paquete NuGet Microsoft.CodeAnalysis.Metrics

La forma más sencilla de generar datos de métricas de código desde la línea de comandos es mediante la instalación del paquete NuGet [Microsoft.CodeAnalysis.Metrics.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) Después de instalar el `msbuild /t:Metrics` paquete, ejecute desde el directorio que contiene el archivo de proyecto. Por ejemplo:

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

Puede reemplazar el nombre del `/p:MetricsOutputFile=<filename>`archivo de salida especificando . También puede obtener datos de métricas de `/p:LEGACY_CODE_METRICS_MODE=true`código de estilo [heredado](#previous-versions) especificando . Por ejemplo:

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

### <a name="code-metrics-output"></a>Salida de métricas de código

La salida XML generada toma el siguiente formato:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Si no desea instalar el paquete NuGet, puede generar y usar el ejecutable *Metrics.exe* directamente. Para generar el ejecutable *Metrics.exe:*

1. Clonar el repositorio [dotnet/roslyn-analyzers.](https://github.com/dotnet/roslyn-analyzers)
2. Abra el símbolo del sistema para desarrolladores de Visual Studio como administrador.
3. Desde la raíz del **repositorio roslyn-analyzers,** ejecute el siguiente comando:`Restore.cmd`
4. Cambie el directorio a *src-Tools*.
5. Ejecute el siguiente comando para compilar el proyecto **Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Se genera un archivo ejecutable denominado *Metrics.exe* en el directorio *artifacts-bin* en la raíz del repositorio.

#### <a name="metricsexe-usage"></a>Uso de Metrics.exe

Para ejecutar *Metrics.exe*, proporcione un proyecto o solución y un archivo XML de salida como argumentos. Por ejemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Modo heredado

Puede elegir crear *Metrics.exe* en *modo heredado.* La versión en modo heredada de la herramienta genera valores de métricas más cercanos a las [versiones anteriores de la herramienta generadas.](#previous-versions) Además, en modo heredado, *Metrics.exe* genera métricas de código para el mismo conjunto de tipos de método para los que las versiones anteriores de la herramienta generaron métricas de código. Por ejemplo, no genera datos de métricas de código para inicializadores de campo y propiedad. El modo heredado es útil para la compatibilidad con versiones anteriores o si tiene puertas de protección de código basadas en números de métricas de código. El comando para compilar *Metrics.exe* en modo heredado es:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obtener más información, consulte [Habilitar la generación de métricas](https://github.com/dotnet/roslyn-analyzers/pull/1841)de código en modo heredado.

### <a name="previous-versions"></a>Versiones anteriores

::: moniker range=">=vs-2019"
Visual Studio 2015 incluía una herramienta de métricas de código de línea de comandos que también se denominaba *Metrics.exe*. Esta versión anterior de la herramienta hizo un análisis binario, es decir, un análisis basado en ensamblado. La versión más reciente de la herramienta *Metrics.exe* analiza el código fuente en su lugar. Dado que la herramienta *Metrics.exe* más reciente está basada en código fuente, los resultados de las métricas de código de línea de comandos pueden ser diferentes de los generados por el IDE de Visual Studio y por versiones anteriores de *Metrics.exe*. A partir de Visual Studio 2019, el IDE de Visual Studio analiza el código fuente como la herramienta de línea de comandos y los resultados deben ser los mismos.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 incluía una herramienta de métricas de código de línea de comandos que también se denominaba *Metrics.exe*. Esta versión anterior de la herramienta hizo un análisis binario, es decir, un análisis basado en ensamblado. La nueva herramienta *Metrics.exe* analiza el código fuente en su lugar. Dado que la nueva herramienta *Metrics.exe* está basada en código fuente, los resultados de las métricas de código de línea de comandos son diferentes de los generados por el IDE de Visual Studio y por las versiones anteriores de *Metrics.exe*.
::: moniker-end

La nueva herramienta de métricas de código de línea de comandos calcula métricas incluso en presencia de errores de código fuente, siempre que se puedan cargar la solución y el proyecto.

#### <a name="metric-value-differences"></a>Diferencias de valor métrico

::: moniker range=">=vs-2019"
A partir de Visual Studio 2019 versión 16.4 y Microsoft.CodeAnalysis.Metics (2.9.5) `SourceLines` y `ExecutableLines` reemplace la métrica anterior. `LinesOfCode` Para obtener descripciones de las nuevas métricas, consulte Valores de [métricas](../code-quality/code-metrics-values.md)de código . La `LinesOfCode` métrica está disponible en modo heredado.
::: moniker-end
::: moniker range="vs-2017"
La `LinesOfCode` métrica es más precisa y confiable en la nueva herramienta de métricas de código de línea de comandos. Es independiente de las diferencias de codegen y no cambia cuando cambia el conjunto de herramientas o el tiempo de ejecución. La nueva herramienta cuenta las líneas de código reales, incluidas las líneas en blanco y los comentarios.
::: moniker-end

Otras métricas, `CyclomaticComplexity` `MaintainabilityIndex` como y usan las mismas fórmulas que las versiones anteriores `IOperations` de *Metrics.exe*, pero la nueva herramienta cuenta el número de instrucciones (instrucciones de origen lógicas) en lugar de instrucciones de lenguaje intermedio (IL). Los números serán ligeramente diferentes a los generados por el IDE de Visual Studio y por las versiones anteriores de *Metrics.exe*.

## <a name="see-also"></a>Consulte también

- [Utilice la ventana Resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de métricas de código](../code-quality/code-metrics-values.md)
