---
title: "CA1052: Los tipos titulares estáticos deben ser sealed | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d9ce807aca8b28a279a3a423802196e710f63dea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Los tipos titulares estáticos deben ser sealed
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|Identificador de comprobación|CA1052|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido solamente contiene miembros estáticos y no se declara con el [sellado](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificador.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla supone que un tipo que contiene a sólo miembros estáticos no está diseñado para heredarse, porque el tipo no proporciona ninguna funcionalidad que se pueden invalidar en un tipo derivado. Un tipo que no está diseñado para heredarse debería marcarse con el `sealed` modificador para prohibir su uso como tipo base.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el tipo como `sealed`. Si desea usar [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 o posterior, es un enfoque más adecuado marcar el tipo como `static`. De esta manera, se evita tener que declarar un constructor privado para evitar que la clase que se está creando.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Suprima las advertencias de esta regla sólo si el tipo está diseñado para heredarse. La ausencia de la `sealed` modificador sugiere que el tipo sea útil como tipo base.  
  
## <a name="example-of-a-violation"></a>Ejemplo de una infracción  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra un tipo que infringe la regla.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Corregir con el modificador Static  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra cómo corregir una infracción de esta regla marcando el tipo con el `static` modificador.  
  
### <a name="code"></a>Código  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
