---
title: 'CA1024: Use las propiedades cuando corresponda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b190e007cfdb016e54148cf0295c68baf68c5033
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661962"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizar las propiedades donde corresponda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|Identificador de comprobación|CA1024|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido tiene un nombre que comienza por `Get`, no toma ningún parámetro y devuelve un valor que no es una matriz.

## <a name="rule-description"></a>Descripción de la regla
 En la mayoría de los casos, las propiedades representan datos y métodos para realizar acciones. Se tiene acceso a las propiedades como campos, lo que facilita su uso. Un método es un buen candidato para convertirse en una propiedad si existe alguna de estas condiciones:

- No toma ningún argumento y devuelve la información de estado de un objeto.

- Acepta un solo argumento para establecer parte del estado de un objeto.

  Las propiedades deben comportarse como si fueran campos; Si el método no puede, no se debe cambiar a una propiedad. Los métodos son mejores que las propiedades en las siguientes situaciones:

- El método realiza una operación que lleva mucho tiempo. El método es perceptiblemente más lento que el tiempo necesario para establecer u obtener el valor de un campo.

- El método realiza una conversión. El acceso a un campo no devuelve una versión convertida de los datos que almacena.

- El método get tiene un efecto secundario observable. La recuperación del valor de un campo no produce efectos secundarios.

- El orden de ejecución es importante. Establecer el valor de un campo no se basa en la aparición de otras operaciones.

- La llamada al método dos veces en sucesión crea resultados diferentes.

- El método es estático, pero devuelve un objeto que el llamador puede cambiar. Al recuperar el valor de un campo, no se permite que el autor de la llamada cambie los datos almacenados por el campo.

- El método devuelve una matriz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el método a una propiedad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método cumple al menos uno de los criterios enumerados anteriormente.

## <a name="controlling-property-expansion-in-the-debugger"></a>Controlar la expansión de propiedades en el depurador
 Uno de los motivos por los que los programadores evitan el uso de una propiedad es porque no quieren que el depurador lo expanda automáticamente. Por ejemplo, la propiedad puede implicar la asignación de un objeto grande o la llamada a P/Invoke, pero podría no tener realmente efectos secundarios observables.

 Puede evitar que el depurador de las propiedades de expansión automática aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. En el ejemplo siguiente se muestra este atributo que se aplica a una propiedad de instancia.

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
 El ejemplo siguiente contiene varios métodos que se deben convertir en propiedades y otros que no deberían hacerlo porque no se comportan como campos.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
