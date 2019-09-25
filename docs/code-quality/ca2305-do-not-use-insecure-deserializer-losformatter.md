---
title: 'CA2305: No usar el deserializador no seguro LosFormatter'
ms.date: 05/01/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
f1_keywords:
- CA2305
- DoNotUseInsecureDeserializerLosFormatter
ms.openlocfilehash: 145d45d79f1dda27d5c69f0c481277572d3eeaa2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237730"
---
# <a name="ca2305-do-not-use-insecure-deserializer-losformatter"></a>CA2305: No usar el deserializador no seguro LosFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerLosFormatter|
|Identificador de comprobación|CA2305|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Se <xref:System.Web.UI.LosFormatter?displayProperty=nameWithType> llamó a un método de deserialización o se hizo referencia a él.

## <a name="rule-description"></a>Descripción de la regla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Esta regla busca <xref:System.Web.UI.LosFormatter?displayProperty=nameWithType> llamadas o referencias al método de deserialización.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

[!INCLUDE[insecure-deserializers-fixes-for-always-insecure-deserializers](includes/insecure-deserializers-fixes-for-always-insecure-deserializers-md.md)]

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System.IO;
using System.Web.UI;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        LosFormatter formatter = new LosFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Web.UI

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As LosFormatter = New LosFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```