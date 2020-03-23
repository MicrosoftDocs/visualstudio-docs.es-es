---
title: Gravedad y supresión de la regla del analizador
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431415"
---
# <a name="use-code-analyzers"></a>Usar analizadores de código

Los analizadores de código de .NET Compiler Platform ("Roslyn") analizan el código de Visual Basic o de C. Cada *diagnóstico* o regla tiene un estado de gravedad y supresión predeterminado que se puede sobrescribir para el proyecto. En este artículo se describe la configuración de la gravedad de la regla, el uso de conjuntos de reglas y la supresión de infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores en el Explorador de soluciones

Puede realizar gran parte de la personalización de los diagnósticos del analizador desde el Explorador de **soluciones.** Si [instala analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet, aparece un nodo **Analizadores** en el nodo **Referencias** o **Dependencias** del Explorador de **soluciones**. Si expande **Analizadores**y, a continuación, expande uno de los ensamblados del analizador, verá todos los diagnósticos del ensamblado.

![Nodo Analizadores en el Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y la gravedad predeterminada, en la ventana **Propiedades.** Para ver las propiedades, haga clic con el botón derecho en la regla y seleccione **Propiedades**o seleccione la regla y, a continuación, presione **Alt**+**Enter**.

![Propiedades de diagnóstico en la ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico y seleccione **Ver ayuda**.

Los iconos situados junto a cada diagnóstico en el Explorador de **soluciones** corresponden a los iconos que se ven en el conjunto de reglas cuando se abre en el editor:

- la "x" en un círculo indica una [gravedad](#rule-severity) de **Error**
- el "!" en un triángulo indica una [severidad](#rule-severity) de **Advertencia**
- la "i" en un círculo indica una [gravedad](#rule-severity) de **la información**
- la "i" en un círculo sobre un fondo de color claro indica una [severidad](#rule-severity) de **Oculto**
- la flecha que apunta hacia abajo en un círculo indica que el diagnóstico se suprime

![Iconos de diagnóstico en el Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravedad de las reglas

::: moniker range=">=vs-2019"

Puede configurar la gravedad de las reglas del analizador o *los diagnósticos,* si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. A partir de Visual Studio 2019 versión 16.3, puede configurar la gravedad de una regla [en un archivo EditorConfig](#set-rule-severity-in-an-editorconfig-file). También puede cambiar la gravedad de una regla [desde el Explorador de soluciones](#set-rule-severity-from-solution-explorer) o en un archivo de [conjunto](#set-rule-severity-in-the-rule-set-file)de reglas.

::: moniker-end

::: moniker range="vs-2017"

Puede configurar la gravedad de las reglas del analizador o *los diagnósticos,* si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. Puede cambiar la gravedad de una regla [desde el Explorador de soluciones](#set-rule-severity-from-solution-explorer) o en un archivo de [conjunto](#set-rule-severity-in-the-rule-set-file)de reglas.

::: moniker-end

En la tabla siguiente se muestran las diferentes opciones de gravedad:

| Gravedad (Explorador de soluciones) | Gravedad (archivo EditorConfig) | Comportamiento en tiempo de compilación | Comportamiento del editor |
|-|-|-|
| Error | `error` | Las infracciones aparecen como *errores* en la lista de errores y en la salida de compilación de línea de comandos, y provocan un error en las compilaciones.| El código infractor se subraya con un ondulado rojo y está marcado por un pequeño cuadro rojo en la barra de desplazamiento. |
| Advertencia | `warning` | Las infracciones aparecen como *advertencias* en la lista de errores y en la salida de compilación de línea de comandos, pero no hacen que las compilaciones fallen. | El código infractor se subraya con un ondulación verde y está marcado por un pequeño cuadro verde en la barra de desplazamiento. |
| Información | `suggestion` | Las infracciones aparecen como *mensajes* en la lista de errores y no en absoluto en la salida de compilación de línea de comandos. | El código infractor se subraya con un ondulación gris y se marca con un pequeño cuadro gris en la barra de desplazamiento. |
| Hidden | `silent` | No visible para el usuario. | No visible para el usuario. Sin embargo, el diagnóstico se notifica al motor de diagnóstico IDE. |
| None | `none` | Suprimido completamente. | Suprimido completamente. |
| Valor predeterminado | `default` | Corresponde a la gravedad predeterminada de la regla. Para determinar cuál es el valor predeterminado de una regla, busque en la ventana Propiedades. | Corresponde a la gravedad predeterminada de la regla. |

La siguiente captura de pantalla del editor de código muestra tres infracciones diferentes con diferentes gravedades. Observe el color del squiggle y el pequeño cuadrado de color en la barra de desplazamiento de la derecha.

![Error, advertencia e infracción de información en el editor de código](media/diagnostics-severity-colors.png)

La siguiente captura de pantalla muestra las mismas tres infracciones que aparecen en la lista de errores:

![Error, advertencia e infracción de información en la lista de errores](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Establecer la gravedad de la regla en un archivo EditorConfig

(Visual Studio 2019 versión 16.3 y versiones posteriores)

Puede establecer la gravedad de las advertencias del compilador o las reglas del analizador en un archivo EditorConfig con la sintaxis siguiente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Establecer la gravedad de una regla en un archivo EditorConfig tiene prioridad sobre cualquier gravedad establecida en un conjunto de reglas o en el Explorador de soluciones. Puede configurar [manualmente](#manually-configure-rule-severity) la gravedad en un archivo EditorConfig o [automáticamente](#automatically-configure-rule-severity) a través de la bombilla que aparece junto a una infracción.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Establezca la gravedad de la regla de varias reglas del analizador a la vez en un archivo EditorConfig

(Visual Studio 2019 versión 16.5 y versiones posteriores)

Puede establecer la gravedad para una categoría específica de reglas de analizador o para todas las reglas del analizador con una sola entrada en un archivo EditorConfig.

- Establezca la gravedad de la regla para una categoría de reglas del analizador:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Establezca la gravedad de la regla para todas las reglas del analizador:

`dotnet_analyzer_diagnostic.severity = <severity>`

Si tiene varias entradas que son aplicables a un ID de regla específico, la siguiente es la orden de precedencia para elegir la entrada aplicable:

- La entrada de gravedad para una regla individual por ID tiene prioridad sobre la entrada de gravedad para una categoría.
- La entrada de gravedad para una categoría tiene prioridad sobre la entrada de gravedad para todas las reglas del analizador.

Considere el siguiente ejemplo de EditorConfig, donde [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) tiene la categoría "Performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

En el ejemplo anterior, las tres entradas son aplicables a CA1822. Sin embargo, utilizando las reglas de precedencia especificadas, la primera entrada de gravedad basada en ID de regla gana en las siguientes entradas. En este ejemplo, CA1822 tendrá una gravedad efectiva de "error". Todas las reglas restantes con la categoría "Rendimiento" tendrán "advertencia" de gravedad. Todas las reglas restantes del analizador, que no tienen la categoría "Rendimiento", tendrán "sugerencia" de gravedad.

#### <a name="manually-configure-rule-severity"></a>Configurar manualmente la gravedad de la regla

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Agregue una entrada para cada regla que desee configurar en la extensión de archivo correspondiente. Por ejemplo, para establecer la gravedad de `error` [CA1822](ca1822.md) en para los archivos de C, la entrada tiene el siguiente aspecto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Para los analizadores de estilo de código IDE, también puede configurarlos en `dotnet_style_qualification_for_field = false:suggestion`un archivo EditorConfig con una sintaxis diferente, por ejemplo, . Sin embargo, si establece `dotnet_diagnostic` una gravedad mediante la sintaxis, tiene prioridad. Para obtener más información, consulte Convenciones de [idioma para EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertir un archivo de conjunto de reglas existente en un archivo EditorConfig

A partir de Visual Studio 2019 versión 16.5, los archivos de conjunto de reglas están en desuso en favor del archivo EditorConfig para la configuración del analizador para código administrado. La mayoría de las herramientas de Visual Studio para la configuración de gravedad de la regla del analizador se han actualizado para trabajar en archivos EditorConfig en lugar de archivos de conjunto de reglas. Los archivos EditorConfig le permiten configurar tanto las gravedades de las reglas del analizador como las opciones del analizador, incluidas las opciones de estilo de código IDE de Visual Studio. Se recomienda encarecidamente convertir el archivo de conjunto de reglas existente en un archivo EditorConfig. También se recomienda guardar el archivo EditorConfig en la raíz del repositorio o en la carpeta de la solución. Mediante el uso de la raíz de la carpeta de repositorio o solución, se asegura de que la configuración de gravedad de este archivo se aplica automáticamente a todo el repositorio o la solución, respectivamente.

Hay un par de maneras de convertir un archivo de conjunto de reglas existente en un archivo EditorConfig:

- Desde el Editor de conjuntos de reglas en Visual Studio (requiere Visual Studio 2019 16.5 o posterior). Si el proyecto ya usa un `CodeAnalysisRuleSet`archivo de conjunto de reglas específico como su , puede convertirlo en un archivo EditorConfig equivalente desde el Editor de conjuntos de reglas en Visual Studio.

    1. Haga doble clic en el archivo de conjunto de reglas en el Explorador de soluciones.

       El archivo de conjunto de reglas debe abrirse en el Editor de conjuntos de reglas. Debería ver una **barra** de información en la parte superior del editor de conjuntos de reglas.

       ![Convertir conjunto de reglas en archivo EditorConfig en el Editor de conjuntos de reglas](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Haga clic en** el enlace de la barra de información.

       Esto debería abrir un cuadro de diálogo **Guardar** como que le permita seleccionar el directorio donde desea generar el archivo EditorConfig.

    3. **Haga clic en** el botón **Guardar** para generar el archivo EditorConfig.

       El EditorConfig generado debe abrirse en el editor. Además, la propiedad `CodeAnalysisRuleSet` MSBuild se actualiza en el archivo de proyecto para que ya no haga referencia al archivo de conjunto de reglas original.

- Desde la línea de comandos:

    1. Instale el paquete NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Ejecute `RulesetToEditorconfigConverter.exe` desde el paquete instalado, con rutas de acceso al archivo de conjunto de reglas y el archivo EditorConfig como argumentos de línea de comandos.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Aquí está un archivo de conjunto de reglas de ejemplo para convertir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Aquí está el archivo EditorConfig convertido:

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Configurar automáticamente la gravedad de la regla

##### <a name="configure-from-light-bulb-menu"></a>Configurar desde el menú de bombillas

Visual Studio proporciona una manera cómoda de configurar la gravedad de una regla desde el menú de bombilla [Acciones rápidas.](../ide/quick-actions.md)

1. Después de que se produzca una infracción, coloque el cursor sobre la infracción en el editor y abra el menú de bombillas. O bien, coloque el cursor en la línea y presione **Ctrl**+**.** (punto).

2. En el menú de bombillas, seleccione **Configurar o Suprimir problemas** > **Configurar \<ID de regla> gravedad**.

   ![Configurar la gravedad de la regla desde el menú de bombillas en Visual Studio](media/configure-rule-severity.png)

3. A partir de ahí, seleccione una de las opciones de gravedad.

   ![Configurar la gravedad de la regla como sugerencia](media/configure-rule-severity-suggestion.png)

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado, como se muestra en el cuadro de vista previa.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

##### <a name="configure-from-error-list"></a>Configurar desde la lista de errores

Visual Studio también proporciona una manera cómoda de configurar la gravedad de una regla desde el menú contextual de la lista de errores.

1. Después de que se produzca una infracción, haga clic con el botón derecho en la entrada de diagnóstico de la lista de errores.

2. En el menú contextual, seleccione **Establecer gravedad**.

   ![Configurar la gravedad de la regla desde la lista de errores en Visual Studio](media/configure-rule-severity-error-list.png)

3. A partir de ahí, seleccione una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde el Explorador de soluciones

1. En el Explorador de soluciones, expanda**Analizadores** de **referencias** > (o **Analizadores** > de**dependencias** para proyectos de .NET Core).

2. Expanda el ensamblado que contiene la regla para la que desea establecer la gravedad.

::: moniker range=">=vs-2019"
3. Haga clic con el botón derecho en la regla y seleccione **Establecer gravedad**. En el menú contextual, seleccione una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado. Si el proyecto utiliza un archivo de conjunto de reglas en lugar de un archivo EditorConfig, la entrada de gravedad se agrega al archivo de conjunto de reglas.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig o un archivo de conjunto de reglas en el proyecto, Visual Studio crea un nuevo archivo EditorConfig automáticamente.
::: moniker-end

::: moniker range="vs-2017"
3. Haga clic con el botón derecho en la regla y seleccione **Establecer gravedad**de conjunto de reglas . En el menú contextual, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de la regla en el archivo de conjunto de reglas

![Archivo de conjunto de reglas en el Explorador de soluciones](media/ruleset-in-solution-explorer.png)

1. Abra el archivo de conjunto de reglas activo haciendo doble clic en él en el **Explorador**de soluciones , seleccionando **Abrir** conjunto de reglas activas en el menú contextual **del** > nodo**Analizadores** de referencias o seleccionando **Abrir** en la página de propiedades **Análisis** de código del proyecto.

   Si es la primera vez que edita el conjunto de reglas, Visual Studio realiza una copia del archivo de conjunto de reglas predeterminado, lo * \<nombra nombre nombre nombre proyecto>.ruleset*y lo agrega al proyecto. Este conjunto de reglas personalizado también se convierte en el conjunto de reglas activo para el proyecto.

   > [!NOTE]
   > Los proyectos de .NET Core y .NET Standard no admiten los comandos de menú para conjuntos de reglas en el **Explorador**de soluciones , por ejemplo, Abrir conjunto de **reglas activas**. Para especificar un conjunto de reglas no predeterminado para un proyecto de .NET Core o .NET Standard, agregue manualmente [la propiedad **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Todavía puede configurar las reglas dentro del conjunto de reglas en la interfaz de usuario del editor del conjunto de reglas de Visual Studio.

1. Busque la regla expandiendo su ensamblaje contenedor.

1. En la columna **Acción,** seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseada de la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir infracciones

Hay varias maneras de suprimir las infracciones de reglas:

::: moniker range=">=vs-2019"

- En un **archivo EditorConfig**

  Establezca la gravedad `none`en , `dotnet_diagnostic.CA1822.severity = none`por ejemplo, .

- Desde el menú **Analizar**

  Seleccione **Analizar** > **compilación y Suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. Esto se conoce a veces como "baselining".

::: moniker-end

::: moniker range="vs-2017"

- Desde el menú **Analizar**

  Seleccione **Analizar análisis** > de código de**ejecución y Suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. Esto se conoce a veces como "baselining".

::: moniker-end

- Desde **el Explorador de soluciones**

  Establezca la gravedad de la regla en **Ninguno**.

- Desde el editor de **conjuntos** de reglas

  Desmarque la casilla situada junto a su nombre o establezca **Acción** en **Ninguno**.

- Desde el editor de **código**

  Coloque el cursor en la línea de código con la infracción y presione **Ctrl**+**Period (.)** para abrir el menú **Acciones rápidas.** Seleccione **Suprimir CAXXXX** > en Archivo de**supresión origen/en**.

  ![Suprimir el diagnóstico del menú de acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Desde la lista de **errores**

  Seleccione las reglas que desea suprimir y, a continuación, haga clic con el botón derecho y seleccione **Suprimir** > en archivo de**supresión de origen/en**.

  - Si suprime **En origen**, se abre el cuadro de diálogo Vista previa de **cambios** y muestra una vista previa de la directiva de [advertencia de #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) de C- o de Visual Basic [#Disable](/dotnet/visual-basic/language-reference/directives/directives) que se agrega al código fuente.

    ![Vista previa de la adición de #pragma advertencia en el archivo de código](media/pragma-warning-preview.png)

  - Si selecciona En archivo de **supresión**, se abre <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> el cuadro de diálogo Vista previa de **cambios** y muestra una vista previa del atributo que se agrega al archivo de supresión global.

    ![Vista previa de la adición del atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

  En el cuadro de diálogo **Vista previa de cambios,** seleccione **Aplicar**.

  > [!NOTE]
  > Si no ve la opción de menú **Suprimir** en el **Explorador**de soluciones , es probable que la infracción provenga de la compilación y no del análisis en vivo. La **lista** de errores muestra diagnósticos o infracciones de reglas, tanto desde el análisis de código en vivo como desde la compilación. Dado que los diagnósticos de compilación pueden estar obsoletos, por ejemplo, si ha editado el código para corregir la infracción pero no se ha reconstruido, no puede suprimir estos diagnósticos de la **lista**de errores . Los diagnósticos del análisis en vivo, o IntelliSense, siempre están actualizados con los orígenes actuales y se pueden suprimir desde la **lista**de errores . Para excluir el diagnóstico de *compilación* de la selección, cambie el filtro de origen **Lista** de errores de **Compilación + IntelliSense** a **Solo IntelliSense**. A continuación, seleccione los diagnósticos que desea suprimir y continúe como se describió anteriormente.
  >
  > ![Filtro de origen de lista de errores en Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso de la línea de comandos

Al compilar el proyecto en la línea de comandos, las infracciones de reglas aparecen en la salida de compilación si se cumplen las condiciones siguientes:

- Los analizadores se instalan como un paquete NuGet y no como una extensión VSIX.

- Una o más reglas se infringen en el código del proyecto.

- La [gravedad](#rule-severity) de una regla infringida se establece en **advertencia,** en cuyo caso las infracciones no provocan errores en la compilación o **errores,** en cuyo caso las infracciones provocan un error en la compilación.

La verbosidad de la salida de compilación no afecta a si se muestran las infracciones de reglas. Incluso con una verbosidad **silenciosa,** las infracciones de reglas aparecen en la salida de compilación.

> [!TIP]
> Si está acostumbrado a ejecutar análisis heredados desde la línea de comandos, ya sea con *FxCopCmd.exe* o a través de msbuild con la marca **RunCodeAnalysis,** aquí le indicamos cómo hacerlo con analizadores de código.

Para ver las infracciones del analizador en la línea de comandos al compilar el proyecto mediante msbuild, ejecute un comando como este:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

En un proyecto de .NET Core, si agrega una referencia a un proyecto que tiene analizadores NuGet, esos analizadores también se agregan automáticamente al proyecto dependiente. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete NuGet como privado en el archivo *.csproj* o *.vbproj* del proyecto al que se hace referencia estableciendo el atributo **PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Consulte también

- [Descripción general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error del analizador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)
