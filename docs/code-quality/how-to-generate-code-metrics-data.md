---
title: Generar métricas de código desde la línea de comandos o IDE
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3f8d6f2df0b0d9ec6e3f9d8ead7fd1e08929f8e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966536"
---
# <a name="how-to-generate-code-metrics-data"></a>Cómo: generar datos de métricas de código

Puede generar resultados de métricas de código para una solución completa o uno o varios proyectos. Las métricas del código está disponible dentro del entorno de desarrollo interactivo (IDE) de Visual Studio y, para C# y proyectos de Visual Basic, en la línea de comandos.

Además, puede instalar un [paquete NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) que incluye cuatro métricas del código [analizador](roslyn-analyzers-overview.md) reglas: CA1501, CA1502, CA1505 y CA1506. Estas reglas están deshabilitadas de forma predeterminada, pero puede habilitarlas desde **el Explorador de soluciones** o en un [conjunto de reglas](using-rule-sets-to-group-code-analysis-rules.md) archivo.

## <a name="visual-studio-ide-code-metrics"></a>Métricas de código de Visual Studio IDE

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

## <a name="command-line-code-metrics"></a>Métricas del código de línea de comandos

Puede generar datos de métricas de código desde la línea de comandos para C# y proyectos de Visual Basic para aplicaciones de .NET Framework, .NET Core y .NET Standard. Se llama a las herramientas de las métricas del código de línea de comandos *Metrics.exe*.

Para obtener el *Metrics.exe* ejecutable, debe [generados por el usuario](#generate-the-executable). En un futuro próximo, una [versión publicada de *Metrics.exe* estará disponible](https://github.com/dotnet/roslyn-analyzers/issues/1756) para no tener que crearlas usted mismo.

### <a name="generate-the-executable"></a>Generar el archivo ejecutable

Para generar el archivo ejecutable *Metrics.exe*, siga estos pasos:

1. Clone el [dotnet/roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers) repositorio.
2. Abra el símbolo del sistema para desarrolladores para Visual Studio como administrador.
3. Desde la raíz de la **analizadores de roslyn** repo, ejecute el siguiente comando: `Restore.cmd`
4. Cambie el directorio a *src\Tools*.
5. Ejecute el siguiente comando para compilar el **Metrics.csproj** proyecto:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Un archivo ejecutable denominado *Metrics.exe* se genera en el *binarios* directorio bajo la raíz del repositorio.

   > [!TIP]
   > Para compilar *Metrics.exe* en [modo heredado](#legacy-mode), ejecute el siguiente comando:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Uso

Para ejecutar *Metrics.exe*, proporcionar un proyecto o solución y una salida XML de archivo como argumentos. Por ejemplo:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Salida

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Diferencias de herramienta

Las versiones anteriores de Visual Studio, incluidos Visual Studio 2015, incluyen una herramienta de métricas de código de línea de comandos denominada *Metrics.exe*. Esta versión anterior de la herramienta realizó un análisis binario, es decir, un análisis basado en ensamblados. La nueva herramienta analiza el código fuente en su lugar. Dado que el nuevo *Metrics.exe* es origen basado en código, los resultados son diferentes a lo que generan las versiones anteriores de *Metrics.exe* y en el IDE de Visual Studio 2017.

El nuevo *Metrics.exe* herramienta puede calcular métricas incluso en presencia de errores de código fuente, siempre que se pueden cargar la solución y proyecto.

#### <a name="metric-value-differences"></a>Diferencias de valor de métrica

El `LinesOfCode` métrica es más precisas y confiables en el nuevo *Metrics.exe*. Es independiente de las diferencias de generación de código y no cambia cuando cambia el conjunto de herramientas o en tiempo de ejecución. El nuevo *Metrics.exe* cuenta reales líneas de código, incluidas las líneas en blanco y comentarios.

Otras métricas como `CyclomaticComplexity` y `MaintainabilityIndex` utilizar las fórmulas de la mismas que en versiones anteriores de *Metrics.exe*, pero el nuevo *Metrics.exe* cuenta el número de `IOperations` (lógico instrucciones de origen) en lugar de instrucciones de lenguaje intermedio (IL). Los números será ligeramente diferentes de versiones anteriores de *Metrics.exe* y de los resultados de las métricas del código de IDE de Visual Studio 2017.

### <a name="legacy-mode"></a>Modo heredado

También puede compilar *Metrics.exe* en *modo heredado*. La versión en modo heredado de la herramienta genera los valores de métricas que están más cercano de las versiones anteriores de la herramienta genera. Además, en el modo heredado *Metrics.exe* genera métricas de código para el mismo conjunto de método que las versiones anteriores de las métricas de herramienta genera código para los tipos. Por ejemplo, no genera datos de métricas de código para los inicializadores de campo y propiedad. Modo heredado es útil para hacia atrás compatibilidad o si tiene código de comprobación de las validaciones basadas en métricas de código números. El comando para compilar *Metrics.exe* en modo heredado es:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Para obtener más información, consulte [Habilitar generación de las métricas del código en modo heredado](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>Vea también

- [Utilice la ventana de resultados de las métricas de código](../code-quality/working-with-code-metrics-data.md)
- [Valores de las métricas de código](../code-quality/code-metrics-values.md)