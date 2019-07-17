---
title: 'CA2222: No disminuir la visibilidad del miembro heredado | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee6228359e84687023a713ee866ebfbb760b206b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142452"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: No disminuir la visibilidad del miembro heredado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|Identificador de comprobación|CA2222|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un método privado en un tipo no sellado tiene una firma que es idéntica a un método público declarado en un tipo base. El método privado no es final.

## <a name="rule-description"></a>Descripción de la regla
 No debería cambiar el modificador de acceso para los miembros heredados. Cambiando un miembro heredado a privado no evita que los llamadores tengan acceso a la implementación de la clase base del método. Si el miembro se cambia a privado y el tipo está sellado, pueden llamar tipos heredados a la última implementación pública del método en la jerarquía de herencia. Si necesita cambiar el modificador de acceso, el método debería marcarse como final o su tipo debe ser sealed para impedir que se invalide el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el acceso para que sea no privados. Como alternativa, si lo admite el lenguaje de programación, puede hacer el método final.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
