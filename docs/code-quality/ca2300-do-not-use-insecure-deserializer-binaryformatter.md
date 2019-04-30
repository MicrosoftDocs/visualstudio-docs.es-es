---
title: 'CA2300: No usar el deserializador no seguro BinaryFormatter'
ms.date: 04/05/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 400c259cf7aac5b6f3ea4a6c196ebaa77e29289b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545581"
---
# <a name="ca2300-do-not-use-insecure-deserializer-binaryformatter"></a>CA2300: No usar el deserializador no seguro BinaryFormatter

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerBinaryFormatter|
|Identificador de comprobación|CA2300|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> método de deserialización se llama o se hace referencia.

## <a name="rule-description"></a>Descripción de la regla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Esta regla busca <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> referencias o llamadas a métodos de deserialización. Si desea deserializar solamente cuando el <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propiedad está establecida para restringir los tipos, deshabilite esta regla y habilitar reglas [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) y [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, use un serializador seguro de en su lugar, y **no permitir que un atacante especificar un tipo arbitrario para deserializar**. Algunos serializadores más seguros incluyen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -No use nunca <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Si debe utilizar a un solucionador de tipos, restringir tipos deserializados a una lista esperada.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - NewtonSoft Json.NET - Use TypeNameHandling.None. Si se debe usar otro valor para TypeNameHandling, restringir tipos deserializados a una lista con un ISerializationBinder personalizado esperada.
  - Búferes de protocolo
- Realizar la prueba de manipulaciones de datos serializados. Después de la serialización, firmar criptográficamente los datos serializados. Antes de la deserialización, validar la firma criptográfica. Impedir que la clave criptográfica que se revele y diseño para las rotaciones de clave.
- Restringir tipos deserializados. Implementar un personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de deserializar con <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, establezca el <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> propiedad a una instancia de personalizado <xref:System.Runtime.Serialization.SerializationBinder>. En el invalidado <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> método, si el tipo es inesperado, a continuación, produce una excepción.
- Si restringe los tipos deserializados, es posible que desea deshabilitar esta regla y habilitar reglas [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) y [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md). Las reglas de [CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) y [CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) ayuda a asegurarse de que el <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Binder> siempre se establece la propiedad antes de deserializar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System.IO;
using System.Runtime.Serialization.Formatters.Binary;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        BinaryFormatter formatter = new BinaryFormatter();
        return formatter.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization.Formatters.Binary

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim formatter As BinaryFormatter = New BinaryFormatter()
        Return formatter.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Reglas relacionadas

[CA2301: No llame a BinaryFormatter.Deserialize sin establecer primero BinaryFormatter.Binder](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)

[CA2302: Asegúrese de que se establece BinaryFormatter.Binder antes de llamar a BinaryFormatter.Deserialize](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)