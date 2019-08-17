---
title: Suprimir advertencias de análisis de código
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 60fcb13c978d614d40964bd8d6da21e8cf41f00f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551081"
---
# <a name="suppress-code-analysis-warnings"></a>Suprimir advertencias de análisis de código

A menudo resulta útil indicar que una advertencia no es aplicable. Esto indica a los miembros del equipo que el código se ha revisado y que se puede suprimir la advertencia. La supresión en el código fuente (ISS) <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> utiliza el atributo para suprimir una advertencia. El atributo se puede colocar cerca del segmento de código que generó la advertencia. Puede Agregar el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo al archivo de código fuente escribiéndolo en, o bien puede utilizar el menú contextual de una advertencia en el **lista de errores** para agregarlo automáticamente.

El <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributo es un atributo condicional, que se incluye en los metadatos de Il del ensamblado de código administrado, solo si el símbolo de compilación CODE_ANALYSIS se define en tiempo de compilación.

En C++/CLI\_, use la CA de macros\_Suppress Message o\_SUPPRESS_MESSAGE\_global de CA en el archivo de encabezado para agregar el atributo.

> [!NOTE]
> No debe usar supresiones en el origen en las compilaciones de versión para evitar que se envíen accidentalmente los metadatos de supresión en el código fuente. Además, debido al costo de procesamiento de la supresión en el código fuente, se puede degradar el rendimiento de la aplicación.

