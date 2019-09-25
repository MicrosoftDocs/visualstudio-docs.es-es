---
title: 'CA2310: No usar el deserializador no seguro NetDataContractSerializer'
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
- CA2310
- DoNotUseInsecureDeserializerNetDataContractSerializer
ms.openlocfilehash: 5335e72307ea201ad77d6e59b267572d4d9aae56
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237720"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: No usar el deserializador no seguro NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|Identificador de comprobación|CA2310|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Se <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> llamó a un método de deserialización o se hizo referencia a él.

## <a name="rule-description"></a>Descripción de la regla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Esta regla busca <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> llamadas o referencias al método de deserialización. Si solo desea deserializar cuando la <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propiedad está establecida en restringir tipos, deshabilite esta regla y habilite las reglas [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, use un serializador seguro en su lugar y **no permita que un atacante especifique un tipo arbitrario para deserializar**. Algunos serializadores más seguros incluyen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>: No usar <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>nunca. Si debe usar un solucionador de tipos, restrinja los tipos deserializados a una lista de espera.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET: Use TypeNameHandling. None. Si debe usar otro valor para TypeNameHandling, restrinja los tipos deserializados a una lista de espera con un ISerializationBinder personalizado.
  - Búferes de protocolo
- Convierta la prueba de alteración de los datos serializados. Después de la serialización, firme criptográficamente los datos serializados. Antes de la deserialización, valide la firma criptográfica. Proteja la clave criptográfica para que no se revele y diseñe las rotaciones de clave.
- Restrinja los tipos deserializados. Implementar un personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de deserializar <xref:System.Runtime.Serialization.NetDataContractSerializer>con, establezca <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> la propiedad en una instancia de su <xref:System.Runtime.Serialization.SerializationBinder>personalizado. En el método invalidado <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si el tipo es inesperado, inicie una excepción para detener la deserialización.
  - Si restringe los tipos deserializados, puede que desee deshabilitar esta regla y habilitar las reglas [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Las reglas [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) ayudan a asegurarse de <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> que la propiedad siempre se establece antes de la deserialización.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

[!INCLUDE[insecure-deserializers-common-safe-to-suppress](includes/insecure-deserializers-common-safe-to-suppress-md.md)]

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

### <a name="violation"></a>Infracción

```csharp
using System.IO;
using System.Runtime.Serialization;

public class ExampleClass
{
    public object MyDeserialize(byte[] bytes)
    {
        NetDataContractSerializer serializer = new NetDataContractSerializer();
        return serializer.Deserialize(new MemoryStream(bytes));
    }
}
```

```vb
Imports System.IO
Imports System.Runtime.Serialization

Public Class ExampleClass
    Public Function MyDeserialize(bytes As Byte()) As Object
        Dim serializer As NetDataContractSerializer = New NetDataContractSerializer()
        Return serializer.Deserialize(New MemoryStream(bytes))
    End Function
End Class
```

## <a name="related-rules"></a>Reglas relacionadas

[CA2311: No deserializar sin establecer primero NetDataContractSerializer. Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Asegúrese de que NetDataContractSerializer. Binder se establece antes de la deserialización](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
