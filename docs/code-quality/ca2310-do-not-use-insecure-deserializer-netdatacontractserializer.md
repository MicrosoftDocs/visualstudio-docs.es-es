---
title: 'CA2310: No use deserializador inseguro NetDataContractSerializer'
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
ms.openlocfilehash: e4af6bbfbd7e14b99f39ffa0adb5d1117c200d9a
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135433"
---
# <a name="ca2310-do-not-use-insecure-deserializer-netdatacontractserializer"></a>CA2310: No use deserializador inseguro NetDataContractSerializer

|||
|-|-|
|TypeName|DoNotUseInsecureDeserializerNetDataContractSerializer|
|Identificador de comprobación|CA2310|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> método de deserialización se llama o se hace referencia.

## <a name="rule-description"></a>Descripción de la regla

[!INCLUDE[insecure-deserializers-description](includes/insecure-deserializers-description-md.md)]

Esta regla busca <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=nameWithType> referencias o llamadas a métodos de deserialización. Si desea deserializar solamente cuando el <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propiedad está establecida para restringir los tipos, deshabilite esta regla y habilitar reglas [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) en su lugar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

- Si es posible, use un serializador seguro de en su lugar, y **no permitir que un atacante especificar un tipo arbitrario para deserializar**. Algunos serializadores más seguros incluyen:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -No use nunca <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Si debe utilizar a un solucionador de tipos, restringir tipos deserializados a una lista esperada.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET - Use TypeNameHandling.None. Si se debe usar otro valor para TypeNameHandling, restringir tipos deserializados a una lista con un ISerializationBinder personalizado esperada.
  - Búferes de protocolo
- Realizar la prueba de manipulaciones de datos serializados. Después de la serialización, firmar criptográficamente los datos serializados. Antes de la deserialización, validar la firma criptográfica. Proteger la clave criptográfica que se revele y el diseño para las rotaciones de clave.
- Restringir tipos deserializados. Implementar un personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Antes de deserializar con <xref:System.Runtime.Serialization.NetDataContractSerializer>, establezca el <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> propiedad a una instancia de personalizado <xref:System.Runtime.Serialization.SerializationBinder>. En el invalidado <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> método, si el tipo es inesperado, produce una excepción.
- Si restringe los tipos deserializados, es posible que desea deshabilitar esta regla y habilitar reglas [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md). Las reglas de [CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) y [CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) ayuda a asegurarse de que el <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder> siempre se establece la propiedad antes de deserializar.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

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

[CA2311: No se puedan deserializar sin establecer primero NetDataContractSerializer.Binder](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)

[CA2312: Asegúrese de que se establece NetDataContractSerializer.Binder antes de deserializar](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)
