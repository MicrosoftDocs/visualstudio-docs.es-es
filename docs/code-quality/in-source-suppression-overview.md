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
ms.openlocfilehash: aec11e54547f05e3ac7babae29e0c95737bc725e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924423"
---
# <a name="suppress-code-analysis-warnings"></a>Suprimir advertencias de análisis de código

A menudo resulta útil indicar que una advertencia no es aplicable. Esto indica a los miembros del equipo que se ha revisado el código y que se puede suprimir la advertencia. En el código fuente (ISS) de supresión utiliza el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo para suprimir una advertencia. El atributo puede colocarse cerca el segmento de código que genera la advertencia. Puede agregar el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> de atributo para el archivo de origen escribiendo, o puede usar el menú contextual en una advertencia en el **lista de errores** para agregarlo automáticamente.

El <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> es un atributo condicional que se incluye en los metadatos IL del ensamblado de código administrado, solo si el símbolo de compilación CODE_ANALYSIS se define en tiempo de compilación.

En C++ / CLI, use las macros CA\_suprimir\_mensaje o CA\_GLOBAL\_SUPPRESS_MESSAGE en el archivo de encabezado para agregar el atributo.

> [!NOTE]
> No se deben usar supresiones en código fuente en versiones de lanzamiento, para evitar que los metadatos de supresión en el código fuente de envío accidentalmente. Además, debido al costo de procesamiento de supresión en el código fuente, el rendimiento de la aplicación puede verse degradado.

> [!NOTE]
> Si migra un proyecto en Visual Studio de 2017, de repente puede encontrar con un número excesivo de advertencias de análisis de código. Si no está preparado para solucionar las advertencias y desea desactivar temporalmente el análisis de código, abra páginas de propiedades del proyecto (**proyecto** > ***proyecto* propiedades...** ) y vaya a la **análisis de código** ficha. Anule la selección de **Habilitar análisis de código al compilar**y, a continuación, recompile el proyecto. Como alternativa, puede seleccionar una regla distintas, menor configurada para ejecutarse en el código. No olvide activar el análisis de código nuevo cuando esté preparado para solucionar las advertencias.

## <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)

Cuando eliges **suprimir** en el menú contextual o el menú contextual de una advertencia de análisis de código en el **lista de errores**, un <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se agrega el atributo en el código o para la supresión global del proyecto archivo.

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

- **Identificador de regla** -el identificador de la regla. La compatibilidad incluye tanto un nombre corto y largo para el identificador de regla. El nombre corto es la regla. el nombre corto es CAXXXX.

- **Justificación** -el texto que se utiliza para documentar el motivo para suprimir el mensaje.

- **Id. de mensaje** -identificador único de un problema para cada mensaje.

- **Ámbito** -el destino en el que se suprime la advertencia. Si no se especifica el destino, se establece en el destino del atributo. Los ámbitos admitidos son los siguientes:

    - Module

    - Espacio de nombres

    - Recurso

    - Tipo

    - Miembro

- **Destino** : un identificador que se utiliza para especificar el destino en el que se suprime la advertencia. Debe contener un nombre de elemento completo.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Se suprimen las advertencias de análisis de código en el nivel al que la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se aplica el atributo. Por ejemplo, se puede aplicar el atributo en el ensamblado, nivel de módulo, tipo, miembro o parámetro. El propósito de este es acoplar estrechamente la información de supresión al código donde se produce la infracción.

La forma de supresión general incluye la categoría de regla y un identificador de regla, que contiene una representación legible opcional del nombre de la regla. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Si hay motivos de rendimiento estricta para minimizar los metadatos de supresión en el código fuente, se puede omitir el nombre de la regla. La categoría de regla y el identificador de regla constituyen en conjunto un identificador de regla suficientemente único. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Por razones de mantenimiento, no se recomienda si se omite el nombre de la regla.

## <a name="suppress-selective-violations-within-a-method-body"></a>Suprimir selectivas infracciones dentro de un cuerpo de método

Atributos de supresión se pueden aplicar a un método, pero no se puede incrustar dentro de un cuerpo de método. Esto significa que todas las infracciones de una regla determinada se suprimen si agrega el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo al método.

En algunos casos, puede suprimir una instancia determinada de la infracción, por ejemplo, de modo que el código futuras no es automáticamente exento de la regla de análisis de código. Ciertas reglas de análisis de código le permiten hacer esto mediante el uso de la `MessageId` propiedad de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. En general, las reglas de heredado de infracciones en un sentido símbolo en concreto (un parámetro o variable local) el `MessageId` propiedad. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) es un ejemplo de dicha regla. Sin embargo, las reglas heredadas de infracciones en código ejecutable (no de símbolos) no respetan la `MessageId` propiedad. Además, los analizadores de .NET Compiler Platform («Roslyn») no respetan la `MessageId` propiedad.

Para suprimir una infracción de símbolo en concreto de una regla, especifique el nombre del símbolo para el `MessageId` propiedad de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo. En el ejemplo siguiente se muestra código con dos infracciones de [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;uno para la `name` variable y otra para el `age` variable. Solo la infracción de la `age` se suprime el símbolo.

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

Los compiladores de código administrado y algunas herramientas de otros fabricantes generan código para facilitar el desarrollo rápido de código. Código generado por el compilador que aparece en los archivos de código fuente normalmente se marca con el `GeneratedCodeAttribute` atributo.

Puede elegir si se debe suprimir las advertencias de análisis de código y los errores de código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, vea [Cómo: Suprimir advertencias de código generado por](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Análisis de código omite `GeneratedCodeAttribute` cuando se aplica a todo un ensamblado o un parámetro único.

## <a name="global-level-suppressions"></a>Supresiones de nivel global

La herramienta de análisis de código administrado examina `SuppressMessage` atributos que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También se desencadena infracciones contra los recursos y los espacios de nombres. Estas infracciones deben aplicarse en el nivel global y se ámbito y se aplican. Por ejemplo, el mensaje siguiente suprime una infracción de espacio de nombres:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Cuando se suprime una advertencia con ámbito de espacio de nombres, se suprime la advertencia contra el espacio de nombres. No se suprime la advertencia contra los tipos dentro del espacio de nombres.

Cualquier supresión se puede expresar especificando un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro decorando un tipo.

Supresiones de nivel global son la única manera de suprimir mensajes que hacen referencia al código generado por el compilador que no se asigna a la fuente de usuario proporcionado de manera explícita. Por ejemplo, el siguiente código elimina una infracción contra un constructor emitido por el compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` siempre contiene el nombre del elemento completo.

## <a name="global-suppression-file"></a>Archivo de supresión global

El archivo de supresión global mantiene supresiones supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, supresiones por infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque la configuración del nivel de proyecto no está disponible para el código detrás de un formulario. Se crea un archivo de supresión global y se agrega al proyecto la primera vez que seleccione la **en el archivo de supresión de proyecto** opción de la **suprimir** comando en el **lista de errores**ventana.

## <a name="see-also"></a>Vea también

- <xref:System.Diagnostics.CodeAnalysis>
- [Usar los analizadores de Roslyn](../code-quality/use-roslyn-analyzers.md)