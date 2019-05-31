---
title: Supresión y la gravedad de regla de analizador
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
ms.openlocfilehash: 7132fae3623e1ad10fb35d2b903935cdbffee12d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676694"
---
# <a name="use-roslyn-analyzers"></a>Usar analizadores de Roslyn

Reglas del analizador de .NET compiler Platform («Roslyn»), o *diagnósticos*, analizar el código de C# o Visual Basic a medida que escribe. Cada diagnóstico tiene un estado de gravedad y la supresión de predeterminado que se puede sobrescribir para el proyecto. Este artículo describe la gravedad de regla de configuración, utilizando los conjuntos de reglas y suprimir las infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores en el Explorador de soluciones

Puede hacer gran parte de la personalización de diagnósticos del analizador de **el Explorador de soluciones**. Si se [instalar analizadores de](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet, un **analizadores** nodo aparece en el **referencias** o **dependencias** nodo  **El Explorador de soluciones**. Si expande **analizadores**y, a continuación, expanda uno de los ensamblados del analizador, verá que todos los diagnósticos en el ensamblado.

![Nodo de analizadores en el Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluidos su descripción y la gravedad de forma predeterminada, en el **propiedades** ventana. Para ver las propiedades, haga doble clic en la regla y seleccione **propiedades**, o seleccione la regla y, a continuación, presione **Alt**+**ENTRAR**.

![Propiedades de diagnóstico en la ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea para obtener un diagnóstico, haga doble clic en el diagnóstico y seleccione **ver Ayuda**.

Los iconos junto a cada diagnóstico en **el Explorador de soluciones** corresponden a los iconos que ve en el conjunto al abrirlo en el editor de reglas:

- la "i" en un círculo indica un [gravedad](#rule-severity) de **Info**
- el "!" en un triángulo indica un [gravedad](#rule-severity) de **advertencia**
- la "x" en un círculo indica un [gravedad](#rule-severity) de **Error**
- la "i" en un círculo sobre un fondo de color claro indica un [gravedad](#rule-severity) de **Hidden**
- la flecha hacia abajo en un círculo indica que se suprime el diagnóstico

![Iconos de diagnóstico en el Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Conjuntos de reglas

Un [conjunto de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) es un archivo XML que almacena el estado de gravedad y la supresión para el diagnóstico individual.

> [!NOTE]
> Conjuntos de reglas pueden incluir reglas de análisis estático de código (binario) y los analizadores de Roslyn.

Para editar la regla activa establecida en el editor de conjunto de reglas, haga doble clic en el **referencias** > **analizadores** nodo **el Explorador de soluciones** y seleccione **Abrir el conjunto de reglas activo**. Si es la primera vez que se está editando el conjunto de reglas, Visual Studio realiza una copia de la regla predeterminada de archivo de conjunto, lo denomina  *\<NombreDelProyecto > .ruleset*y lo agrega al proyecto. Esta regla personalizada conjunto también se convierte en la regla activa establecida para el proyecto.

Para cambiar la regla activa establecida para un proyecto, vaya a la **análisis de código** ficha de propiedades de un proyecto. Seleccione el conjunto de reglas de la lista bajo **ejecutar este conjunto de reglas**. Para abrir el conjunto de reglas, seleccione **abrir**.

> [!NOTE]
> Los proyectos de .NET core y .NET Standard no admiten los comandos de menú para conjuntos de reglas **el Explorador de soluciones**, por ejemplo, **Abrir conjunto de reglas activo**. Para especificar una regla no predeterminado establecida para un proyecto .NET Core o .NET Standard, manualmente [agregar el **CodeAnalysisRuleSet** propiedad](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) al archivo de proyecto. Puede configurar las reglas incluidas en el conjunto de reglas en Visual Studio UI del editor de conjunto de reglas.

## <a name="rule-severity"></a>Gravedad de las reglas

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, si se [instalar los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet. En la siguiente tabla muestra las opciones de gravedad para el diagnóstico:

|Gravedad|Comportamiento en tiempo de compilación|Comportamiento del Editor|
|-|-|-|
|Error|Las infracciones aparezcan como *errores* en el **lista de errores** en línea de comandos resultados de compilación y hacer que las compilaciones de un error.|Código que provoca el error aparece subrayado con una roja ondulada y marcada por un pequeño cuadro rojo en la barra de desplazamiento.|
|Advertencia|Las infracciones aparezcan como *advertencias* en el **lista de errores** y en línea de comandos salida de la compilación, pero no se producirá un error en las compilaciones.|Código que provoca el error aparece subrayado con color verde ondulada y marcado por un pequeño cuadro verde en la barra de desplazamiento.|
|Info|Las infracciones aparezcan como *mensajes* en el **lista de errores**y no en absoluto en la salida de la compilación de línea de comandos.|Código que provoca el error aparece subrayado con un gris ondulado y marcado por un pequeño cuadro gris en la barra de desplazamiento.|
|Hidden|No visibles al usuario.|No visibles al usuario. El diagnóstico se notifica al motor de diagnóstico de IDE, sin embargo.|
|Ninguna|Suprimir completamente.|Suprimir completamente.|

Además, puede "Restablecer" gravedad de una regla si se establece en **predeterminado**. Cada diagnóstico tiene una gravedad predeterminada que se puede ver en el **propiedades** ventana.

Captura de pantalla siguiente muestra tres infracciones de diagnóstico diferentes en el editor de código, con tres niveles de gravedad diferentes. Tenga en cuenta el color de la línea ondulada, así como el pequeño cuadro en la barra de desplazamiento a la derecha.

![Infracción de error, advertencia e información en el editor de código](media/diagnostics-severity-colors.png)

Captura de pantalla siguiente muestra las infracciones de tres mismas tal y como aparecen en la **lista de errores**:

![Infracción de error, advertencia e información en la lista de errores](media/diagnostics-severities-in-error-list.png)

Puede cambiar la gravedad de una regla de **el Explorador de soluciones**, o dentro del  *\<NombreDelProyecto > .ruleset* archivo que se agrega a la solución después de cambiar la gravedad de una regla en  **El Explorador de soluciones**.

![Archivo de conjunto de reglas en el Explorador de soluciones](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Gravedad del conjunto de reglas desde el Explorador de soluciones

1. En **el Explorador de soluciones**, expanda **referencias** > **analizadores** (**dependencias**  >  **Analizadores** para proyectos de .NET Core).

1. Expanda el ensamblado que contiene la regla que desea establecer gravedad para.

1. Haga doble clic en la regla y seleccione **establecer gravedad del conjunto de reglas**. En el menú emergente, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Gravedad del conjunto de reglas en el archivo de conjunto de reglas

1. Abrir el [conjunto de reglas](analyzer-rule-sets.md) archivo haciendo doble clic en él en **el Explorador de soluciones**, seleccione **Abrir conjunto de reglas activo** en el menú contextual de la **analizadores** nodo, o bien seleccionando **abierto** en el **análisis de código** página de propiedades del proyecto.

1. Vaya a la regla expandiendo el ensamblado que lo contiene.

1. En el **acción** columna, seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir las infracciones

Hay varias maneras de suprimir las infracciones de reglas:

- Desde el **analizar** menú

   Seleccione **analizar** > **ejecutar análisis de código y suprimir problemas activos** en la barra de menús para suprimir todas las infracciones actuales. Esto se conoce a veces como "línea de base".

- Desde **el Explorador de soluciones**

   Para suprimir una infracción en **el Explorador de soluciones**, Establece la gravedad de la regla en **ninguno**.

- Desde el **editor de conjunto de reglas**

   Para suprimir una infracción en el editor de conjunto de reglas, desactive la casilla junto a su nombre o establecer **acción** a **ninguno**.

- Desde el **editor de código**

   Para suprimir una infracción del editor de código, coloque el cursor en la línea de código con la infracción y presione **Ctrl**+ **.** Para abrir el **acciones rápidas** menú. Seleccione **Suprimir regla** > **en origen/en el archivo de supresión**.

   ![Suprimir diagnóstico desde el menú Acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Desde el **lista de errores**

   Puede suprimir diagnóstico uno o varios de los **lista de errores** , seleccione los que quiere suprimir, y, a continuación, con el botón secundario y seleccione **suprimir** > **Source/In en Archivo de supresión**.

   - Si se suprimen **en origen**, el **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de la C# [advertencia #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable advertencia](/dotnet/visual-basic/language-reference/directives/directives) directiva que se agrega al código fuente.

      ![Vista previa de la adición de advertencia #pragma de archivo de código](media/pragma-warning-preview.png)

   - Si selecciona **en el archivo de supresión**, **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que se agrega al archivo supresiones globales.

      ![Vista previa de agregar el atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

   En el **vista previa de cambios** cuadro de diálogo, seleccione **aplicar**.

   > [!NOTE]
   > Si no ve el **suprimir** opción de menú en **el Explorador de soluciones**, la infracción es probable que procede de la compilación y el análisis dinámico no. El **lista de errores** muestra diagnósticos o regla infracciones, tanto de análisis de código activo y compilación. Dado que los diagnósticos de compilación pueden ser obsoletos, por ejemplo, si ha editado el código para corregir la infracción, pero aún no vuelve a generar, no puede suprimir estos diagnósticos desde la **lista de errores**. Diagnósticos de análisis dinámico, ni IntelliSense, siempre están actualizados con fuentes actuales y se puede suprimir desde el **lista de errores**. Para excluir *compilar* diagnósticos desde la selección, cambie el **lista de errores** filtro de origen de **compilación + IntelliSense** a **Intellisense solo**. A continuación, seleccione los diagnósticos que desea suprimir y continuar como se describió anteriormente.
   >
   > ![Filtro de origen de la lista de errores en Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Uso de la línea de comandos

Al compilar el proyecto en la línea de comandos, las infracciones de reglas aparecen en la salida de compilación si se cumplen las condiciones siguientes:

- Los analizadores se instalan como un paquete de Nuget y no como una extensión VSIX.

- Se infringen una o varias reglas en el código del proyecto.

- El [gravedad](#rule-severity) de una regla infringida está establecida en **advertencia**, en cuyo caso las infracciones no producir un error en, compilación o **error**, en cuyo caso las infracciones producir un error en compilación.

El nivel de detalle de la salida de compilación no afecta a si se muestran las infracciones de reglas. Incluso con **silencioso** las infracciones de reglas de nivel de detalle, aparecen en la salida de compilación.

> [!TIP]
> Si está acostumbrado a la ejecución de análisis de código estático de la línea de comandos, ya sea con *FxCopCmd.exe* o a través de msbuild con el **RunCodeAnalysis** marca, aquí se muestra cómo hacer que los analizadores de Roslyn.

Para ver las infracciones de analizador en la línea de comandos al compilar el proyecto mediante msbuild, ejecute un comando similar al siguiente:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

La siguiente imagen muestra la salida de compilación de línea de comandos desde la creación de un proyecto que contiene una infracción de regla de analizador:

![Salida de MSBuild con infracción de regla](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Proyectos dependientes

En un proyecto .NET Core, si agrega una referencia a un proyecto que tiene los analizadores de NuGet, los analizadores se agregan automáticamente al proyecto dependiente demasiado. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete de NuGet como privada en el *.csproj* o *.vbproj* archivo del proyecto que se hace referencia mediante el establecimiento del **PrivateAssets** atributo:

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error del analizador de Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)