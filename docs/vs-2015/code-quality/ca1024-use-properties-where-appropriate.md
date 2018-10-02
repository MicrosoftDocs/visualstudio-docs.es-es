---
title: 'CA1024: Utilizar las propiedades donde corresponda | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 952bb3c63e9d8ce645b9e986f44aaed50cb0afa4
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592008"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizar las propiedades donde corresponda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1024: utilizar las propiedades donde corresponda](https://docs.microsoft.com/visualstudio/code-quality/ca1024-use-properties-where-appropriate).

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|Identificador de comprobación|CA1024|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido tiene un nombre que comienza con `Get`no toma ningún parámetro y devuelve un valor que no es una matriz.

## <a name="rule-description"></a>Descripción de la regla
 En la mayoría de los casos, las propiedades representan datos y los métodos realizan acciones. Las propiedades son accesibles como campos, que hace que sea más fácil de usar. Un método es un buen candidato para convertirse en una propiedad, si hay alguna de estas condiciones:

-   No toma ningún argumento y devuelve la información de estado de un objeto.

-   Acepta un argumento único para establecer alguna parte del estado de un objeto.

 Las propiedades deben comportarse como si fueran campos; Si el método no es posible, no debe cambiarse a una propiedad. Los métodos son mejores que las propiedades en las situaciones siguientes:

-   El método realiza una operación lenta. El método es tarda más que el tiempo necesario para establecer u obtener el valor de un campo.

-   El método realiza una conversión. Acceso a un campo no devuelve una versión convertida de los datos que almacena.

-   El método Get tiene un efecto secundario observable. Recuperar el valor de un campo no producir efectos secundarios.

-   Es importante el orden de ejecución. Establecer el valor de un campo no se basa en la aparición de otras operaciones.

-   Llamar al método dos veces seguidas crea resultados diferentes.

-   El método es estático pero devuelve un objeto que se puede cambiar el llamador. Recuperar el valor de un campo no permite al llamador para cambiar los datos que se almacenan en el campo.

-   El método devuelve una matriz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el método a una propiedad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método cumpla al menos uno de los criterios mostrados anteriormente.

## <a name="controlling-property-expansion-in-the-debugger"></a>Controlar la expansión de la propiedad en el depurador
 Una razón que los programadores de evitan el uso de una propiedad es ya que no desean que el depurador se expanda automáticamente. Por ejemplo, puede implicar la propiedad de asignación de un objeto grande o una llamada P/Invoke, pero realmente no podría tener cualquier efecto secundario observable.

 Puede impedir que el depurador de ampliación automática propiedades aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. El ejemplo siguiente muestra este atributo se aplica a una propiedad de instancia.

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
```

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene varios métodos que deben convertirse en Propiedades, y varios que no deben porque no se comportan como campos.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]



