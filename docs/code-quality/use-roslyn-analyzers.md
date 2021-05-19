---
title: Configuración del analizador
ms.date: 05/10/2021
description: Aprenda a personalizar las reglas del analizador de Roslyn. Vea cómo ajustar las gravedades del analizador, suprimir infracciones y designar archivos como código generado.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973387"
---
# <a name="overview"></a>Información general

Cada regla o  diagnóstico del analizador de Roslyn tiene una gravedad y un estado de supresión predeterminados que se pueden sobrescribir y personalizar para el proyecto. En este artículo se describe cómo establecer las gravedades del analizador y suprimir las infracciones del analizador.

## <a name="configure-severity-levels"></a>Configuración de los niveles de gravedad

::: moniker range=">=vs-2019"

A partir de Visual Studio versión 16.3 de 2019, puede configurar la gravedad de las reglas del [](#set-rule-severity-from-the-light-bulb-menu)analizador, o *diagnósticos,* en un archivo [EditorConfig](#set-rule-severity-in-an-editorconfig-file), desde el menú de bombilla y desde la lista de errores.

::: moniker-end

::: moniker range="vs-2017"

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos,* si [instala](../code-quality/install-roslyn-analyzers.md) los analizadores como un paquete NuGet. Puede cambiar la gravedad de una regla [de](#set-rule-severity-from-solution-explorer) Explorador de soluciones o en un archivo de conjunto [de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

En la tabla siguiente se muestran las distintas opciones de gravedad:

| Gravedad (Explorador de soluciones) | Gravedad (archivo .editorconfig) | Comportamiento en tiempo de compilación | Comportamiento del editor |
|-|-|-|
| Error | `error` | Las infracciones aparecen como *Errores* en la Lista de errores y en la salida de compilación de la línea de comandos, e impiden que las compilaciones se lleven a cabo.| El código infractor se subraya con un subrayado ondulado de color rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento. |
| Advertencia | `warning` | Las infracciones aparecen como *Advertencias* en la Lista de errores y en la salida de compilación de la línea de comandos, pero no impiden que las compilaciones se lleven a cabo. | El código infractor se subraya con un subrayado ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento. |
| Información | `suggestion` | Las infracciones aparecen como *Mensajes* en la Lista de errores, pero no se incluyen en la salida de compilación de la línea de comandos. | El código infractor se subraya con un subrayado ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento. |
| Hidden | `silent` | No es visible para el usuario. | No es visible para el usuario, pero el diagnóstico se notifica al motor de diagnóstico del IDE. |
| Ninguno | `none` | Se suprime por completo. | Se suprime por completo. |
| Default | `default` | Corresponde a la gravedad predeterminada de la regla. Para averiguar cuál es el valor predeterminado de una regla, consulte la ventana Propiedades. | Corresponde a la gravedad predeterminada de la regla. |

Si un analizador detecta infracciones de reglas, se notifican en el editor de código (como un *subrayado ondulado* bajo el código infractor) y en la ventana Lista de errores.

Las infracciones de analizadores informadas en la lista de errores coincide con el [valor del nivel de gravedad](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la regla. Las infracciones de analizadores también se muestran en el editor de código como subrayados ondulados debajo del código infractor. En la imagen siguiente se muestran tres infracciones&mdash;un error (subrayado ondulado rojo), una advertencia (subrayado ondulado verde) y una sugerencia (tres puntos grises):

![Subrayados ondulados en el editor de código en Visual Studio](media/diagnostics-severity-colors.png)

En la captura de pantalla siguiente se muestran las mismas tres infracciones que aparecen en la lista de errores:

![Error, advertencia e infracción de información en la lista de errores](media/diagnostics-severities-in-error-list.png)

Muchas reglas de los analizadores, o *diagnósticos*, tienen una o más *correcciones de código* asociadas que se pueden aplicar para corregir la infracción de la regla. Las correcciones de código se muestran en el menú del icono de bombilla junto con otros tipos de [Acciones rápidas](../ide/quick-actions.md). Para obtener información sobre estas correcciones de código, vea [Acciones rápidas comunes](../ide/quick-actions.md).

![Infracción de analizador y corrección de código de Acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Gravedad "Oculta" frente a gravedad "Ninguno"

`Hidden` Las reglas de gravedad que están habilitadas de forma predeterminada son diferentes de las reglas deshabilitadas o de gravedad `None` de dos maneras.

- Si se ha registrado alguna corrección de código para una regla de gravedad, la corrección se ofrece como una acción de refactorización de código de bombilla en Visual Studio, aunque el diagnóstico oculto no sea visible para el `Hidden` usuario. Este no es el caso de las reglas `None` de gravedad deshabilitadas.
- `Hidden` Las reglas de gravedad se pueden configurar de forma masiva mediante entradas que establecen la gravedad de las reglas de varios analizadores [a la vez en un archivo EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` Las reglas de gravedad no se pueden configurar de esta manera. En su lugar, deben configurarse mediante entradas que establezcan la gravedad de la regla en un [archivo EditorConfig para cada identificador de regla.](#set-rule-severity-in-an-editorconfig-file)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Establecer la gravedad de la regla en un archivo EditorConfig

(Visual Studio versión 16.3 y posteriores de 2019)

Puede establecer la gravedad de las advertencias del compilador o las reglas del analizador en un archivo EditorConfig con la sintaxis siguiente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Establecer la gravedad de una regla en un archivo EditorConfig tiene prioridad sobre cualquier gravedad establecida en un conjunto de reglas o en Explorador de soluciones. Puede configurar [manualmente la](#manually-configure-rule-severity-in-an-editorconfig-file) gravedad en un [](#set-rule-severity-from-the-light-bulb-menu) archivo EditorConfig o automáticamente a través de la bombilla que aparece junto a una infracción.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Establecer la gravedad de la regla de varias reglas del analizador a la vez en un archivo EditorConfig

(Visual Studio 2019, versión 16.5 y posteriores)

Puede establecer la gravedad de una categoría específica de reglas de analizador o para todas las reglas del analizador con una sola entrada en un archivo EditorConfig.

- Establezca la gravedad de la regla para una categoría de reglas de analizador:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Establezca la gravedad de la regla para todas las reglas del analizador:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Las entradas para configurar varias reglas del analizador a la vez solo se aplican a las reglas que están *habilitadas de forma predeterminada.* Las reglas del analizador que están marcadas como deshabilitadas de forma predeterminada en el paquete del analizador deben habilitarse a través `dotnet_diagnostic.<rule ID>.severity = <severity>` de entradas explícitas.

Si tiene varias entradas que son aplicables a un identificador de regla específico, el siguiente es el orden de precedencia para elegir la entrada aplicable:

- La entrada de gravedad de una regla individual por identificador tiene prioridad sobre la entrada de gravedad de una categoría.
- La entrada de gravedad de una categoría tiene prioridad sobre la entrada de gravedad para todas las reglas del analizador.

Considere el siguiente ejemplo de EditorConfig, donde [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) tiene la categoría "Performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

En el ejemplo anterior, las tres entradas son aplicables a CA1822. Sin embargo, con las reglas de precedencia especificadas, la primera entrada de gravedad basada en el identificador de regla gana sobre las entradas siguientes. En este ejemplo, CA1822 tendrá una gravedad efectiva de "error". Todas las reglas restantes con la categoría "Rendimiento" tendrán gravedad "advertencia". Todas las reglas restantes del analizador, que no tienen la categoría "Rendimiento", tendrán una "sugerencia" de gravedad.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Configurar manualmente la gravedad de la regla en un archivo EditorConfig

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue un .](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Agregue una entrada para cada regla que quiera configurar en la extensión de archivo correspondiente. Por ejemplo, para establecer la gravedad de [CA1822 en](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) para los archivos de C#, la entrada `error` tiene el siguiente aspecto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Para los analizadores de estilo de código ide, también puede configurarlos en un archivo EditorConfig con una sintaxis diferente, por ejemplo, `dotnet_style_qualification_for_field = false:suggestion` . Sin embargo, si establece una gravedad mediante la `dotnet_diagnostic` sintaxis , tiene prioridad. Para obtener más información, vea [Convenciones de lenguaje para EditorConfig.](/dotnet/fundamentals/code-analysis/style-rules/language-rules)

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Establecer la gravedad de la regla en el menú de bombilla

Visual Studio proporciona una manera cómoda de configurar la gravedad de una regla desde el [menú de bombilla](../ide/quick-actions.md) Acciones rápidas.

1. Después de que se produzca una infracción, mantenga el puntero sobre el ondulado de infracción en el editor y abra el menú de bombilla. O bien, coloque el cursor en la línea y presione **Ctrl** + **.** (punto).

2. En el menú de bombilla, seleccione **Configurar o suprimir problemas** Configure > **\<rule ID> severity (Configurar gravedad).**

   ![Configuración de la gravedad de la regla desde el menú de bombilla en Visual Studio](media/configure-rule-severity.png)

3. Desde allí, elija una de las opciones de gravedad.

   ![Configuración de la gravedad de la regla como sugerencia](media/configure-rule-severity-suggestion.png)

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado, como se muestra en el cuadro de vista previa.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

### <a name="set-rule-severity-from-the-error-list-window"></a>Establecer la gravedad de la regla en la ventana Lista de errores

Visual Studio también proporciona una manera cómoda de configurar la gravedad de una regla desde el menú contextual de la lista de errores.

1. Después de que se produzca una infracción, haga clic con el botón derecho en la entrada de diagnóstico de la lista de errores.

2. En el menú contextual, seleccione **Establecer gravedad.**

   ![Configurar la gravedad de la regla de la lista de errores en Visual Studio](media/configure-rule-severity-error-list.png)

3. Desde allí, elija una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde Explorador de soluciones

Puede realizar gran parte de la personalización de los diagnósticos del **analizador desde Explorador de soluciones**. Si instala [analizadores como](../code-quality/install-roslyn-analyzers.md) un paquete NuGet, aparecerá un  nodo Analizadores en el nodo Referencias o  **Dependencias** en **Explorador de soluciones**. Si expande **Analizadores** y, a continuación, expande uno de los ensamblados del analizador, verá todos los diagnósticos en el ensamblado.

![Nodo Analizadores en Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y gravedad predeterminada, en la **ventana** Propiedades. Para ver las propiedades, haga clic con el botón derecho en la regla y seleccione **Propiedades** o seleccione la regla y presione **Alt** + **Entrar.**

![Propiedades de diagnóstico en ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico y seleccione **Ver ayuda**.

Los iconos junto a cada diagnóstico de **Explorador de soluciones** corresponden a los iconos que ve en el conjunto de reglas al abrirlo en el editor:

- la "x" de un círculo indica una [gravedad de](#configure-severity-levels) **Error**
- "!" en un triángulo indica una [gravedad de](#configure-severity-levels) **Advertencia**
- la "i" en un círculo indica una [gravedad de](#configure-severity-levels) **Información**
- la "i" en un círculo sobre un fondo de color claro indica [una gravedad](#configure-severity-levels) de **Hidden**
- la flecha hacia abajo de un círculo indica que se suprime el diagnóstico.

![Iconos de diagnóstico en Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertir un archivo de conjunto de reglas existente en un archivo EditorConfig

A partir Visual Studio versión 16.5 de 2019, los archivos del conjunto de reglas están en desuso en favor del archivo EditorConfig para la configuración del analizador de código administrado. La mayoría de las Visual Studio para la configuración de gravedad de la regla del analizador se han actualizado para que funcionen en archivos EditorConfig en lugar de archivos de conjunto de reglas. Los archivos EditorConfig permiten configurar las opciones de analizador y gravedad de las reglas del analizador, Visual Studio opciones de estilo de código ide. Se recomienda encarecidamente convertir el archivo de conjunto de reglas existente en un archivo EditorConfig. También se recomienda guardar el archivo EditorConfig en la raíz del repositorio o en la carpeta de la solución. Al usar la raíz del repositorio o la carpeta de la solución, se asegura de que la configuración de gravedad de este archivo se aplica automáticamente a todo el repositorio o la solución, respectivamente.

Hay un par de maneras de convertir un archivo de conjunto de reglas existente en un archivo EditorConfig:

- Desde el Editor de conjunto de reglas Visual Studio (requiere Visual Studio 2019 16.5 o posterior). Si el proyecto ya usa un archivo de conjunto de reglas específico como , puede convertirlo en un archivo EditorConfig equivalente desde el Editor de conjunto de `CodeAnalysisRuleSet` reglas Visual Studio.

    1. Haga doble clic en el archivo del conjunto de reglas Explorador de soluciones.

       El archivo Conjunto de reglas debe abrirse en el Editor de conjunto de reglas. Debería ver una barra de información en la que **se** puede hacer clic en la parte superior del editor del conjunto de reglas.

       ![Convertir conjunto de reglas en archivo EditorConfig en el Editor de conjunto de reglas](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Seleccione el **vínculo de la barra de** información.

       Esto debería abrir un **cuadro de diálogo Guardar** como que le permita seleccionar el directorio donde desea generar el archivo EditorConfig.

    3. Seleccione el **botón** Guardar para generar el archivo EditorConfig.

       El valor de EditorConfig generado debe abrirse en el editor. Además, la propiedad MSBuild se actualiza en el archivo de proyecto para que ya no haga referencia `CodeAnalysisRuleSet` al archivo de conjunto de reglas original.

- Desde la línea de comandos:

    1. Instale el paquete NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Ejecute desde el paquete instalado, con rutas de acceso al archivo de conjunto de reglas y el `RulesetToEditorconfigConverter.exe` archivo EditorConfig como argumentos de línea de comandos.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Este es un archivo de conjunto de reglas de ejemplo para convertir:

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

Este es el archivo EditorConfig convertido:

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
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde Explorador de soluciones

1. En Explorador de soluciones, expanda   >  **Analizadores de referencias** (o   >  **Analizadores de dependencias** para proyectos de .NET Core).

2. Expanda el ensamblado que contiene la regla para la que desea establecer la gravedad.

::: moniker range=">=vs-2019"
3. Haga clic con el botón derecho en la regla y **seleccione Establecer gravedad.** En el menú contextual, elija una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado. Si el proyecto usa un archivo de conjunto de reglas en lugar de un archivo EditorConfig, la entrada de gravedad se agrega al archivo del conjunto de reglas.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig o un archivo de conjunto de reglas en el proyecto, Visual Studio crea automáticamente un archivo EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Haga clic con el botón derecho en la regla y **seleccione Establecer gravedad del conjunto de reglas.** En el menú contextual, elija una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de la regla en el archivo de conjunto de reglas

![Archivo de conjunto de reglas en Explorador de soluciones](media/ruleset-in-solution-explorer.png)

1. Abra el archivo de conjunto de reglas activo de una de las maneras siguientes:

- En **Explorador de soluciones**, haga doble clic en el archivo, haga clic con el botón derecho en el nodo  >  **Analizadores de** referencias y seleccione Abrir conjunto de reglas **activas**.
- En la **Code Analysis** de propiedades del proyecto, seleccione **Abrir** .

  Si es la primera vez que edita el conjunto de reglas, Visual Studio realiza una copia del archivo de conjunto de reglas predeterminado, lo denomina *\<projectname> .ruleset* y lo agrega al proyecto. Este conjunto de reglas personalizado también se convierte en el conjunto de reglas activo para el proyecto.

   > [!NOTE]
   > Los proyectos de .NET Core .NET Standard no admiten los comandos de menú para conjuntos de reglas en **Explorador de soluciones**, por ejemplo, Abrir conjunto **de reglas activas**. Para especificar un conjunto de reglas no predeterminado para un proyecto de .NET Core o .NET Standard, agregue manualmente la propiedad [ **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Todavía puede configurar las reglas dentro del conjunto de reglas en la interfaz Visual Studio editor del conjunto de reglas.

1. Vaya a la regla expandiendo su ensamblado que lo contiene.

1. En la **columna** Acción, seleccione el valor para abrir una lista desplegable y elija la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configuración del código generado

Los analizadores se ejecutan en todos los archivos de código fuente de un proyecto e informan de infracciones en ellos. Sin embargo, estas infracciones no son útiles en los archivos de código generados, como los archivos de código generados por el diseñador, los archivos de código fuente temporales generados por el sistema de compilación, etc. Los usuarios no pueden editar manualmente estos archivos o no les preocupa corregir infracciones en este tipo de archivos generados por herramientas.

De forma predeterminada, el controlador del analizador que ejecuta los analizadores trata los archivos con determinado nombre, extensión de archivo o encabezado de archivo generado automáticamente como archivos de código generados. Por ejemplo, un nombre de archivo que termina con `.designer.cs` o `.generated.cs` se considera código generado. Sin embargo, es posible que estas heurísticas no puedan identificar todos los archivos de código generados personalizados en el código fuente del usuario.

A partir de Visual Studio 2019 16.5, los usuarios finales pueden configurar archivos o carpetas específicos para tratarse como código generado en un [archivo EditorConfig](https://editorconfig.org/). Siga los pasos que se indican a continuación para agregar esta configuración:

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue un .](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. Agregue la `generated_code = true | false` entrada para archivos o carpetas específicos. Por ejemplo, para tratar todos los archivos cuyo nombre termina con como código `.MyGenerated.cs` generado, la entrada sería la siguiente:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Supresión de infracciones

Puede suprimir las infracciones de reglas mediante varios métodos. Para obtener más información, vea [Suprimir infracciones de análisis de código.](../code-quality/in-source-suppression-overview.md)

## <a name="command-line-usage"></a>Uso de la línea de comandos

Al compilar el proyecto en la línea de comandos, aparecen infracciones de reglas en la salida de compilación si se cumplen las condiciones siguientes:

- Los analizadores se instalan con el SDK de .NET o como un paquete NuGet, y no como una extensión VSIX.

  En el caso de los analizadores instalados mediante el SDK de .NET, puede que necesite [habilitar los analizadores](../code-quality/install-net-analyzers.md). Para los estilos de código, también puede [aplicar estilos de código en la compilación](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) estableciendo una propiedad de MSBuild.

- Se infringen una o varias reglas en el código del proyecto.

- La [gravedad](#configure-severity-levels) de una regla infringido se establece en la advertencia **,** en cuyo caso las infracciones no provocan errores de compilación, o bien en **el error**, en cuyo caso las infracciones hacen que se genere un error en la compilación.

El nivel de detalle de la salida de compilación no afecta a si se muestran infracciones de reglas. Incluso con **un nivel** de detalle silencioso, las infracciones de reglas aparecen en la salida de la compilación.

> [!TIP]
> Si está acostumbrado a ejecutar análisis heredados desde la línea de comandos, ya sea con *FxCopCmd.exe* o a través de msbuild con la marca **RunCodeAnalysis,** aquí se muestra cómo hacerlo con los analizadores de código.

Para ver las infracciones del analizador en la línea de comandos al compilar el proyecto mediante msbuild, ejecute un comando como este:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

En un proyecto de .NET Core, si agrega una referencia a un proyecto que tiene analizadores de NuGet, esos analizadores también se agregan automáticamente al proyecto dependiente. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete NuGet como privado en el archivo *.csproj* o *.vbproj* del proyecto al que se hace referencia estableciendo el **atributo PrivateAssets:**

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Consulte también

- [Introducción a los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Envío de un error del analizador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Uso de conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supresión de advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)
- [Opciones de configuración para el análisis de código (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
