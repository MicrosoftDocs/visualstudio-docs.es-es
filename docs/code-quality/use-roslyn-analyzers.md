---
title: Gravedad y supresión de reglas de analizador
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5c5af5c98be92e52c356e0f20eaf437f66878690
ms.sourcegitcommit: 8a699df154464387f327691dce507d7c3d0e2aab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060447"
---
# <a name="use-code-analyzers"></a>Usar analizadores de código

Los analizadores de código .NET Compiler Platform ("Roslyn") C# analizan su código de o Visual Basic a medida que escribe. Cada *diagnóstico* o regla tiene una gravedad y un estado de supresión predeterminados que se pueden sobrescribir para el proyecto. En este artículo se describe la configuración de la gravedad de la regla, el uso de conjuntos de reglas y la supresión de infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores en Explorador de soluciones

Puede realizar gran parte de la personalización de diagnósticos de analizador desde **Explorador de soluciones**. Si [instala analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet, aparece un nodo **analizadores** en el nodo **referencias** o **dependencias** en **Explorador de soluciones**. Si expande **analizadores**y, a continuación, expande uno de los ensamblados del analizador, verá todos los diagnósticos en el ensamblado.

![Nodo analizadores en Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y gravedad predeterminada, en la ventana **propiedades** . Para ver las propiedades, haga clic con el botón derecho en la regla y seleccione **propiedades**, o seleccione la regla y, a continuación, presione **Alt**+**entrar**.

![Propiedades de diagnóstico en ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico y seleccione **Ver ayuda**.

Los iconos situados junto a cada diagnóstico en **Explorador de soluciones** corresponden a los iconos que aparecen en el conjunto de reglas cuando se abre en el editor:

- la "i" en un círculo indica una [gravedad](#rule-severity) de la **información**
- el "!" de un triángulo indica una [gravedad](#rule-severity) de **ADVERTENCIA**
- la "x" en un círculo indica una [gravedad](#rule-severity) de **error**
- la "i" en un círculo de un fondo de color claro indica una [gravedad](#rule-severity) de **oculta**
- la flecha hacia abajo de un círculo indica que se ha suprimido el diagnóstico.

![Iconos de diagnósticos en Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Conjuntos de reglas

Un [conjunto de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) es un archivo XML que almacena la gravedad y el estado de supresión para el diagnóstico individual.

> [!NOTE]
> Los conjuntos de reglas pueden incluir reglas de análisis heredados y analizadores de código.

Para editar el conjunto de reglas activo en el editor de conjuntos de reglas, haga clic con el botón secundario en el nodo**analizadores** de **referencias** > en **Explorador de soluciones** y seleccione **abrir conjunto de reglas activas**. Si es la primera vez que está editando el conjunto de reglas, Visual Studio realiza una copia del archivo de conjunto de reglas predeterminado, le asigna el nombre  *\<nombreDeProyecto >. ruleset*y lo agrega al proyecto. Este conjunto de reglas personalizado también se convierte en el conjunto de reglas activo para el proyecto.

Para cambiar el conjunto de reglas activo de un proyecto, vaya a la pestaña **análisis de código** de las propiedades de un proyecto. Seleccione el conjunto de reglas en la lista **ejecutar este conjunto de reglas**. Para abrir el conjunto de reglas, seleccione **abrir**.

> [!NOTE]
> Los proyectos de .NET Core y .NET Standard no admiten los comandos de menú para conjuntos de reglas en **Explorador de soluciones**, por ejemplo, **abrir el conjunto de reglas activo**. Para especificar un conjunto de reglas no predeterminado para un proyecto de .NET Core o .NET Standard, [agregue manualmente la propiedad **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Todavía puede configurar las reglas en el conjunto de reglas en la interfaz de usuario del editor de conjuntos de reglas de Visual Studio.

## <a name="rule-severity"></a>Gravedad de las reglas

Puede configurar la gravedad de las reglas del analizador,o diagnósticos, si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. En la tabla siguiente se muestran las opciones de gravedad de los diagnósticos:


::: moniker range="vs-2019"
|Severity|Comportamiento en tiempo de compilación|Comportamiento del editor|
|-|-|-|
|Error|Las infracciones aparecen como *errores* en el **lista de errores** y en la salida de la compilación de línea de comandos y provocan un error en las compilaciones.|El código infractor se subraya con un ondulado rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento.|
|Advertencia|Las infracciones aparecen como *advertencias* en el **lista de errores** y en la salida de la compilación de línea de comandos, pero no provocan errores en las compilaciones.|El código infractor se subraya con un ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento.|
|Sugerencia|Las infracciones aparecen como *mensajes* en el **lista de errores**y no en todos los resultados de la compilación de línea de comandos.|El código infractor se subraya con un ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento.|
|Silent|No es visible para el usuario.|No es visible para el usuario. Sin embargo, el diagnóstico se envía al motor de diagnóstico del IDE.|
|None|Se han suprimido por completo.|Se han suprimido por completo.|
::: moniker-end

::: moniker range="< vs-2019"
|Severity|Comportamiento en tiempo de compilación|Comportamiento del editor|
|-|-|-|
|Error|Las infracciones aparecen como *errores* en el **lista de errores** y en la salida de la compilación de línea de comandos y provocan un error en las compilaciones.|El código infractor se subraya con un ondulado rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento.|
|Advertencia|Las infracciones aparecen como *advertencias* en el **lista de errores** y en la salida de la compilación de línea de comandos, pero no provocan errores en las compilaciones.|El código infractor se subraya con un ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento.|
|Info|Las infracciones aparecen como *mensajes* en el **lista de errores**y no en todos los resultados de la compilación de línea de comandos.|El código infractor se subraya con un ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento.|
|Hidden|No es visible para el usuario.|No es visible para el usuario. Sin embargo, el diagnóstico se envía al motor de diagnóstico del IDE.|
|None|Se han suprimido por completo.|Se han suprimido por completo.|
::: moniker-end

Además, puede "restablecer" la gravedad de una regla si la establece en el valor **predeterminado**. Cada diagnóstico tiene una gravedad predeterminada que puede verse en la ventana **propiedades** .

En la captura de pantalla siguiente se muestran tres infracciones de diagnóstico diferentes en el editor de código, con tres gravedades diferentes. Observe el color del ondulado, así como el cuadro pequeño de la barra de desplazamiento de la derecha.

![Infracción de error, advertencia e información en el editor de código](media/diagnostics-severity-colors.png)

En la captura de pantalla siguiente se muestran las tres infracciones que aparecen en el **lista de errores**:

![Infracción de error, advertencia e información en Lista de errores](media/diagnostics-severities-in-error-list.png)

Puede cambiar la gravedad de una regla de **Explorador de soluciones**, o en el  *\<archivo ProjectName >. ruleset* que se agrega a la solución después de cambiar la gravedad de una regla en **Explorador de soluciones**.

![Archivo de conjunto de reglas en Explorador de soluciones](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de la regla desde Explorador de soluciones

1. En **Explorador de soluciones**, expanda**analizadores** de **referencias** > (**analizadores** de**dependencias** > para proyectos de .net Core).

1. Expanda el ensamblado que contiene la regla para la que desea establecer la gravedad.

1. Haga clic con el botón derecho en la regla y seleccione **establecer gravedad del conjunto de reglas**. En el menú emergente, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de la regla en el archivo de conjunto de reglas

1. Abra el archivo del [conjunto de reglas](analyzer-rule-sets.md) haciendo doble clic en él en **Explorador de soluciones**, seleccionando **abrir conjunto de reglas activas** en el menú contextual del nodo **analizadores** o seleccionando **abrir** en la página de propiedades análisis de **código** para el proyecto.

1. Vaya a la regla expandiendo su ensamblado contenedor.

1. En la columna **acción** , seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir infracciones

Hay varias maneras de suprimir las infracciones de reglas:

- En el menú **analizar**

  Seleccione **analizar** > **Ejecutar Análisis de código y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. A veces, esto se conoce como "línea de referencia".

- Desde **Explorador de soluciones**

  Para suprimir una infracción en **Explorador de soluciones**, establezca la gravedad de la regla en **ninguno**.

- En el **Editor de conjuntos de reglas**

  Para suprimir una infracción del editor de conjuntos de reglas, desactive la casilla situada junto a su nombre o establezca **acción** en **ninguno**.

- Desde el **Editor de código**

  Para suprimir una infracción del editor de código, coloque el cursor en la línea de código con la infracción y presione **Ctrl**+ **.** para abrir el menú **acciones rápidas** . Seleccione **suprimir CAXXXX** > **en origen/en archivo de supresión**.

  ![Suprimir diagnóstico del menú acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Desde el **lista de errores**

  Puede suprimir uno o varios diagnósticos de la **lista de errores** seleccionando los que desea suprimir y, a continuación, haciendo clic con el botón derecho y seleccionando **suprimir** > **en el archivo de supresión de origen/en**.

  - Si se suprime **en origen**, se abre el cuadro de diálogo **vista previa de los cambios** y se muestra una vista previa de la C# [#pragma ADVERTENCIA](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic #Disable Directiva de [ADVERTENCIA](/dotnet/visual-basic/language-reference/directives/directives) que se agrega al código fuente.

    ![Vista previa de la adición de #pragma ADVERTENCIA en el archivo de código](media/pragma-warning-preview.png)

  - Si selecciona **en archivo de supresión**, se abre el cuadro de diálogo **vista previa de los cambios** y se muestra una <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> vista previa del atributo que se agrega al archivo de supresiones global.

    ![Vista previa de la adición del atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

  En el cuadro de diálogo **vista previa de los cambios** , seleccione **aplicar**.

  > [!NOTE]
  > Si no ve la opción de menú suprimir en **Explorador de soluciones**, es probable que la infracción provenga de la compilación y no del análisis activo. El **lista de errores** muestra los diagnósticos, o las infracciones de las reglas, desde el análisis de código activo y la compilación. Como los diagnósticos de compilación pueden estar obsoletos, por ejemplo, si ha editado el código para corregir la infracción pero no se ha vuelto a generar, no podrá suprimir estos diagnósticos del **lista de errores**. Los diagnósticos del análisis en vivo, o IntelliSense, siempre están actualizados con los orígenes actuales y se pueden suprimir del **lista de errores**. Para excluir diagnósticos de *compilación* de la selección, cambie el **lista de errores** filtro de origen de **compilación + IntelliSense** a **solo IntelliSense**. A continuación, seleccione los diagnósticos que desea suprimir y continúe como se describió anteriormente.
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

En la imagen siguiente se muestra el resultado de la compilación de la línea de comandos de compilar un proyecto que contiene una infracción de la regla del analizador:

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
