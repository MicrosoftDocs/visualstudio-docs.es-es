---
title: Gravedad y supresión de reglas de analizador
ms.date: 09/23/2019
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
ms.openlocfilehash: c24164f31ca444d17035f145a1783c69dfb2585b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587204"
---
# <a name="use-code-analyzers"></a>Usar analizadores de código

Los analizadores de código .NET Compiler Platform ("Roslyn") C# analizan su código de o Visual Basic a medida que escribe. Cada *diagnóstico* o regla tiene una gravedad y un estado de supresión predeterminados que se pueden sobrescribir para el proyecto. En este artículo se describe la configuración de la gravedad de la regla, el uso de conjuntos de reglas y la supresión de infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores en Explorador de soluciones

Puede realizar gran parte de la personalización de diagnósticos de analizador desde **Explorador de soluciones**. Si [instala analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet, aparece un nodo **analizadores** en el **nodo referencias** o **dependencias** en **Explorador de soluciones**. Si expande **analizadores**y, a continuación, expande uno de los ensamblados del analizador, verá todos los diagnósticos en el ensamblado.

![Nodo analizadores en Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y gravedad predeterminada, en la ventana **propiedades** . Para ver las propiedades, haga clic con el botón derecho en la regla y seleccione **propiedades**, o seleccione la regla y, a continuación, presione **Alt**+**entrar**.

![Propiedades de diagnóstico en ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico y seleccione **Ver ayuda**.

Los iconos situados junto a cada diagnóstico en **Explorador de soluciones** corresponden a los iconos que aparecen en el conjunto de reglas cuando se abre en el editor:

- la "x" en un círculo indica una [gravedad](#rule-severity) de **error**
- el "!" de un triángulo indica una [gravedad](#rule-severity) de **ADVERTENCIA**
- la "i" en un círculo indica una [gravedad](#rule-severity) de la **información**
- la "i" en un círculo de un fondo de color claro indica una [gravedad](#rule-severity) de **oculta**
- la flecha hacia abajo de un círculo indica que se ha suprimido el diagnóstico.

![Iconos de diagnósticos en Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravedad de las reglas

::: moniker range=">=vs-2019"

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. A partir de la versión 16,3 de Visual Studio 2019, puede configurar la gravedad de una regla [en un archivo EditorConfig](#set-rule-severity-in-an-editorconfig-file). También puede cambiar la gravedad de una regla [de explorador de soluciones](#set-rule-severity-from-solution-explorer) o [de un archivo de conjunto de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. Puede cambiar la gravedad de una regla [de explorador de soluciones](#set-rule-severity-from-solution-explorer) o [de un archivo de conjunto de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

En la tabla siguiente se muestran las diferentes opciones de gravedad:

| Gravedad (Explorador de soluciones) | Gravedad (archivo EditorConfig) | Comportamiento en tiempo de compilación | Comportamiento del editor |
|-|-|-|
| Error de : | `error` | Las infracciones aparecen como *errores* en el lista de errores y en la salida de la compilación de línea de comandos y provocan un error en las compilaciones.| El código infractor se subraya con un subrayado ondulado de color rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento. |
| advertencia | `warning` | Las infracciones aparecen como *advertencias* en el lista de errores y en la salida de la compilación de línea de comandos, pero no provocan errores en las compilaciones. | El código infractor se subraya con un subrayado ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento. |
| Info | `suggestion` | Las infracciones aparecen como *mensajes* en el lista de errores y no en todos los resultados de la compilación de línea de comandos. | El código infractor se subraya con un subrayado ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento. |
| Hidden | `silent` | No es visible para el usuario. | No es visible para el usuario. Sin embargo, el diagnóstico se envía al motor de diagnóstico del IDE. |
| Ninguno | `none` | Se han suprimido por completo. | Se han suprimido por completo. |
| Predeterminado | `default` | Corresponde a la gravedad predeterminada de la regla. Para determinar cuál es el valor predeterminado de una regla, mire en el ventana Propiedades. | Corresponde a la gravedad predeterminada de la regla. |

La siguiente captura de pantalla del editor de código muestra tres infracciones diferentes con diferentes niveles de gravedad. Observe el color de la línea ondulada y el cuadrado pequeño coloreado en la barra de desplazamiento de la derecha.

![Infracción de error, advertencia e información en el editor de código](media/diagnostics-severity-colors.png)

En la captura de pantalla siguiente se muestran las tres infracciones que aparecen en el Lista de errores:

![Infracción de error, advertencia e información en Lista de errores](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Establecer la gravedad de la regla en un archivo EditorConfig

(Visual Studio 2019 versión 16,3 y versiones posteriores)

La sintaxis general para especificar la gravedad de una regla en un archivo EditorConfig es la siguiente:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Establecer la gravedad de una regla en un archivo EditorConfig tiene prioridad sobre cualquier gravedad que se establezca en un conjunto de reglas o en Explorador de soluciones. Puede configurar [manualmente](#manually-configure-rule-severity) la gravedad en un archivo EditorConfig o [automáticamente](#automatically-configure-rule-severity) a través de la bombilla que aparece junto a una infracción.

#### <a name="manually-configure-rule-severity"></a>Configurar manualmente la gravedad de la regla

1. Si aún no tiene un archivo EditorConfig para el proyecto, [agregue uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Agregue una entrada para cada regla que desee configurar en la extensión de archivo correspondiente. Por ejemplo, para establecer la gravedad de [CA1822](ca1822.md) en `error` para C# los archivos, la entrada tiene el siguiente aspecto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> En el caso de los analizadores de estilo de código IDE, también puede configurarlos en un archivo EditorConfig con una sintaxis diferente, por ejemplo, `dotnet_style_qualification_for_field = false:suggestion`. Sin embargo, si establece una gravedad mediante la sintaxis de `dotnet_diagnostic`, tendrá prioridad. Para obtener más información, vea [convenciones de lenguaje para EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Configurar automáticamente la gravedad de la regla

Visual Studio proporciona una manera cómoda de configurar la gravedad de una regla en el menú de bombillas de [acciones rápidas](../ide/quick-actions.md) .

1. Después de que se produzca una infracción, mantenga el mouse sobre la línea ondulada en el editor y abra el menú de bombilla. O bien, coloque el cursor en la línea y presione **Ctrl**+ **.** (punto).

2. En el menú de bombilla, seleccione **configurar o suprimir problemas** > **configurar \<ID. de regla > gravedad**.

   ![Configurar la gravedad de la regla desde el menú de bombilla en Visual Studio](media/configure-rule-severity.png)

3. Desde allí, seleccione una de las opciones de gravedad.

   ![Configurar la gravedad de la regla como sugerencia](media/configure-rule-severity-suggestion.png)

   Visual Studio agrega una entrada al archivo EditorConfig para configurar la regla en el nivel solicitado, tal como se muestra en el cuadro vista previa.

   > [!TIP]
   > Si aún no tiene un archivo EditorConfig en el proyecto, Visual Studio crea uno automáticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde Explorador de soluciones

1. En **Explorador de soluciones**, expanda **referencias** > **analizadores** (o **dependencias** > **analizadores** para proyectos de .net Core).

1. Expanda el ensamblado que contiene la regla para la que desea establecer la gravedad.

1. Haga clic con el botón derecho en la regla y seleccione **establecer gravedad del conjunto de reglas**. En el menú emergente, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de la regla en el archivo de conjunto de reglas

![Archivo de conjunto de reglas en Explorador de soluciones](media/ruleset-in-solution-explorer.png)

1. Abra el archivo del conjunto de reglas activo haciendo doble clic en él en **Explorador de soluciones**, seleccionando **abrir conjunto de reglas activas** en el menú contextual del nodo **referencias** > **analizadores** o seleccionando **abrir** en el **código.** Página de propiedades de análisis del proyecto.

   Si es la primera vez que está editando el conjunto de reglas, Visual Studio realiza una copia del archivo de conjunto de reglas predeterminado, lo nombra *\<nombredeproyecto >. ruleset*y lo agrega al proyecto. Este conjunto de reglas personalizado también se convierte en el conjunto de reglas activo para el proyecto.

   > [!NOTE]
   > Los proyectos de .NET Core y .NET Standard no admiten los comandos de menú para conjuntos de reglas en **Explorador de soluciones**, por ejemplo, **abrir el conjunto de reglas activo**. Para especificar un conjunto de reglas no predeterminado para un proyecto de .NET Core o .NET Standard, [agregue manualmente la propiedad **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Todavía puede configurar las reglas en el conjunto de reglas en la interfaz de usuario del editor de conjuntos de reglas de Visual Studio.

1. Vaya a la regla expandiendo su ensamblado contenedor.

1. En la columna **acción** , seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir infracciones

Hay varias maneras de suprimir las infracciones de reglas:

::: moniker range=">=vs-2019"

- En un **archivo EditorConfig**

  Establezca la gravedad en `none`, por ejemplo, `dotnet_diagnostic.CA1822.severity = none`.

- En el menú **analizar**

  Seleccione **analizar** > **compilar y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. A veces, esto se conoce como "línea de referencia".

::: moniker-end

::: moniker range="vs-2017"

- En el menú **analizar**

  Seleccione **analizar** > **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. A veces, esto se conoce como "línea de referencia".

::: moniker-end

- Desde **Explorador de soluciones**

  Establezca la gravedad de la regla en **ninguno**.

- En el **Editor de conjuntos de reglas**

  Desactive la casilla situada junto a su nombre o establezca **acción** en **ninguno**.

- Desde el **Editor de código**

  Coloque el cursor en la línea de código con la infracción y presione **Ctrl**+**punto (.)** para abrir el menú **acciones rápidas** . Seleccione **suprimir CAXXXX** > **en origen/en archivo de supresión**.

  ![Suprimir diagnóstico del menú acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Desde el **lista de errores**

  Seleccione las reglas que desea suprimir y, a continuación, haga clic con el botón derecho y seleccione **suprimir** > **en origen/en el archivo de supresión**.

  - Si se suprime **en origen**, se abre el cuadro de diálogo **vista previa de los cambios** y se muestra una vista previa de la C# [#pragma ADVERTENCIA](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic #Disable Directiva de [ADVERTENCIA](/dotnet/visual-basic/language-reference/directives/directives) que se agrega al código fuente.

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

- Los analizadores se instalan como un paquete Nuget y no como una extensión VSIX.

- Una o varias reglas se infringen en el código del proyecto.

- La [gravedad](#rule-severity) de una regla infringida se establece en cualquiera de las **advertencias**, en cuyo caso las infracciones no provocan un error en la compilación, o **error**, en cuyo caso las infracciones causan un error en la compilación.

El nivel de detalle de la salida de la compilación no afecta a si se muestran las infracciones de la regla. Incluso con un nivel de detalle **silencioso** , las infracciones de reglas aparecen en la salida de la compilación.

> [!TIP]
> Si está acostumbrado a ejecutar el análisis heredado desde la línea de comandos, ya sea con *FxCopCmd. exe* o a través de MSBuild con la marca **RunCodeAnalysis** , aquí se muestra cómo hacerlo con los analizadores de código.

Para ver las infracciones del analizador en la línea de comandos al compilar el proyecto con MSBuild, ejecute un comando similar al siguiente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

En un proyecto de .NET Core, si agrega una referencia a un proyecto que tiene analizadores de NuGet, esos analizadores también se agregan automáticamente al proyecto dependiente. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete NuGet como privado en el archivo *. csproj* o *. vbproj* del proyecto al que se hace referencia estableciendo el atributo **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error del analizador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)
