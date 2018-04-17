---
title: 'CA2222: No reducir la visibilidad del miembro heredado | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de96b199adf5b282f70207478e4d9ae38c4d00f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: No reducir la visibilidad del miembro heredado
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|Identificador de comprobación|CA2222|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un método privado en un tipo no sellado tiene una firma que es idéntica a un método público declarado en un tipo base. El método privado no es final.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No debería cambiar el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método. Si el miembro se cambia a privado y el tipo está sellado, pueden llamar tipos heredados a la última implementación pública del método en la jerarquía de herencia. Si necesita cambiar el modificador de acceso, el método debería marcarse final o su tipo debe ser sealed para impedir que el método se invalide.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el acceso para ser no privados. O bien, si su lenguaje de programación lo admite, puede realizar el método final.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]