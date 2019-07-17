---
title: 'CA2238: Implementar métodos de serialización correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cff617adf2b31ef773de3bc41db7245346795bee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142383"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementar métodos de serialización correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA2238: Implementar métodos de serialización correctamente](https://docs.microsoft.com/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).  
  
|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|Identificador de comprobación|CA2238|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Importante: si el método es visible fuera del ensamblado.<br /><br /> Non-problemático: si el método no es visible fuera del ensamblado.|  
  
## <a name="cause"></a>Causa  
 Un método que controla un evento de serialización no especifica la firma correcta, el tipo de valor devuelto ni la visibilidad.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Un método se designa un controlador de eventos de serialización aplicando uno de los atributos de eventos de serialización siguientes:  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
  Controladores de eventos de serialización toman un único parámetro de tipo <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>, return `void`y tienen `private` visibilidad.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija la firma, el tipo de valor devuelto o la visibilidad del controlador de eventos de serialización.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los controladores de eventos de serialización correctamente declarados.  
  
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)
