---
title: 'CA1024: Utilizar las propiedades donde corresponda'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfedb55c0dcdb1077faea03bca56488ab3da1525
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842468"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizar las propiedades donde corresponda

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|Identificador de comprobación|CA1024|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método tiene un nombre que comienza con `Get`no toma ningún parámetro y devuelve un valor que no es una matriz.

De forma predeterminada, esta regla solo se examina los métodos públicos y protegidos, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

En la mayoría de los casos, las propiedades representan datos y los métodos realizan acciones. Las propiedades son accesibles como campos, que hace que sea más fácil de usar. Un método es un buen candidato para convertirse en una propiedad, si hay alguna de estas condiciones:

- No toma ningún argumento y devuelve la información de estado de un objeto.

- Acepta un argumento único para establecer alguna parte del estado de un objeto.

Las propiedades deben comportarse como si fueran campos; Si el método no es posible, no debe cambiarse a una propiedad. Los métodos son mejores que las propiedades en las situaciones siguientes:

- El método realiza una operación lenta. El método es tarda más que el tiempo necesario para establecer u obtener el valor de un campo.

- El método realiza una conversión. Acceso a un campo no devuelve una versión convertida de los datos que almacena.

- El método Get tiene un efecto secundario observable. Recuperar el valor de un campo no producir efectos secundarios.

- Es importante el orden de ejecución. Establecer el valor de un campo no se basa en la aparición de otras operaciones.

- Llamar al método dos veces seguidas crea resultados diferentes.

- El método es estático pero devuelve un objeto que se puede cambiar el llamador. Recuperar el valor de un campo no permite al llamador para cambiar los datos que se almacenan en el campo.

- El método devuelve una matriz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el método a una propiedad.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprima una advertencia de esta regla si el método cumpla al menos uno de los criterios mostrados anteriormente.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Expansión de la propiedad de control en el depurador

Los programadores de evitan el uso de una propiedad de una de las razones es ya que no desean que el depurador de ampliación automática. Por ejemplo, puede implicar la propiedad de asignación de un objeto grande o una llamada P/Invoke, pero realmente no podría tener cualquier efecto secundario observable.

Puede evitar que el depurador de propiedades autoexpanding aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. El ejemplo siguiente muestra este atributo se aplica a una propiedad de instancia.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp
using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]
            }
        }
    }
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente contiene varios métodos que deben convertirse en propiedades y varios que no deben porque no se comportan como campos.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]