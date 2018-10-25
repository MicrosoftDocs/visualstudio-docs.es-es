---
title: 'CA1052: Los tipos titulares estáticos deben ser sealed | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b605d4361e2a29174d4640406228c402a9c8429a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823858"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052: Los tipos titulares estáticos deben ser sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|Identificador de comprobación|CA1052|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene sólo miembros estáticos y no se ha declarado con el [sealed](http://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](http://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modificador.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla supone que un tipo que contiene a sólo miembros estáticos no está diseñado para heredarse, porque el tipo no proporciona ninguna funcionalidad que se puede invalidar en un tipo derivado. Un tipo que no está diseñado para heredarse debería marcarse con el `sealed` modificador para prohibir su uso como un tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el tipo como `sealed`. Si desea usar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 o versiones anteriores, un mejor enfoque es marcar el tipo como `static`. De esta manera, se evita tener que declarar un constructor privado para evitar que la clase que se está creando.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla sólo si el tipo está diseñado para heredarse. La ausencia de la `sealed` modificador sugiere que el tipo es útil como tipo base.

## <a name="example-of-a-violation"></a>Ejemplo de una infracción

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra un tipo que infringe la regla.

### <a name="code"></a>Código
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Corregir con el modificador "Static"

### <a name="description"></a>Descripción
 El ejemplo siguiente muestra cómo corregir una infracción de esta regla, marque el tipo con el `static` modificador.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1053: Los tipos titulares estáticos no deben tener constructores](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)



