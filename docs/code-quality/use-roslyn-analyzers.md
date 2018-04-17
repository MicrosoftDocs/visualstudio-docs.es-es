---
title: Usar y configurar los analizadores de Roslyn en Visual Studio | Documentos de Microsoft
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 17758b8cd901a03e2ce4f93fe5dfcfdbe97eadab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurar y usar las reglas del analizador Roslyn

Reglas del analizador de .NET compiler Platform («Roslyn»), o *diagnósticos*, analizar el código de C# o Visual Basic a medida que escribe. Cada diagnóstico tiene un estado de gravedad y supresión de predeterminada que se puede sobrescribir para el proyecto. Este artículo tratan gravedad de regla de configuración, usar conjuntos de reglas y suprimir infracciones.

## <a name="analyzers-in-solution-explorer"></a>Analizadores de en el Explorador de soluciones

Puede realizar gran parte de la personalización de diagnósticos de analizador de **el Explorador de soluciones**. Si se [instalar analizadores de](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet, un **analizadores** nodo aparece en el **referencias** o **dependencias** nodo  **El Explorador de soluciones**. Si expande **analizadores**y, a continuación, expanda uno de los ensamblados de analizador, verá todos los diagnósticos en el ensamblado.

![Nodo de analizadores en el Explorador de soluciones](media/analyzers-expanded-in-solution-explorer.png)

Puede ver las propiedades de un diagnóstico, incluida su descripción y la gravedad de manera predeterminada, en la **propiedades** ventana. Para ver las propiedades, haga doble clic en la regla y seleccione **propiedades**, o seleccione la regla y, a continuación, presione **Alt**+**ENTRAR**.

![Propiedades de diagnóstico en la ventana Propiedades](media/analyzer-diagnostic-properties.png)

Para ver la documentación en línea para obtener un diagnóstico, haga doble clic en el diagnóstico y seleccione **ver Ayuda**.

Los iconos junto a cada diagnóstico en **el Explorador de soluciones** corresponden a los iconos que se ven en el conjunto al abrirlo en el editor de reglas:

- la "i" en un círculo indica un [gravedad](#rule-severity) de **información**
- el "!" en un triángulo indica un [gravedad](#rule-severity) de **advertencia**
- la "x" en un círculo indica un [gravedad](#rule-severity) de **Error**
- la "i" en un círculo sobre un fondo de color claro indica un [gravedad](#rule-severity) de **Hidden**
- la flecha hacia abajo en un círculo indica que se suprime el diagnóstico

![Iconos de diagnóstico en el Explorador de soluciones](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Conjuntos de reglas

A [conjunto de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) es un archivo XML que almacena el estado de gravedad y supresión para el diagnóstico individual. Conjuntos de reglas se aplican a un proyecto único, y un proyecto puede tener varios conjuntos de reglas. Para ver el conjunto en el editor de reglas activo, haga doble clic en el **analizadores** nodo **el Explorador de soluciones** y seleccione **Abrir conjunto de reglas Active**. Si se trata de establecer la primera vez que se tiene acceso a la regla, un archivo denominado  *\<NombreDeProyecto > .ruleset* se agrega al proyecto y aparece en **el Explorador de soluciones**.

> [!NOTE]
> Conjuntos de reglas incluyen análisis de código estático de (binario) y las reglas del analizador de Roslyn.

Puede cambiar la active conjunto de reglas para un proyecto en el **análisis de código** ficha de propiedades del proyecto. Seleccione el conjunto de reglas en la **ejecutar este conjunto de reglas** lista desplegable. También puede abrir el conjunto de reglas de la **análisis de código** página de propiedades seleccionando **abrir**.

## <a name="rule-severity"></a>Gravedad de regla

Puede configurar la gravedad de las reglas del analizador, o *diagnósticos*, si se [instalar los analizadores](../code-quality/install-roslyn-analyzers.md) como un paquete de NuGet. La siguiente tabla muestra las opciones de gravedad para el diagnóstico:

|Gravedad|Comportamiento en tiempo de compilación|Comportamiento del Editor|
|-|-|-|
|Error|Infracciones aparecen como *errores* en el **lista de errores** y en línea de comandos resultado de la compilación y que las compilaciones y producirá un error.|El código es subrayado con una roja ondulada y marcada por un pequeño cuadro rojo en la barra de desplazamiento.|
|Advertencia|Infracciones aparecen como *advertencias* en el **lista de errores** y en línea de comandos resultado de la compilación, pero no hacen que las compilaciones y producirá un error.|El código es subrayado con una de color verde ondulada y marcada por un pequeño cuadro verde en la barra de desplazamiento.|
|Info|Infracciones aparecen como *mensajes* en el **lista de errores**y no en absoluto en los resultados de la compilación de línea de comandos.|El código es subrayado con un color gris ondulado y marcado por un pequeño cuadro gris en la barra de desplazamiento.|
|Hidden|No visible al usuario.|No visible al usuario. El diagnóstico se notifica al motor de diagnóstico de IDE, sin embargo.|
|Ninguna|Suprimido por completo.|Suprimido por completo.|

Además, puede "Restablecer" gravedad de una regla si se establece en **predeterminado**. Cada diagnóstico tiene una gravedad predeterminada que se pueden ver en la **propiedades** ventana.

Captura de pantalla siguiente muestra tres infracciones de diagnóstico diferentes en el editor de código, con tres niveles de gravedad diferentes. Tenga en cuenta el color de la onduladas, así como el pequeño cuadro en la barra de desplazamiento a la derecha.

![Infracción de error, advertencia e información en el editor de código](media/diagnostics-severity-colors.png)

Captura de pantalla siguiente muestra las infracciones de tres mismas tal y como aparecen en la **lista de errores**:

![Infracción de error, advertencia e información en la lista de errores](media/diagnostics-severities-in-error-list.png)

Puede cambiar la gravedad de una regla de **el Explorador de soluciones**, o en la  *\<NombreDeProyecto > .ruleset* archivo que se agrega a la solución después de cambiar la gravedad de una regla en  **El Explorador de soluciones**.

![Archivo de conjunto de reglas en el Explorador de soluciones](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Para establecer la gravedad de la regla desde el Explorador de soluciones

1. En **el Explorador de soluciones**, expanda **referencias** > **analizadores** (**dependencias**  >  **Analizadores** para los proyectos de .NET Core).

1. Expanda el ensamblado que contiene la regla que desea establecer la gravedad para.

1. Haga doble clic en la regla y seleccione **establecer regla establecer gravedad**. En el menú emergente, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Para establecer la regla de gravedad de la regla establece archivo

1. Abra el conjunto de reglas archivo haga doble clic en **el Explorador de soluciones**, seleccione **Abrir conjunto de reglas activo** en el menú contextual de la **analizadores** nodo, o mediante la selección **Abiertos** en el **análisis de código** página de propiedades para el proyecto.

1. Vaya a la regla expandiendo el ensamblado que lo contiene.

1. En el **acción** columna, seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseados de la lista.

   ![Conjunto de reglas archivo abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir las infracciones

Hay varias maneras para suprimir las infracciones de reglas:

- Para suprimir todas las infracciones del actuales, seleccione **analizar** > **ejecutar análisis de código y suprimir problemas activos** en la barra de menús. Esto se conoce a veces como "línea de base".

- Para suprimir un diagnóstico de **el Explorador de soluciones**, establecer su gravedad **ninguno**.

- Para suprimir un diagnóstico desde el editor de conjunto de reglas, desactive la casilla situada junto a su nombre o establecer **acción** a **ninguno**.

- Para suprimir un diagnóstico desde el editor de código, coloque el cursor en la línea de código con la infracción y presione **Ctrl**+**.** Para abrir el **acciones rápidas** menú. Seleccione **Suprimir regla** > **en origen** o **Suprimir regla** > **en archivo de supresión**.

   ![Suprimir diagnóstico en el menú de acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Para suprimir un diagnóstico de la **lista de errores**, haga doble clic en el error, advertencia o mensaje y seleccione **suprimir** > **en origen** o **Suprimir** > **en archivo de supresión**.

   - Si selecciona **en origen**, **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de C# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable advertencia](/dotnet/visual-basic/language-reference/directives/directives) directiva que se agrega al código fuente.

      ![Vista previa de adición de advertencia #pragma en archivo de código](media/pragma-warning-preview.png)

   - Si selecciona **en el archivo de supresión**, **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que se agrega al archivo de supresiones global.

      ![Vista previa de cómo agregar SuppressMessage (atributo) al archivo de supresión](media/preview-changes-in-suppression-file.png)

   En el **vista previa de cambios** cuadro de diálogo, seleccione **aplicar**.

> [!NOTE]
> En un proyecto de .NET Core, si agrega una referencia a un proyecto que tiene los analizadores de NuGet, los analizadores de se agregan automáticamente al proyecto dependiente demasiado. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete de NuGet como privada en el *.csproj* o *.vbproj* archivo del proyecto que se hace referencia:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error de analizador Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)