---
title: Usar y configurar los analizadores de Roslyn en Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6668b3727e5df17c3d436e37f2edd78a67a79eba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204159"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurar y usar las reglas del analizador de Roslyn

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

Un [conjunto de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) es un archivo XML que almacena el estado de gravedad y la supresión para el diagnóstico individual. Conjuntos de reglas se aplican a un proyecto único y un proyecto puede tener varios conjuntos de reglas. Para ver el conjunto en el editor de reglas activas, haga doble clic en el **analizadores** nodo **el Explorador de soluciones** y seleccione **Abrir conjunto de reglas activo**. Si se trata de establecer la primera vez que se tiene acceso a la regla, un archivo denominado  *\<NombreDelProyecto > .ruleset* se agrega al proyecto y aparece en **el Explorador de soluciones**.

> [!NOTE]
> Conjuntos de reglas incluyen análisis estático de código (binario) y las reglas del analizador de Roslyn.

Puede cambiar la regla activa establecida para un proyecto en el **análisis de código** ficha de propiedades de un proyecto. Seleccione el conjunto de reglas en el **ejecutar este conjunto de reglas** lista desplegable. También puede abrir el conjunto de reglas de la **análisis de código** página de propiedades seleccionando **abrir**.

## <a name="rule-severity"></a>Gravedad de regla

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

### <a name="to-set-rule-severity-from-solution-explorer"></a>Para establecer la gravedad de regla desde el Explorador de soluciones

1. En **el Explorador de soluciones**, expanda **referencias** > **analizadores** (**dependencias**  >  **Analizadores** para proyectos de .NET Core).

1. Expanda el ensamblado que contiene la regla que desea establecer gravedad para.

1. Haga doble clic en la regla y seleccione **establecer gravedad del conjunto de reglas**. En el menú emergente, seleccione una de las opciones de gravedad.

   La gravedad de la regla se guarda en el archivo de conjunto de reglas activo.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Para establecer la regla de archivo de conjunto de gravedad de la regla

1. Abrir el conjunto de reglas archivo haga doble clic en **el Explorador de soluciones**, seleccione **Abrir conjunto de reglas activo** en el menú contextual de la **analizadores** nodo, o mediante la selección **Abierto** en el **análisis de código** página de propiedades del proyecto.

1. Vaya a la regla expandiendo el ensamblado que lo contiene.

1. En el **acción** columna, seleccione el valor para abrir una lista desplegable y seleccione la gravedad deseada en la lista.

   ![Archivo de conjunto de reglas abierto en el editor](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Suprimir las infracciones

Hay varias maneras de suprimir las infracciones de reglas:

- Para suprimir todas las infracciones actuales, seleccione **analizar** > **ejecutar análisis de código y suprimir problemas activos** en la barra de menús. Esto se conoce a veces como "línea de base".

- Para suprimir un diagnóstico de **el Explorador de soluciones**, establece su gravedad en **ninguno**.

- Para suprimir un diagnóstico desde el editor de conjunto de reglas, desactive la casilla junto a su nombre o establecer **acción** a **ninguno**.

- Para suprimir un diagnóstico desde el editor de código, coloque el cursor en la línea de código con la infracción y presione **Ctrl**+**.** Para abrir el **acciones rápidas** menú. Seleccione **Suprimir regla** > **en origen** o **Suprimir regla** > **en archivo de supresión**.

   ![Suprimir diagnóstico desde el menú Acciones rápidas](media/suppress-diagnostic-from-editor.png)

- Para suprimir un diagnóstico desde el **lista de errores**, consulte [suprimir las infracciones de la lista de errores](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Suprimir las infracciones de la lista de errores

Puede suprimir diagnóstico uno o varios de los **lista de errores** , seleccione los que quiere suprimir, y, a continuación, con el botón secundario y seleccione **suprimir** > **en origen**  o **suprimir** > **en archivo de supresión**.

   - Si selecciona **en origen**, **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de C# [advertencia #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) o Visual Basic [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives) directiva que se agrega al código fuente.

      ![Vista previa de la adición de advertencia #pragma de archivo de código](media/pragma-warning-preview.png)

   - Si selecciona **en el archivo de supresión**, **vista previa de cambios** cuadro de diálogo se abre y muestra una vista previa de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo que se agrega al archivo supresiones globales.

      ![Vista previa de agregar el atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

   En el **vista previa de cambios** cuadro de diálogo, seleccione **aplicar**.

El **lista de errores** muestra diagnósticos o regla infracciones, tanto de análisis de código activo y compilación. Dado que los diagnósticos de compilación pueden ser obsoletos, por ejemplo, si ha editado el código para corregir la infracción, pero aún no vuelve a generar, no puede suprimir estos diagnósticos desde la **lista de errores**. Sin embargo, diagnósticos de análisis dinámico, ni IntelliSense, siempre están actualizados con orígenes actuales y se puede suprimir desde el **lista de errores**. Si se deshabilita la opción de supresión en el menú contextual o contexto, es probable porque tiene uno o más diagnósticos en la selección de compilación. Para excluir los diagnósticos de la compilación de la selección, cambie el **lista de errores** filtro de origen de **compilación + IntelliSense** a **Intellisense solo**. A continuación, seleccione los diagnósticos que desea suprimir y continuar como se describió anteriormente.

![Filtro de origen de la lista de errores en Visual Studio](media/error-list-filter.png)

> [!NOTE]
> En un proyecto .NET Core, si agrega una referencia a un proyecto que tiene los analizadores de NuGet, los analizadores se agregan automáticamente al proyecto dependiente demasiado. Para deshabilitar este comportamiento, por ejemplo, si el proyecto dependiente es un proyecto de prueba unitaria, marque el paquete de NuGet como privada en el *.csproj* o *.vbproj* archivo del proyecto que se hace referencia:
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn en Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Enviar un error del analizador de Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Usar conjuntos de reglas](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Suprimir advertencias de análisis de código](../code-quality/in-source-suppression-overview.md)