> [!NOTE]
> Si migra un proyecto a Visual Studio 2017 o Visual Studio 2019, es posible que se enfrente a un gran número de advertencias de análisis de código. Si no está listo para corregir las advertencias, puede suprimir todas ellas eligiendo **analizar** > **Ejecutar Análisis de código y suprimir problemas activos**.
>
> ![Ejecutar análisis de código y suprimir problemas en Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage (atributo)

Al elegir suprimir en el menú contextual o de clic con el botón derecho de una advertencia de análisis de <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> código en el **lista de errores**, se agrega un atributo en el código o en el archivo de supresión global del proyecto.

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

- **Categoría** : la categoría en la que se define la regla. Para obtener más información sobre las categorías de reglas de análisis de código, vea [advertencias de código administrado](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** : el identificador de la regla. La compatibilidad incluye un nombre corto y largo para el identificador de regla. El nombre corto es CAXXXX; el nombre largo es CAXXXX: FriendlyTypeName.

- **Justificación** : el texto que se usa para documentar el motivo de la supresión del mensaje.

- **MessageId** : identificador único de un problema para cada mensaje.

- **Ámbito** : el destino en el que se va a suprimir la advertencia. Si no se especifica el destino, se establece en el destino del atributo. Entre los [ámbitos](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) admitidos se incluyen los siguientes:

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace`: Este ámbito suprime las advertencias en el espacio de nombres. No suprime las advertencias de los tipos dentro del espacio de nombres.

  - `namespaceanddescendants`-(Novedad de Visual Studio 2019) este ámbito suprime las advertencias en un espacio de nombres y todos sus símbolos descendientes. El `namespaceanddescendants` análisis heredado omite el valor.

- **Target** : un identificador que se usa para especificar el destino en el que se va a suprimir la advertencia. Debe contener un nombre de elemento completo.

## <a name="suppressmessage-usage"></a>Uso de SuppressMessage

Las advertencias de análisis de código se suprimen en el <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> nivel al que se aplica el atributo. Por ejemplo, el atributo se puede aplicar en el nivel de ensamblado, módulo, tipo, miembro o parámetro. La finalidad de esto es acoplar estrechamente la información de supresión en el código donde se produce la infracción.

La forma general de supresión incluye la categoría de regla y un identificador de regla, que contiene una representación opcional inteligible del nombre de la regla. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Si hay razones de rendimiento estrictas para minimizar los metadatos de supresión en el código fuente, se puede omitir el nombre de la regla. La categoría de regla y su identificador de regla forman un identificador de regla suficientemente único. Por ejemplo:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

Por motivos de mantenimiento, no se recomienda omitir el nombre de la regla.

## <a name="suppress-selective-violations-within-a-method-body"></a>Suprimir infracciones selectivas dentro de un cuerpo de método

Los atributos de supresión se pueden aplicar a un método, pero no se pueden incrustar dentro de un cuerpo de método. Esto significa que todas las infracciones de una regla determinada se suprimen si <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> agrega el atributo al método.

En algunos casos, puede que desee suprimir una instancia determinada de la infracción, por ejemplo, para que el código futuro no se excluya automáticamente de la regla de análisis de código. Ciertas reglas `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> de análisis de código permiten hacer esto mediante el uso de la propiedad del atributo. En general, las reglas heredadas para las infracciones en un símbolo determinado (una variable local o `MessageId` un parámetro) respetan la propiedad. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) es un ejemplo de este tipo de regla. Sin embargo, las reglas heredadas para las infracciones en código ejecutable (sin símbolo) no `MessageId` respetan la propiedad. Además, los analizadores de .net Compiler Platform ("Roslyn") no respetan la `MessageId` propiedad.

Para suprimir una infracción de símbolo en particular de una regla, especifique el `MessageId` nombre del símbolo <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> para la propiedad del atributo. En el ejemplo siguiente se muestra código con dos infracciones de [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;una para la `name` variable y `age` otra para la variable. Solo se suprime la `age` infracción del símbolo.

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

Los compiladores de código administrado y algunas herramientas de terceros generan código para facilitar el desarrollo rápido de código. El código generado por el compilador que aparece en los archivos de `GeneratedCodeAttribute` código fuente normalmente se marca con el atributo.

Puede decidir si desea suprimir los errores y advertencias de análisis de código para el código generado. Para obtener información sobre cómo suprimir estas advertencias y errores, [consulte Cómo: Suprime las advertencias del](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)código generado.

> [!NOTE]
> El análisis de código `GeneratedCodeAttribute` se omite cuando se aplica a un ensamblado completo o a un solo parámetro.

## <a name="global-level-suppressions"></a>Supresiones de nivel global

La herramienta de análisis de código administrado `SuppressMessage` examina los atributos que se aplican en el nivel de ensamblado, módulo, tipo, miembro o parámetro. También activa las infracciones en los recursos y espacios de nombres. Estas infracciones deben aplicarse en el nivel global y tienen el ámbito y el destino. Por ejemplo, el siguiente mensaje suprime una infracción del espacio de nombres:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Al suprimir una advertencia con `namespace` el ámbito, se suprime la advertencia en el espacio de nombres en sí. No suprime la advertencia en los tipos del espacio de nombres.

Cualquier supresión se puede expresar especificando un ámbito explícito. Estas supresiones deben residir en el nivel global. No se puede especificar la supresión de nivel de miembro decorando un tipo.

Las supresiones de nivel global son la única manera de suprimir los mensajes que hacen referencia al código generado por el compilador que no se asigna a un origen de usuario proporcionado explícitamente. Por ejemplo, el siguiente código suprime una infracción en un constructor emitido por compilador:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`siempre contiene el nombre completo del elemento.

## <a name="global-suppression-file"></a>Archivo de supresión global

El archivo de supresión global mantiene las supresiones que son supresiones de nivel global o supresiones que no especifican un destino. Por ejemplo, las supresiones para las infracciones de nivel de ensamblado se almacenan en este archivo. Además, algunas supresiones de ASP.NET se almacenan en este archivo porque la configuración de nivel de proyecto no está disponible para el código subyacente de un formulario. Se crea un archivo de supresión global y se agrega al proyecto la primera vez que se selecciona la opción **en el archivo de supresión del proyecto** del comando **suprimir** de la ventana de **lista de errores** .

## <a name="see-also"></a>Vea también

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Usar analizadores de código](../code-quality/use-roslyn-analyzers.md)
