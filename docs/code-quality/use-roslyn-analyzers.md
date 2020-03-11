---
title: Gravedad y supresión de reglas del analizador
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408472"
---
# <a name="use-code-analyzers"></a>Uso de analizadores de código

Los analizadores de código de .NET Compiler Platform ("Roslyn") analizan el código de C# o de Visual Basic a medida que se va escribiendo. Cada *diagnóstico* o regla tiene una gravedad y un estado de supresión predeterminados que se pueden sobrescribir según el proyecto. En este artículo se explica cómo establecer la gravedad de una regla, usar conjuntos de reglas y suprimir infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores del Explorador de soluciones

Gran parte de la personalización de diagnósticos de analizador se puede realizar desde el **Explorador de soluciones**. Si [instala analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet, aparecerá un nodo **Analizadores** en el nodo **Referencias** o **Dependencias** del **Explorador de soluciones**. Si expande **Analizadores** y, después, expande uno de los ensamblados del analizador, verá todos los diagnósticos de ese ensamblado.

![Nodo Analizadores del Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

En la ventana **Propiedades** puede ver las propiedades de un diagnóstico, incluida una descripción y su gravedad predeterminada. Para ver las propiedades, haga clic con el botón derecho en la regla y seleccione **Propiedades**, o bien seleccione la regla y presione **Alt**+**Entrar**.

![Propiedades de diagnóstico en la ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea de un diagnóstico, haga clic con el botón derecho en el diagnóstico en cuestión y seleccione **Ver Ayuda**.

Los iconos situados junto a cada diagnóstico en el **Explorador de soluciones** se corresponden con los que aparecen en el conjunto de reglas cuando este se abre en el editor:

- Una "x" en un círculo indica una [gravedad](#rule-severity) de tipo **Error**.
- Un signo "!" en un triángulo indica una [gravedad](#rule-severity) de tipo **Advertencia**.
- Una "i" en un círculo indica una [gravedad](#rule-severity) de tipo **Información**.
- Una "i" en un círculo con un fondo de color claro indica una [gravedad](#rule-severity) de tipo **Oculto**.
- Una flecha hacia abajo dentro de un círculo indica que el diagnóstico se ha suprimido.

![Iconos de diagnóstico del Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravedad de las reglas

::: moniker range=">=vs-2019"

Puede configurar la gravedad de las reglas del analizador o *diagnósticos* si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. A partir de Visual Studio 2019, versión 16.3, la gravedad de una regla se puede configurar [en un archivo .editorconfig](#set-rule-severity-in-an-editorconfig-file). La gravedad de una regla también se puede cambiar [en el Explorador de soluciones](#set-rule-severity-from-solution-explorer) o [en un archivo de conjunto de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Puede configurar la gravedad de las reglas del analizador o *diagnósticos* si [instala los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete NuGet. La gravedad de una regla se puede cambiar [en el Explorador de soluciones](#set-rule-severity-from-solution-explorer) o [en un archivo de conjunto de reglas](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

En la siguiente tabla se muestran las distintas opciones de gravedad:

| Gravedad (Explorador de soluciones) | Gravedad (archivo .editorconfig) | Comportamiento en tiempo de compilación | Comportamiento del editor |
|-|-|-|
| Error | `error` | Las infracciones aparecen como *Errores* en la Lista de errores y en la salida de compilación de la línea de comandos, e impiden que las compilaciones se lleven a cabo.| El código infractor se subraya con un subrayado ondulado de color rojo y se marca con un pequeño cuadro rojo en la barra de desplazamiento. |
| Advertencia | `warning` | Las infracciones aparecen como *Advertencias* en la Lista de errores y en la salida de compilación de la línea de comandos, pero no impiden que las compilaciones se lleven a cabo. | El código infractor se subraya con un subrayado ondulado de color verde y se marca con un pequeño cuadro verde en la barra de desplazamiento. |
| Info | `suggestion` | Las infracciones aparecen como *Mensajes* en la Lista de errores, pero no se incluyen en la salida de compilación de la línea de comandos. | El código infractor se subraya con un subrayado ondulado de color gris y se marca con un pequeño cuadro gris en la barra de desplazamiento. |
| Hidden | `silent` | No es visible para el usuario. | No es visible para el usuario, pero el diagnóstico se notifica al motor de diagnóstico del IDE. |
| None | `none` | Se suprime por completo. | Se suprime por completo. |
| Default | `default` | Corresponde a la gravedad predeterminada de la regla. Para averiguar cuál es el valor predeterminado de una regla, consulte la ventana Propiedades. | Corresponde a la gravedad predeterminada de la regla. |

La siguiente captura de pantalla del editor de código muestra tres infracciones diferentes con distintos niveles de gravedad. Fíjese en el color de la línea ondulada y en el cuadrado pequeño de color en la barra de desplazamiento de la derecha.

![Infracciones de error, de advertencia y de información en el editor de código](media/diagnostics-severity-colors.png)

En la siguiente captura de pantalla se muestran las mismas tres infracciones, pero en la Lista de errores:

![Infracciones de error, de advertencia y de información en la Lista de errores](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Establecer la gravedad de la regla en un archivo .editorconfig

(Visual Studio 2019, versión 16.3 y posteriores)

Esta es sintaxis general para especificar la gravedad de una regla en un archivo .editorconfig:

`dotnet_diagnostic.<rule ID>.severity = <severity>`

Establecer la gravedad de una regla en un archivo .editorconfig tiene prioridad sobre cualquier gravedad que se establezca en un conjunto de reglas o en el Explorador de soluciones. La gravedad en un archivo .editorconfig se puede [configurar manualmente](#manually-configure-rule-severity) o [automáticamente](#automatically-configure-rule-severity) con la bombilla que aparece junto a una infracción.

#### <a name="manually-configure-rule-severity"></a>Configurar la gravedad de una regla manualmente

1. Si aún no tiene un archivo .editorconfig en el proyecto, [agregue uno](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Agregue una entrada por cada regla que quiera configurar en la extensión de archivo correspondiente. Por ejemplo, para establecer la gravedad de [CA1822](ca1822.md) en `error` en los archivos de C#, la entrada tendrá el siguiente aspecto:

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Los analizadores de estilo de código del IDE también se pueden configurar en un archivo .editorconfig con una sintaxis diferente (por ejemplo, `dotnet_style_qualification_for_field = false:suggestion`), pero si se establece una gravedad mediante la sintaxis `dotnet_diagnostic`, esta tendrá prioridad. Para más información, vea [Convenciones de lenguaje de EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Configurar la gravedad de una regla automáticamente

Visual Studio proporciona una forma cómoda de configurar la gravedad de una regla en el menú de bombilla [Acciones rápidas](../ide/quick-actions.md).

1. Cuando se produzca una infracción, mantenga el ratón sobre la línea ondulada en el editor y abra el menú de bombilla. También puede colocar el cursor en la línea y presionar **Ctrl**+ **.** (punto).

2. En el menú de bombilla, seleccione **Configurar o suprimir problemas** > **Configurar gravedad de \<identificador de regla>** .

   ![Configurar la gravedad de una regla desde el menú de bombilla en Visual Studio](media/configure-rule-severity.png)

3. Una vez ahí, seleccione una de las opciones de gravedad.

   ![Configurar la gravedad de una regla como Sugerencia](media/configure-rule-severity-suggestion.png)

   Visual Studio agrega una entrada al archivo .editorconfig para establecer la regla en el nivel solicitado, tal y como se muestra en el cuadro vista previa.

   > [!TIP]
   > Si todavía no tiene un archivo .editorconfig en el proyecto, Visual Studio crea uno automáticamente.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Establecer la gravedad de una regla desde el Explorador de soluciones

1. En el **Explorador de soluciones**, expanda **Referencias** > **Analizadores** (o **Dependencias** > **Analizadores** si el proyecto es de .NET Core).

1. Expanda el ensamblado que contiene la regla cuya gravedad quiera establecer.

1. Haga clic con el botón derecho en la regla y seleccione **Configurar gravedad del conjunto de reglas**. En el menú flotante, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo del conjunto de reglas activo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Establecer la gravedad de una regla en el archivo de conjunto de reglas

![Archivo de conjunto de reglas en el Explorador de soluciones](media/ruleset-in-solution-explorer.png)

1. Para abrir el archivo del conjunto de reglas activo, haga doble clic en él en el **Explorador de soluciones**, seleccione **Abrir conjunto de reglas activo** en el menú contextual del nodo **Referencias** > **Analizadores**, o bien seleccione **Abrir** en la página de propiedades **Análisis de código** del proyecto.

   Si es la primera vez que edita el conjunto de reglas, Visual Studio hace una copia del archivo de conjunto de reglas predeterminado, le asigna el nombre *\<nombreDeProyecto>.ruleset* y lo agrega al proyecto. Este conjunto de reglas personalizado también pasa a ser el conjunto de reglas activo del proyecto.

   > [!NOTE]
   > Los proyectos de .NET Core y .NET Standard no admiten los comandos de menú relativos a conjuntos de reglas del **Explorador de soluciones** (por ejemplo, **Abrir conjunto de reglas activo**). Para especificar un conjunto de reglas no predeterminado en un proyecto de .NET Core o .NET Standard, [agregue la propiedad **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) manualmente al archivo del proyecto. Las reglas del conjunto de reglas se pueden seguir configurando en la interfaz de usuario del editor de conjuntos de reglas de Visual Studio.

1. Vaya a la regla expandiendo el ensamblado que la contiene.

1. En la columna **Acción**, seleccione el valor para abrir una lista desplegable y seleccione la gravedad que quiera de la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir infracciones

Existen varias formas de suprimir infracciones de regla:

::: moniker range=">=vs-2019"

- En un archivo **.editorconfig**

  Establezca la gravedad en `none`, por ejemplo, `dotnet_diagnostic.CA1822.severity = none`.

- En el menú **Analizar**

  Seleccione **Analizar** > **Compilar y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. Esta acción se denomina a veces "línea de base".

::: moniker-end

::: moniker range="vs-2017"

- En el menú **Analizar**

  Seleccione **Analizar** > **Ejecutar análisis de código y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. Esta acción se denomina a veces "línea de base".

::: moniker-end

- En el **Explorador de soluciones**

  Establezca la gravedad de la regla en **Ninguna**.

- En el **editor de conjuntos de reglas**

  Desactive la casilla situada junto al nombre de la regla o establezca **Acción** en **Ninguna**.

- En el **editor de código**

  Coloque el cursor en la línea de código con la infracción y presione **Ctrl**+**punto (.)** para abrir el menú **Acciones rápidas**. Seleccione **Suprimir CAXXXX** > **En origen/En archivo de supresión**.

  ![Suprimir diagnóstico en el menú Acciones rápidas](media/suppress-diagnostic-from-editor.png)

- En la **Lista de errores**

  Seleccione las reglas que quiera suprimir, haga clic con el botón derecho y seleccione **Suprimir** > **En origen/En archivo de supresión**.

  - Si opta por suprimir **En origen**, se abre el cuadro de diálogo **Vista previa de los cambios**, que muestra una vista previa de la directiva [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) (C#) o [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives) (Visual Basic) que se agrega al código fuente.

    ![Vista previa de la adición de #pragma warning en el archivo de código](media/pragma-warning-preview.png)

  - Si selecciona **En archivo de supresión**, se abre el cuadro de diálogo **Vista previa de los cambios**, que muestra una vista previa del atributo <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> que se agrega al archivo de supresiones global.

    ![Vista previa de la adición del atributo SuppressMessage al archivo de supresiones](media/preview-changes-in-suppression-file.png)

  En el cuadro de diálogo **Vista previa de los cambios**, seleccione **Aplicar**.

  > [!NOTE]
  > Si no ve la opción de menú **Suprimir** en el **Explorador de soluciones**, es probable que la infracción provenga de la compilación y no del análisis activo. La **Lista de errores** muestra diagnósticos (o infracciones de reglas) procedentes tanto del análisis de código activo como de la compilación. Como los diagnósticos de compilación pueden estar obsoletos (por ejemplo, porque se haya editado el código para corregir la infracción, pero no se haya vuelto a compilar), estos diagnósticos no se pueden suprimir de la **Lista de errores**. Los diagnósticos procedentes del análisis en vivo, o IntelliSense, siempre están actualizados con los orígenes actuales y sí se pueden suprimir de la **Lista de errores**. Para excluir los diagnósticos de *compilación* de la selección, cambie el filtro de origen **Lista de errores** de **Compilación + IntelliSense** a **Solo IntelliSense**. Luego, seleccione los diagnósticos que quiera suprimir y continúe del modo descrito arriba.
  >
  > ![Filtro de origen Lista de errores en Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso de la línea de comandos

Al compilar el proyecto en la línea de comandos, la salida de la compilación reflejará infracciones de regla si se cumplen las siguientes condiciones:

- Los analizadores están instalados como un paquete Nuget, y no como una extensión VSIX.

- Hay una o varias infracciones de regla en el código del proyecto.

- La [gravedad](#rule-severity) de una regla infringida se establece en **Advertencia** (en cuyo caso las infracciones no provocan un error de compilación) o en **Error**error (en cuyo caso sí se genera un error de compilación).

El nivel de detalle de la salida de la compilación no afecta al hecho de que las infracciones de regla se muestren o no. Incluso con un nivel de detalle **quiet**, las infracciones de regla aparecerán en la salida de la compilación.

> [!TIP]
> Si está acostumbrado a ejecutar análisis heredados desde la línea de comandos, ya sea con *FxCopCmd.exe* o a través de MSBuild con la marca **RunCodeAnalysis**, aquí le indicamos cómo hacerlo con analizadores de código.

Para ver las infracciones del analizador en la línea de comandos al compilar el proyecto con MSBuild, ejecute un comando similar al siguiente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

En la siguiente imagen se muestra la salida de compilación de línea de comandos de la compilación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

Si se agrega una referencia a un proyecto de .NET Core que tiene analizadores de NuGet, esos analizadores también se agregarán automáticamente al proyecto dependiente. Si quiere deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete NuGet como privado en el archivo *.csproj* o *.vbproj* del proyecto al que se hace referencia; para ello, establezca el atributo **PrivateAssets**:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Envío de un error del analizador de código](https://github.com/dotnet/roslyn-analyzers/issues)
- [Uso de conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supresión de advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)
