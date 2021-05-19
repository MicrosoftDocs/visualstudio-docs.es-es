---
title: Supresión de infracciones de análisis de código
ms.date: 05/10/2021
description: Obtenga información sobre cómo suprimir las infracciones de análisis de código en Visual Studio. Comprenda cómo usar el atributo SuppressMessageAttribute para la supresión en el origen.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973348"
---
# <a name="suppress-code-analysis-violations"></a>Supresión de infracciones de análisis de código

A menudo resulta útil indicar que una advertencia no es aplicable. Esto indica a los miembros del equipo que se ha revisado el código y que se puede suprimir la advertencia. En este artículo se describen las distintas formas de suprimir las infracciones de análisis de código mediante Visual Studio IDE.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>Supresión de infracciones mediante el archivo EditorConfig

En un **archivo EditorConfig**, establezca la gravedad en `none` , por ejemplo, `dotnet_diagnostic.CA1822.severity = none` . Para agregar un archivo EditorConfig, vea [Agregar un archivo EditorConfig a un proyecto.](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files)

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Supresión de infracciones en el código fuente

Puede suprimir las infracciones en el código mediante una directiva de preprocesador, la directiva [#pragma warning (C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) o [Disable (Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) para suprimir la advertencia solo para una línea de código específica. O bien, puede usar el [atributo SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- Desde el **editor de código**

  Coloque el cursor en la línea de código con la infracción y presione **Ctrl** + **Período (.) para** abrir el menú **Acciones** rápidas. Seleccione **Suprimir CAXXXX** y, a continuación, elija **en Origen** o en Origen **(atributo).**

  Si elige en **Origen,** verá una vista previa de la directiva de preprocesador que se agregará al código.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Suprimir el diagnóstico del menú de acciones rápidas":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Suprimir el diagnóstico del menú de acciones rápidas":::

  Si elige en **Origen (atributo),** verá una vista previa del atributo [SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute) que se agregará al código.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Suprimir el diagnóstico del menú de acciones rápidas mediante el atributo":::
  ::: moniker-end

- En la lista **de errores**

  Seleccione las reglas que desea suprimir y, a continuación, haga clic con el botón derecho y **seleccione Suprimir en**  >  **origen.**

  - Si suprime En  el origen **,** se abre el cuadro de diálogo Vista previa de los cambios y se muestra una vista previa de la directiva de advertencia de [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) de C# o Visual Basic [#Disable](/dotnet/visual-basic/language-reference/directives/directives) que se agrega al código fuente.

    ![Vista previa de la adición #pragma advertencia en el archivo de código](media/pragma-warning-preview.png)

  En el cuadro **de diálogo Vista** previa de cambios, seleccione **Aplicar**.

  > [!NOTE]
  > Si no ve la  opción de menú Suprimir en Explorador de soluciones , **es** probable que la infracción se deba a la compilación y no al análisis en directo. La **lista de errores** muestra diagnósticos, o infracciones de reglas, tanto del análisis de código en directo como de la compilación. Puesto que los diagnósticos de compilación pueden estar obsoletos, por ejemplo, si ha editado el código para corregir la infracción pero no se ha recompilado, no puede suprimir estos diagnósticos de la lista **de errores**. Los diagnósticos de análisis en directo, o IntelliSense, siempre están actualizados con los orígenes actuales y se pueden suprimir de la **lista de errores**. Para excluir *diagnósticos* de compilación de la selección, cambie el filtro de origen **Lista** de errores de **Compilación + IntelliSense** a **Solo IntelliSense.** A continuación, seleccione los diagnósticos que desea suprimir y continúe como se describió anteriormente.
  >
  > ![Filtro de origen lista de errores en Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Supresión de infracciones mediante un archivo de supresión global

El [archivo de supresión global](#global-level-suppressions) usa el atributo [SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- En la **lista de errores**, seleccione las reglas que desea suprimir y, a continuación, haga clic con el botón derecho y seleccione Suprimir **en** archivo de  >  **supresión**. Se **abre el cuadro de** diálogo Vista previa de cambios y se muestra una vista previa del atributo que se agrega al archivo de <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> supresiones globales.

  ![Vista previa de la adición del atributo SuppressMessage al archivo de supresión](media/preview-changes-in-suppression-file.png)

- En el **editor** de código , coloque el cursor en la línea de código con la infracción y presione Acciones rápidas y refactorizaciones (o presione **Ctrl** Período (.) ) para abrir el menú Acciones  + rápidas.  Seleccione **Suprimir CAXXXX** y, a continuación, elija **en Archivo de supresión**. Verá una vista previa del archivo [de supresión global](#global-level-suppressions) que se creará o modificará.

::: moniker range=">=vs-2019"

- En el **menú Analizar,** seleccione **Analizar compilación** y suprimir problemas activos en la barra de  >   menús para suprimir todas las infracciones actuales. Esto se conoce a veces como "baselining".

::: moniker-end
::: moniker range="vs-2017"

- En el **menú Analizar,** seleccione **Analizar** ejecución Code Analysis Suprimir problemas activos en la barra de menús para suprimir  >   todas las infracciones actuales. Esto se conoce a veces como "baselining".
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Supresión de infracciones mediante la configuración del proyecto

Desde **Explorador de soluciones**, abra las propiedades del proyecto (haga clic con el botón derecho en el proyecto y elija Propiedades **(o** presione Alt **+ Entrar)** y use la pestaña Code Analysis **para** configurar las opciones. Por ejemplo, puede deshabilitar el análisis de código en directo o deshabilitar los analizadores de .NET.

## <a name="suppress-violations-using-a-rule-set"></a>Supresión de infracciones mediante un conjunto de reglas

En el **editor de conjunto de reglas**, desactive la casilla situada junto a su nombre o establezca **Acción** en **Ninguno.**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Supresión en el origen y el atributo SuppressMessage

La supresión en el origen (ISS) usa el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo para suprimir una advertencia. El atributo se puede colocar cerca del segmento de código que generó la advertencia. Puede agregar el atributo al archivo de código fuente si lo escribe o puede usar el menú contextual de una advertencia en la lista de errores para <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> agregarlo automáticamente. 

El atributo es un atributo condicional, que se incluye en los metadatos de IL del ensamblado de código administrado, solo si el símbolo de compilación CODE_ANALYSIS se define en tiempo <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> de compilación.

En C++/CLI, use las macros CA SUPPRESS MESSAGE o CA GLOBAL SUPPRESS_MESSAGE en el archivo de encabezado \_ \_ para agregar el \_ \_ atributo.

> [!NOTE]
> No debe usar supresiones en el origen en las compilaciones de versión para evitar el envío accidental de los metadatos de supresión en el origen. Además, debido al costo de procesamiento de la supresión en el origen, el rendimiento de la aplicación se puede degradar.

::: moniker range="vs-2017"

> [!NOTE]
> Si migra un proyecto a Visual Studio 2017, podría encontrarse repentinamente con un gran número de advertencias de análisis de código. Si no está listo para corregir las advertencias, puede suprimirlas todas seleccionando Analizar ejecución Code Analysis Suprimir   >  **problemas activos**.
>
> ![Ejecutar análisis de código y suprimir problemas en Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Si migra un proyecto a Visual Studio 2019, podría encontrarse repentinamente con un gran número de advertencias de análisis de código. Si no está listo para corregir las advertencias, puede suprimirlas todas seleccionando Analizar la compilación y suprimir   >  **problemas activos.**

::: moniker-end

### <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)

Al seleccionar  Suprimir en el menú contextual o en el menú contextual de una advertencia de análisis de código en la lista de errores **,** se agrega un atributo en el código o en el archivo de supresión global <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> del proyecto.

El <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo tiene el formato siguiente:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Las propiedades del atributo incluyen:

- **Categoría:** categoría en la que se define la regla. Para obtener más información sobre las categorías de reglas de análisis de código, vea [Advertencias de código administrado.](/dotnet/fundamentals/code-analysis/quality-rules/index)

- **CheckId:** identificador de la regla. La compatibilidad incluye un nombre corto y largo para el identificador de regla. El nombre corto es CAXXXX; el nombre largo es CAXXXX:FriendlyTypeName.

- **Justificación:** texto que se usa para documentar el motivo para suprimir el mensaje.

- **MessageId:** identificador único de un problema para cada mensaje.

- **Ámbito:** el destino en el que se suprime la advertencia. Si no se especifica el destino, se establece en el destino del atributo . Entre [los ámbitos admitidos](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) se incluyen los siguientes:

  - [`module`](#module-suppression-scope) : este ámbito suprime las advertencias en un ensamblado. Es una supresión global que se aplica a todo el proyecto.

  - `resource` -[(solo FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) heredado) Este ámbito suprime las advertencias en la información de diagnóstico escrita en los archivos de recursos que forman parte del módulo (ensamblado). Este ámbito no se lee ni respeta en los compiladores de C#/VB para el diagnóstico del analizador de Roslyn, que solo analiza los archivos de código fuente.

  - `type` : este ámbito suprime las advertencias en un tipo.

  - `member` : este ámbito suprime las advertencias en un miembro.

  - `namespace` : este ámbito suprime las advertencias en el propio espacio de nombres. No suprime las advertencias en los tipos del espacio de nombres .

  - `namespaceanddescendants` - (Requiere la versión del compilador 3.x o superior y Visual Studio 2019) Este ámbito suprime las advertencias en un espacio de nombres y todos sus símbolos descendientes. El `namespaceanddescendants` análisis heredado omite el valor.

- **Destino:** identificador que se usa para especificar el destino en el que se suprime la advertencia. Debe contener un nombre de elemento completo.

Cuando vea advertencias en Visual Studio, puede ver ejemplos de agregando una supresión `SuppressMessage` [al archivo de supresión global](../code-quality/use-roslyn-analyzers.md#suppress-violations). El atributo de supresión y sus propiedades necesarias aparecen en una ventana de vista previa.

### <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Code Analysis advertencias se suprimen en el nivel al que <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se aplica el atributo. Por ejemplo, el atributo se puede aplicar en el nivel de ensamblado, módulo, tipo, miembro o parámetro. El propósito de esto es une estrechamente la información de supresión al código donde se produce la infracción.

La forma general de supresión incluye la categoría de regla y un identificador de regla, que contiene una representación legible opcional del nombre de la regla. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Si hay razones de rendimiento estrictas para minimizar los metadatos de supresión en el origen, se puede omitir el nombre de la regla. La categoría de regla y su identificador de regla constituyen juntos un identificador de regla lo suficientemente único. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Por motivos de mantenimiento, no se recomienda omitir el nombre de la regla.

### <a name="suppress-selective-violations-within-a-method-body"></a>Suprimir infracciones selectivas dentro de un cuerpo de método

Los atributos de supresión se pueden aplicar a un método, pero no se pueden incrustar dentro de un cuerpo del método. Esto significa que todas las infracciones de una regla determinada se suprimen si agrega <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> el atributo al método .

En algunos casos, es posible que quiera suprimir una instancia determinada de la infracción, por ejemplo, para que el código futuro no esté exento automáticamente de la regla de análisis de código. Ciertas reglas de análisis de código permiten hacerlo mediante la `MessageId` propiedad del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo . En general, las reglas heredadas para infracciones en un símbolo determinado (una variable o parámetro local) respetan la `MessageId` propiedad . [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) es un ejemplo de esta regla. Sin embargo, las reglas heredadas para infracciones en código ejecutable (no símbolo) no respetan la `MessageId` propiedad . Además, .NET Compiler Platform analizadores ("Roslyn") no respetan la `MessageId` propiedad .

Para suprimir una infracción de símbolo determinada de una regla, especifique el nombre del símbolo para `MessageId` la propiedad del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. En el ejemplo siguiente se muestra código con dos infracciones de [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)una para la variable y otra &mdash; para la `name` `age` variable. Solo se suprime la `age` infracción del símbolo.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

### <a name="global-level-suppressions"></a>Supresiones de nivel global

La herramienta de análisis de código administrado examina los atributos que se aplican en el nivel `SuppressMessage` de ensamblado, módulo, tipo, miembro o parámetro. También se infringen los recursos y los espacios de nombres. Estas infracciones deben aplicarse en el nivel global y tienen como ámbito y destino. Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Cuando se suprime una advertencia con `namespace` ámbito, suprime la advertencia en el propio espacio de nombres. No suprime la advertencia en los tipos del espacio de nombres .

Cualquier supresión se puede expresar especificando un ámbito explícito. Estas supresiones deben estar en el nivel global. No se puede especificar la supresión de nivel de miembro si se decora un tipo.

Las supresiones de nivel global son la única manera de suprimir los mensajes que hacen referencia al código generado por el compilador que no se asigna al origen de usuario proporcionado explícitamente. Por ejemplo, el siguiente código suprime una infracción en un constructor emitido por el compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` siempre contiene el nombre completo del elemento.

#### <a name="global-suppression-file"></a>Archivo de supresión global

El archivo de supresión global mantiene supresiones que son supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, las supresiones de infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones ASP.NET se almacenan en este archivo porque la configuración de nivel de proyecto no está disponible para el código subyacente a un formulario. Se crea un archivo de supresión global y se  agrega al proyecto la  primera vez que se selecciona la opción En archivo de supresión de proyectos del comando Suprimir en la ventana **Lista de** errores.

#### <a name="module-suppression-scope"></a>Ámbito de supresión de módulos

Puede suprimir las infracciones de calidad del código para todo el ensamblado mediante el ámbito **del** módulo.

Por ejemplo, el siguiente atributo en el archivo de proyecto _GlobalSuppressions_ suprimirá la infracción configureWait de un proyecto ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Código generado

Los compiladores de código administrado y algunas herramientas de terceros generan código para facilitar el desarrollo rápido del código. El código generado por el compilador que aparece en los archivos de código fuente normalmente se marca con el `GeneratedCodeAttribute` atributo .

Para el análisis de código fuente, puede suprimir los mensajes en el código generado en un `.editorconfig` archivo. Para obtener más información, vea [Excluir código generado.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Para el análisis de código heredado, puede elegir si desea suprimir advertencias y errores de análisis de código para el código generado. Para obtener información sobre cómo suprimir tales advertencias y errores, vea Cómo: Suprimir [advertencias para código generado.](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)

> [!NOTE]
> El análisis de `GeneratedCodeAttribute` código omite cuando se aplica a un ensamblado completo o a un único parámetro.

## <a name="see-also"></a>Consulte también

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Uso de analizadores de código](../code-quality/use-roslyn-analyzers.md)
