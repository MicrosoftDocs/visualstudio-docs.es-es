---
title: 'CA1024: Utilizar las propiedades donde corresponda | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bf44541c9eca3d2b8027ff1b5811caf0ba6824f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Utilizar las propiedades donde corresponda
|||  
|-|-|  
|TypeName|UsePropertiesWhereAppropriate|  
|Identificador de comprobación|CA1024|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método público o protegido tiene un nombre que comienza con `Get`, no toma ningún parámetro y devuelve un valor que no es una matriz.  
  
## <a name="rule-description"></a>Descripción de la regla  
 En la mayoría de los casos, las propiedades representan datos y los métodos realizan acciones. Propiedades son accesibles como campos, que hace que sean fáciles de usar. Un método es un buen candidato para convertirse en propiedad si hay alguna de estas condiciones:  
  
-   No toma ningún argumento y devuelve la información de estado de un objeto.  
  
-   Acepta un argumento único para establecer alguna parte del estado de un objeto.  
  
 Las propiedades deberían comportarse como si fueran campos; Si el método no es posible, no debe cambiarse a una propiedad. Métodos son mejores que las propiedades en las situaciones siguientes:  
  
-   El método realiza una operación que consume mucho tiempo. El método es tarda más que el tiempo necesario para establecer u obtener el valor de un campo.  
  
-   El método realiza una conversión. Acceso a un campo no devuelve una versión convertida de los datos que almacena.  
  
-   El método Get tiene un efecto secundario observable. La recuperación del valor de un campo no produce ningún efecto secundario.  
  
-   Es importante el orden de ejecución. Establecer el valor de un campo no se basa en la repetición de otras operaciones.  
  
-   Llamar al método dos veces seguidas da lugar a resultados diferentes.  
  
-   El método es estático pero devuelve un objeto que se puede cambiar por el llamador. La recuperación del valor de un campo no permite al llamador cambiar los datos que se almacenan en el campo.  
  
-   El método devuelve una matriz.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el método a una propiedad.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla si el método cumple al menos uno de los criterios enumerados anteriormente.  
  
## <a name="controlling-property-expansion-in-the-debugger"></a>Controlar la expansión de la propiedad en el depurador  
 Los programadores de evitan el uso de una propiedad de una de las razones es porque no desea que el depurador se expanda automáticamente. Por ejemplo, la propiedad podría implicar la asignación de un objeto grande o una llamada a P/Invoke, pero realmente no podría tener efectos secundarios observables.  
  
 Puede impedir que el depurador de ampliación automática propiedades aplicando <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. En el ejemplo siguiente se muestra este atributo se aplica a una propiedad de instancia.  
  
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
  
 [!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]