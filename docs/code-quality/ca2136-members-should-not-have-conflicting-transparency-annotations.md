---
title: 'CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75947139de74323006692c7427d3cf598cb9bc52
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto
|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|Identificador de comprobación|CA2136|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Esta regla se desencadena cuando un miembro de tipo se marca con un <xref:System.Security> atributo de seguridad que tiene una transparencia diferente que el atributo de seguridad de un contenedor del miembro.

## <a name="rule-description"></a>Descripción de la regla
 Los atributos de transparencia se aplican de los elementos de código de ámbito mayor a los elementos de ámbito menor. Los atributos de transparencia de los elementos de código con mayor ámbito tienen prioridad sobre los atributos de transparencia de los elementos de código incluidos en el primer elemento. Por ejemplo, una clase que se marca con la <xref:System.Security.SecurityCriticalAttribute> atributo no puede contener un método que se marca con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, quite el atributo de seguridad de elemento de código que tiene un ámbito inferior o cambie su atributo para que sea el mismo que el elemento de código que lo contiene.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, un método está marcado con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo y es miembro de una clase que se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo. La seguridad se debe quitar el atributo seguro.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]