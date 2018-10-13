---
title: 'CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto | Microsoft Docs'
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
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a45e949733acc923c4d4dc2ab5ee102ee8367ff6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280142"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|Identificador de comprobación|CA2136|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Esta regla se desencadena cuando un miembro de tipo se marca con un <xref:System.Security> atributo de seguridad que tiene una transparencia diferente que el atributo de seguridad de un contenedor del miembro.

## <a name="rule-description"></a>Descripción de la regla
 Los atributos de transparencia se aplican de los elementos de código de ámbito mayor a los elementos de ámbito menor. Los atributos de transparencia de los elementos de código con mayor ámbito tienen prioridad sobre los atributos de transparencia de los elementos de código incluidos en el primer elemento. Por ejemplo, una clase marcada con el <xref:System.Security.SecurityCriticalAttribute> atributo no puede contener un método marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, quite el atributo de seguridad desde el elemento de código que tiene un ámbito inferior o cambie su atributo para que sea el mismo que el elemento de código que lo contiene.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, un método está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo y es un miembro de una clase marcada con el <xref:System.Security.SecurityCriticalAttribute> atributo. El atributo de prueba de errores de seguridad se debe quitar.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]



