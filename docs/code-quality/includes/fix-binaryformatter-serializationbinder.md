---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471587"
---
- En su lugar, use un serializador seguro y **no permita que un atacante especifique un tipo arbitrario para deserializar**. Para obtener más información, vea las [alternativas preferidas](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Convierta la prueba de alteración de los datos serializados. Después de la serialización, firme criptográficamente los datos serializados. Antes de la deserialización, valide la firma criptográfica. Proteja la clave criptográfica para que no se revele y diseñe las rotaciones de clave.
- Esta opción hace que el código sea vulnerable a los ataques de denegación de servicio y posibles ataques de ejecución remota de código en el futuro. Para obtener más información, vea la [Guía de seguridad BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Restrinja los tipos deserializados. Implementar un personalizado <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Antes de la deserialización, establezca la `Binder` propiedad en una instancia del personalizado <xref:System.Runtime.Serialization.SerializationBinder> en todas las rutas de acceso del código. En el método invalidado <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , si el tipo es inesperado, inicie una excepción para detener la deserialización.
