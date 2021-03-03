---
title: Configuración del analizador
ms.date: 09/02/2020
description: Obtenga información sobre cómo personalizar las reglas del analizador de Roslyn. Vea cómo ajustar gravedades del analizador, suprimir infracciones y designar archivos como código generado.
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
ms.openlocfilehash: 956e63384619a82b7f0abb7dd3771ed2db9cba01
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684372"
---
# <a name="overview"></a>Información general

Cada una de las reglas o *diagnósticos* del analizador de Roslyn tiene una gravedad y un estado de supresión predeterminados que se pueden sobrescribir y personalizar para el proyecto. En este artículo se describe el establecimiento de gravedad del analizador y la supresión de infracciones del analizador.

## <a name="configure-severity-levels"></a>Configurar niveles de gravedad

::: moniker range=">=vs-2019"

A partir de la versión 16,3 de Visual Studio 2019, puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, en un [archivo EditorConfig](#set-rule-severity-in-an-editorconfig-file), en el [menú de bombilla](#set-rule-severity-from-the-light-bulb-menu)y en la lista de errores.

::: moniker-end

::: moniker range="vs-2017"

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. Puede cambiar la gravedad de una regla [de explorador de soluciones](#set-rule-severity-from-solution-explorer) o [de un archivo de conjunto de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

En la tabla siguiente se muestran las diferentes opciones de gravedad:

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

En la captura de pantalla siguiente se muestran las tres infracciones que aparecen en el Lista de errores:

![Infracción de error, advertencia e información en Lista de errores](media/diagnostics-severities-in-error-list.png)

Muchas reglas de los analizadores, o *diagnósticos*, tienen una o más *correcciones de código* asociadas que se pueden aplicar para corregir la infracción de la regla. Las correcciones de código se muestran en el menú del icono de bombilla junto con otros tipos de [Acciones rápidas](../ide/quick-actions.md). Para obtener información sobre estas correcciones de código, vea [Acciones rápidas comunes](../ide/quick-actions.md).

![Infracción de analizador y corrección de código de Acción rápida](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Gravedad ' Hidden ' frente a ' none ' gravedad

`Hidden` las reglas de gravedad que están habilitadas de forma predeterminada son diferentes de las reglas deshabilitadas o de `None` gravedad de dos maneras.

- Si se ha registrado alguna corrección de código para una `Hidden` regla de gravedad, la corrección se ofrece como una acción de refactorización de código de bombilla en Visual Studio, aunque el diagnóstico oculto no sea visible para el usuario. Este no es el caso de las reglas de gravedad deshabilitadas `None` .
- `Hidden` las reglas de gravedad se pueden configurar de forma masiva mediante entradas que [establecen la gravedad de la regla de varias reglas del analizador a la vez en un archivo EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` las reglas de gravedad no se pueden configurar de esta manera. En su lugar, deben configurarse mediante entradas que [establezcan la gravedad de la regla en un archivo EditorConfig para cada identificador de regla](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Establecer la gravedad de la regla en un archivo EditorConfig

(Visual Studio 2019 versión 16,3 y versiones posteriores)

Puede establecer la gravedad de las advertencias del compilador o las reglas del analizador en un archivo EditorConfig con la siguiente sintaxis:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Establecer la gravedad de una regla en un archivo EditorConfig tiene prioridad sobre cualquier gravedad que se establezca en un conjunto de reglas o en Explorador de soluciones. Puede configurar [manualmente](#manually-configure-rule-severity-in-an-editorconfig-file) la gravedad en un archivo EditorConfig o [automáticamente](#set-rule-severity-from-the-light-bulb-menu) a través de la bombilla que aparece junto a una infracción.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Establecer la gravedad de la regla de varias reglas del analizador a la vez en un archivo EditorConfig

(Visual Studio 2019 versión 16,5 y versiones posteriores)

Puede establecer la gravedad para una categoría específica de reglas del analizador o para todas las reglas del analizador con una sola entrada en un archivo EditorConfig.

- Establezca la gravedad de la regla para una categoría de reglas del analizador:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Establezca la gravedad de la regla para todas las reglas del analizador:

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Las entradas para configurar varias reglas del analizador a la vez solo se aplican a las reglas que están *habilitadas de forma predeterminada*. Las reglas del analizador que se marcan como deshabilitadas de forma predeterminada en el paquete del analizador se deben habilitar mediante entradas explícitas `dotnet_diagnostic.<rule ID>.severity = <severity>` .

Si tiene varias entradas que son aplicables a un ID. de regla específico, el orden de prioridad que se especifica a continuación es el siguiente:

- La entrada de gravedad de una regla individual por identificador tiene prioridad sobre la entrada de gravedad de una categoría.
- La entrada de gravedad de una categoría tiene prioridad sobre la entrada de gravedad para todas las reglas del analizador.

Considere el siguiente ejemplo de EditorConfig, donde [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) tiene la categoría "performance":

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

En el ejemplo anterior, las tres entradas se aplican a CA1822. Sin embargo, con las reglas de precedencia especificadas, la primera entrada de gravedad basada en el identificador de regla gana sobre las siguientes entradas. En este ejemplo, CA1822 tendrá una gravedad efectiva de "error". Todas las reglas restantes con la categoría "rendimiento" tendrán la gravedad "ADVERTENCIA". Todas las demás reglas del analizador, que no tienen la categoría "rendimiento", tendrán la gravedad "sugerencia".

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Configurar manualmente la gravedad de la regla en un archivo EditorConfig

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Agregue una entrada para cada regla que desee configurar en la extensión de archivo correspondiente. Por ejemplo, para establecer la gravedad de [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) en `error` para los archivos de C#, la entrada tiene el siguiente aspecto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> En el caso de los analizadores de estilo de código IDE, también puede configurarlos en un archivo EditorConfig con una sintaxis diferente, por ejemplo, `dotnet_style_qualification_for_field = false:suggestion` . Sin embargo, si establece una gravedad mediante la `dotnet_diagnostic` sintaxis, tendrá prioridad. Para obtener más información, vea [convenciones de lenguaje para EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Establecer la gravedad de la regla desde el menú de bombilla

Visual Studio proporciona una manera cómoda de configurar la gravedad de una regla en el menú de bombillas de [acciones rápidas](../ide/quick-actions.md) .

1. Después de que se produzca una infracción, mantenga el mouse sobre la línea ondulada en el editor y abra el menú de bombilla. O bien, coloque el cursor en la línea y presione **Ctrl** + **.** (punto).

2. En el menú de bombilla, seleccione **configurar o suprimir problemas** > **configurar \<rule ID> gravedad**.

   ![Configurar la gravedad de la regla desde el menú de bombilla en Visual Studio](media/configure-rule-severity.png)

3. Desde allí, elija una de las opciones de gravedad.

   ![Configurar la gravedad de la regla como sugerencia](media/configure-rule-severity-suggestion.png)

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado, tal como se muestra en el cuadro vista previa.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

### <a name="set-rule-severity-from-the-error-list-window"></a>Establecer la gravedad de la regla desde la ventana de Lista de errores

Visual Studio también proporciona una forma cómoda de configurar la gravedad de una regla en el menú contextual de la lista de errores.

1. Después de producirse una infracción, haga clic con el botón derecho en la entrada de diagnóstico en la lista de errores.

2. En el menú contextual, seleccione **establecer gravedad**.

   ![Configurar la gravedad de la regla en la lista de errores en Visual Studio](media/configure-rule-severity-error-list.png)

3. Desde allí, elija una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde Explorador de soluciones

Puede realizar gran parte de la personalización de diagnósticos de analizador desde **Explorador de soluciones**. Si [instala analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet, aparece un nodo **analizadores** en el **nodo referencias** o **dependencias** en **Explorador de soluciones**. Si expande **analizadores** y, a continuación, expande uno de los ensamblados del analizador, verá todos los diagnósticos en el ensamblado.

![Nodo analizadores en Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y gravedad predeterminada, en la ventana **propiedades** . Para ver las propiedades, haga clic con el botón secundario en la regla y seleccione **propiedades**, o seleccione la regla y, a continuación, presione **Alt** + **entrar**.

![Propiedades de diagnóstico en ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico y seleccione **Ver ayuda**.

Los iconos situados junto a cada diagnóstico en **Explorador de soluciones** corresponden a los iconos que aparecen en el conjunto de reglas cuando se abre en el editor:

- la "x" en un círculo indica una [gravedad](#configure-severity-levels) de **error**
- el "!" de un triángulo indica una [gravedad](#configure-severity-levels) de **ADVERTENCIA**
- la "i" en un círculo indica una [gravedad](#configure-severity-levels) de la **información**
- la "i" en un círculo de un fondo de color claro indica una [gravedad](#configure-severity-levels) de **oculta**
- la flecha hacia abajo de un círculo indica que se ha suprimido el diagnóstico.

![Iconos de diagnósticos en Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertir un archivo ruleset existente en archivo EditorConfig

A partir de la versión 16,5 de Visual Studio 2019, los archivos ruleset están desusados en favor del archivo EditorConfig para la configuración del analizador para código administrado. La mayoría de las herramientas de Visual Studio para la configuración de gravedad de la regla del analizador se ha actualizado para que funcione en archivos EditorConfig en lugar de en archivos ruleset. Los archivos EditorConfig le permiten configurar las opciones del analizador y las gravedad de la regla del analizador, incluidas las opciones de estilo de código del IDE de Visual Studio. Se recomienda convertir el archivo ruleset existente en un archivo EditorConfig. También se recomienda que guarde el archivo EditorConfig en la raíz del repositorio o en la carpeta de la solución. Mediante el uso de la raíz del repositorio o la carpeta de la solución, se asegura de que la configuración de gravedad de este archivo se aplique automáticamente a todo el repositorio o solución, respectivamente.

Hay un par de formas de convertir un archivo ruleset existente en un archivo EditorConfig:

- En el editor ruleset de Visual Studio (requiere Visual Studio 2019 16,5 o posterior). Si el proyecto ya usa un archivo ruleset específico como su `CodeAnalysisRuleSet` , puede convertirlo en un archivo EditorConfig equivalente desde el editor de ruleset dentro de Visual Studio.

    1. Haga doble clic en el archivo ruleset en Explorador de soluciones.

       El archivo ruleset debe abrirse en el editor ruleset. Debería ver una **barra** de deshacer clic en la parte superior del editor de ruleset.

       ![Convertir ruleset en archivo EditorConfig en el editor ruleset](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Seleccione el vínculo de la **barra de barra** .

       Debe abrir un cuadro de diálogo **Guardar como** que le permita seleccionar el directorio en el que desea generar el archivo EditorConfig.

    3. Seleccione el botón **Guardar** para generar el archivo EditorConfig.

       El EditorConfig generado debe abrirse en el editor. Además, la propiedad `CodeAnalysisRuleSet` de MSBuild se actualiza en el archivo de proyecto para que ya no haga referencia al archivo ruleset original.

- Desde la línea de comandos:

    1. Instale el paquete NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Ejecute `RulesetToEditorconfigConverter.exe` desde el paquete instalado, con las rutas de acceso al archivo ruleset y el archivo EditorConfig como argumentos de la línea de comandos.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

A continuación se muestra un ejemplo de archivo ruleset para convertir:

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

1. En explorador de soluciones, expanda los analizadores de **referencias**  >   (o los   >  **analizadores** de dependencias para proyectos de .net Core).

2. Expanda el ensamblado que contiene la regla para la que desea establecer la gravedad.

::: moniker range=">=vs-2019"
3. Haga clic con el botón secundario en la regla y seleccione **establecer gravedad**. En el menú contextual, elija una de las opciones de gravedad.

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado. Si el proyecto usa un archivo ruleset en lugar de un archivo EditorConfig, se agrega la entrada Severity al archivo ruleset.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig o un archivo ruleset en el proyecto, Visual Studio crea un nuevo archivo EditorConfig.
::: moniker-end

::: moniker range="vs-2017"
3. Haga clic con el botón secundario en la regla y seleccione **establecer gravedad del conjunto de reglas**. En el menú contextual, elija una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de la regla en el archivo de conjunto de reglas

![Archivo de conjunto de reglas en Explorador de soluciones](media/ruleset-in-solution-explorer.png)

1. Abra el archivo del conjunto de reglas activo de una de las siguientes maneras:

- En **Explorador de soluciones**, haga doble clic en el archivo, haga clic con el botón secundario en el nodo **referencias**  >  **analizadores** y seleccione **abrir conjunto de reglas activo**.
- En la página de propiedades **análisis de código** del proyecto, seleccione **abrir** .

  Si es la primera vez que está editando el conjunto de reglas, Visual Studio realiza una copia del archivo de conjunto de reglas predeterminado, le asigna el nombre *\<projectname> . ruleset* y lo agrega al proyecto. Este conjunto de reglas personalizado también se convierte en el conjunto de reglas activo para el proyecto.

   > [!NOTE]
   > Los proyectos de .NET Core y .NET Standard no admiten los comandos de menú para conjuntos de reglas en **Explorador de soluciones**, por ejemplo, **abrir el conjunto de reglas activo**. Para especificar un conjunto de reglas no predeterminado para un proyecto de .NET Core o .NET Standard, [agregue manualmente la propiedad **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Todavía puede configurar las reglas en el conjunto de reglas en la interfaz de usuario del editor de conjuntos de reglas de Visual Studio.

1. Vaya a la regla expandiendo su ensamblado contenedor.

1. En la columna **acción** , seleccione el valor para abrir una lista desplegable y elija la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configurar código generado

Los analizadores se ejecutan en todos los archivos de origen de un proyecto y notifican las infracciones en ellos. Sin embargo, estas infracciones no son útiles en los archivos de código generados, como los archivos de código generado por el diseñador, los archivos de código fuente temporales generados por el sistema de compilación, etc. Los usuarios no pueden editar manualmente estos archivos o no están preocupados por corregir las infracciones en este tipo de archivos generados por herramientas.

De forma predeterminada, el controlador del analizador que ejecuta analizadores trata los archivos con el nombre, la extensión de archivo o el encabezado de archivo generado automáticamente como archivos de código generados. Por ejemplo, un nombre de archivo que termina con `.designer.cs` o `.generated.cs` se considera código generado. Sin embargo, es posible que esta heurística no pueda identificar todos los archivos de código generado personalizados en el código fuente del usuario.

A partir de Visual Studio 2019 16,5, los usuarios finales pueden configurar archivos y carpetas específicos para que se traten como código generado en un [archivo EditorConfig](https://editorconfig.org/). Siga los pasos que se indican a continuación para agregar este tipo de configuración:

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Agregue la `generated_code = true | false` entrada para archivos y/o carpetas específicos. Por ejemplo, para tratar todos los archivos cuyo nombre termina con `.MyGenerated.cs` como código generado, la entrada sería la siguiente:

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Suprimir infracciones

Hay varias maneras de suprimir las infracciones de reglas:

::: moniker range=">=vs-2019"

- En un **archivo EditorConfig**

  Establezca la gravedad en `none` , por ejemplo, `dotnet_diagnostic.CA1822.severity = none` .

- En el menú **analizar**

  Seleccione **analizar**  >  **compilación e suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. A veces, esto se conoce como "línea de referencia".

::: moniker-end

::: moniker range="vs-2017"

- En el menú **analizar**

  Seleccione **analizar**  >  **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. A veces, esto se conoce como "línea de referencia".

::: moniker-end

- Desde **Explorador de soluciones**

  Establezca la gravedad de la regla en **ninguno**.

- En el **Editor de conjuntos de reglas**

  Desactive la casilla situada junto a su nombre o establezca **acción** en **ninguno**.

- Desde el **Editor de código**

  Coloque el cursor en la línea de código con la infracción y presione **Ctrl** + **(.)** para abrir el menú **acciones rápidas** . Seleccione **suprimir CAXXXX**  >  **en origen/en archivo de supresión**.

  ![Suprimir diagnóstico del menú acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Desde el **lista de errores**

  Seleccione las reglas que desea suprimir y, a continuación, haga clic con el botón derecho y seleccione **suprimir**  >  **en origen/en archivo de supresión**.

  - Si se suprime **en origen**, se abre el cuadro de diálogo **vista previa de los cambios** y se muestra una vista previa de la [Advertencia de #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) de C# o Visual Basic #Disable Directiva de [ADVERTENCIA](/dotnet/visual-basic/language-reference/directives/directives) que se agrega al código fuente.

    ![Vista previa de la adición de #pragma ADVERTENCIA en el archivo de código](media/pragma-warning-preview.png)

  - Si selecciona **en archivo de supresión**, se abre el cuadro de diálogo **vista previa de los cambios** y se muestra una vista previa del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que se agrega al archivo de supresiones global.

    ![Vista previa de la adición del atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

  En el cuadro de diálogo **vista previa de los cambios** , seleccione **aplicar**.

  > [!NOTE]
  > Si no ve la opción de menú **suprimir** en **Explorador de soluciones**, es probable que la infracción provenga de la compilación y no del análisis activo. El **lista de errores** muestra los diagnósticos, o las infracciones de las reglas, desde el análisis de código activo y la compilación. Como los diagnósticos de compilación pueden estar obsoletos, por ejemplo, si ha editado el código para corregir la infracción pero no se ha vuelto a generar, no podrá suprimir estos diagnósticos del **lista de errores**. Los diagnósticos del análisis en vivo, o IntelliSense, siempre están actualizados con los orígenes actuales y se pueden suprimir del **lista de errores**. Para excluir diagnósticos de *compilación* de la selección, cambie el **lista de errores** filtro de origen de **compilación + IntelliSense** a **solo IntelliSense**. A continuación, seleccione los diagnósticos que desea suprimir y continúe como se describió anteriormente.
  >
  > ![Lista de errores filtro de origen en Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso de la línea de comandos

Al compilar el proyecto en la línea de comandos, las infracciones de la regla aparecen en la salida de la compilación si se cumplen las condiciones siguientes:

- Los analizadores se instalan con el SDK de .NET o como un paquete de NuGet, y no como una extensión VSIX.

  En el caso de los analizadores instalados con el SDK de .NET, puede que tenga que [habilitar los analizadores](../code-quality/install-net-analyzers.md). En el caso de los estilos de código, también puede [aplicar estilos de código en la compilación](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) estableciendo una propiedad de MSBuild.

- Una o varias reglas se infringen en el código del proyecto.

- La [gravedad](#configure-severity-levels) de una regla infringida se establece en cualquiera de las **advertencias**, en cuyo caso las infracciones no provocan un error en la compilación, o **error**, en cuyo caso las infracciones causan un error en la compilación.

El nivel de detalle de la salida de la compilación no afecta a si se muestran las infracciones de la regla. Incluso con un nivel de detalle **silencioso** , las infracciones de reglas aparecen en la salida de la compilación.

> [!TIP]
> Si está acostumbrado a ejecutar el análisis heredado desde la línea de comandos, ya sea con *FxCopCmd.exe* o a través de MSBuild con la marca **RunCodeAnalysis** , aquí se muestra cómo hacerlo con los analizadores de código.

Para ver las infracciones del analizador en la línea de comandos al compilar el proyecto con MSBuild, ejecute un comando similar al siguiente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

En un proyecto de .NET Core, si agrega una referencia a un proyecto que tiene analizadores de NuGet, esos analizadores también se agregan automáticamente al proyecto dependiente. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete NuGet como privado en el archivo *. csproj* o *. vbproj* del proyecto al que se hace referencia estableciendo el atributo **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Consulte también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error del analizador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)
- [Opciones de configuración para el análisis de código (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
