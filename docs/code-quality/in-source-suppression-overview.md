---
title: Suprimir advertencias de análisis de código en Visual Studio
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 7fe91532c3b4e020541f5f96152253f1df673ded
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117789"
---
# <a name="suppress-code-analysis-warnings"></a>Suprimir advertencias de análisis de código

A menudo resulta útil indicar que una advertencia no es aplicable. Esto indica a los miembros del equipo que se ha revisado el código y que se puede suprimir la advertencia. Usos de supresión (ISS) en el origen del <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo para suprimir una advertencia. El atributo puede colocarse cerca de segmento de código que genera la advertencia. Puede agregar el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo al archivo de origen escribiendo, o bien puede usar el menú contextual en una advertencia en el **lista de errores** para agregarlo automáticamente.

El <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> es un atributo condicional que se incluye en los metadatos de IL del ensamblado de código administrado, solo si se ha definido el símbolo de compilación CODE_ANALYSIS en tiempo de compilación.

En C++ / c++ / CLI, use las macros CA\_suprimir\_mensaje o CA\_GLOBAL\_SUPPRESS_MESSAGE en el archivo de encabezado para agregar el atributo.

> [!NOTE]
> No debe utilizar supresiones en código fuente en las compilaciones de versión para evitar que los metadatos de supresión en el origen de trasvase de registros por accidente. Además, debido al costo de procesamiento de supresión en el código fuente, puede disminuir el rendimiento de la aplicación.

> [!NOTE]
> Si migra un proyecto de Visual Studio 2017, podría encontrarse, de repente, con un número excesivo de las advertencias de análisis de código. Si no está listo para solucionar las advertencias y desee desactivar temporalmente el análisis de código, abra páginas de propiedades del proyecto (**proyecto** > **\<proyecto > propiedades**) y vaya a el **análisis de código** ficha. Anule la selección de **Habilitar análisis de código al compilar**y, a continuación, recompile el proyecto. Como alternativa, puede seleccionar un conjunto para ejecutarla en el código de reglas diferentes, más pequeño. No olvide activar el análisis de código activarlo cuando esté preparado para solucionar las advertencias.

## <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)

Cuando se elige **suprimir** desde el menú contextual de una advertencia de análisis de código en el **lista de errores**, un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se agrega un atributo en el código o a la supresión global del proyecto archivo.

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

- **Categoría de regla** -la categoría en la que se define la regla. Para obtener más información acerca de las categorías de regla de análisis de código, vea [administra las advertencias de código](../code-quality/code-analysis-for-managed-code-warnings.md).

- **Id. de regla** -el identificador de la regla. La compatibilidad incluye tanto un nombre corto y largo para el identificador de regla. El nombre corto es la regla. el nombre corto es CAXXXX.

- **Justificación** -el texto que se usa para documentar el motivo para suprimir el mensaje.

- **Id. de mensaje** -identificador único de un problema para cada mensaje.

- **Ámbito** -el destino en el que se suprime la advertencia. Si el destino no se especifica, se establece en el destino del atributo. Los ámbitos admitidos incluyen lo siguiente:

    - Module

    - Espacio de nombres

    - Recurso

    - Tipo

    - Miembro

- **Destino** : un identificador que se usa para especificar el destino en el que se suprime la advertencia. Debe contener un nombre de elemento completo.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Se suprimen las advertencias de análisis de código en el nivel al que el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se aplica el atributo. Por ejemplo, el atributo puede aplicarse al ensamblado, módulo, tipo, miembro o parámetro. El propósito de esto es acoplando la información de supresión en el código donde se produce la infracción.

La forma general de supresión incluye la categoría de regla y un identificador de regla, que contiene una representación legible opcional del nombre de la regla. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Si hay razones de rendimiento estricta para minimizar los metadatos de supresión en el código fuente, se puede omitir el nombre de la regla. La categoría de regla y el identificador de regla constituyen en conjunto un identificador de regla lo suficientemente exclusivos. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Por razones de mantenimiento, no se recomienda si se omite el nombre de la regla.

## <a name="suppress-selective-violations-within-a-method-body"></a>Suprimir selectivas infracciones dentro de un cuerpo de método

Atributos de supresión se pueden aplicar a un método, pero no se puede incrustar dentro de un cuerpo de método. Esto significa que todas las infracciones de una regla determinada se han suprimido si agrega el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> al método.

En algunos casos, es posible que desea suprimir una instancia determinada de la infracción, por ejemplo, para que el código futuro no está exento de automáticamente de la regla de análisis de código. Ciertas reglas de análisis de código le permiten hacer esto mediante el uso de la `MessageId` propiedad de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. En general, las reglas heredado para las infracciones en el respeto de un símbolo concreto (un parámetro o variable local) el `MessageId` propiedad. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) es un ejemplo de este tipo de regla. Sin embargo, las reglas heredadas de infracciones en el código ejecutable (no de símbolos) no respetan el `MessageId` propiedad. Además, los analizadores de .NET Compiler Platform («Roslyn») no respetan el `MessageId` propiedad.

Para suprimir una infracción de símbolo concreto de una regla, especifique el nombre del símbolo para el `MessageId` propiedad de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. El ejemplo siguiente muestra el código con dos infracciones de [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;uno para el `name` variable y otra para el `age` variable. Solo la infracción de la `age` se suprime el símbolo.

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

## <a name="generated-code"></a>Código generado

Los compiladores de código administrado y algunas herramientas de otros fabricantes generan código para facilitar el desarrollo rápido de código. Código generado por el compilador que aparece en los archivos de código fuente normalmente está marcado con el `GeneratedCodeAttribute` atributo.

Puede elegir si se debe suprimir las advertencias de análisis de código y los errores de código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, vea [Cómo: Suprimir advertencias de código generado](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Análisis de código omite `GeneratedCodeAttribute` cuando se aplica a todo el ensamblado o un parámetro único.

## <a name="global-level-suppressions"></a>Supresiones de nivel global

La herramienta de análisis de código administrado examina `SuppressMessage` atributos que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También se desencadena las infracciones contra los recursos y los espacios de nombres. Estas infracciones deben aplicarse en el nivel global y son ámbito y de destino. Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Al suprimir una advertencia con ámbito de espacio de nombres, se suprime la advertencia en el espacio de nombres. No se suprime la advertencia contra los tipos del espacio de nombres.

Cualquier supresión se puede expresar mediante la especificación de un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro mediante la decoración de un tipo.

Las supresiones de nivel global son la única manera para suprimir los mensajes que hacen referencia al código generado por el compilador que no se asigna a la fuente de usuario proporcionado explícitamente. Por ejemplo, el código siguiente suprime la infracción contra un constructor emitido por el compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` siempre contiene el nombre del elemento completo.

## <a name="global-suppression-file"></a>Archivo de supresión global

El archivo de supresión global mantiene supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, las supresiones de infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque no está disponibles para el código detrás de un formulario de configuración de nivel de proyecto. Se crea un archivo de supresión global y se agrega al proyecto la primera vez que seleccione el **en el archivo de supresión del proyecto** opción de la **suprimir** comando en el **lista de errores**ventana.

## <a name="see-also"></a>Vea también

- <xref:System.Diagnostics.CodeAnalysis>
- [Usar analizadores de Roslyn](../code-quality/use-roslyn-analyzers.md)