---
title: "CA1413: Evite campos no públicos en tipos de valor visibles COM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0e2763cb21107f19768a8161d18e1128eb000d29
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evite campos no públicos en tipos de valor visibles para COM
|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|Identificador de comprobación|CA1413|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo de valor que está marcado específicamente como visible para el modelo de objetos componentes (COM) declara un campo de instancia no públicos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los campos de instancia no públicos de tipos de valor visibles para COM están visibles para los clientes COM. Revise el contenido del campo para obtener información que no deba exponerse o que tendrá un efecto no deseado de seguridad o el diseño.  
  
 De forma predeterminada, todos los tipos de valor público están visibles para COM. Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad de COM del tipo para especificarse explícitamente. El ensamblado que lo contiene se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla y mantener el campo oculto, cambie el tipo de valor a un tipo de referencia o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributo del tipo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la exposición pública del campo es aceptable.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Vea también  
 [Interoperar con código no administrado](/dotnet/framework/interop/index)   
 [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)