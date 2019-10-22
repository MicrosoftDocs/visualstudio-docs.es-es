---
title: 'CA1026: no se deben usar los parámetros predeterminados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8fffbdc2cf9f4e09fe98c8e14b6692802ab3f275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661942"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: No debería utilizar parámetros predeterminados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|Identificador de comprobación|CA1026|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos que utilizan parámetros predeterminados se permiten en el Common Language Specification (CLS); sin embargo, CLS permite a los compiladores omitir los valores que se asignan a estos parámetros. El código que se escribe para los compiladores que omiten los valores de parámetro predeterminados debe proporcionar explícitamente argumentos para cada parámetro predeterminado. Para mantener el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deben reemplazarse por sobrecargas de método que proporcionan los parámetros predeterminados.

 El compilador omite los valores de los parámetros predeterminados C++ para la extensión administrada para cuando tiene acceso al código administrado. El compilador Visual Basic admite métodos que tienen parámetros predeterminados que utilizan la palabra clave [opcional](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el método que usa los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que usa parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vea también
 [Independencia del lenguaje y componentes independientes del lenguaje](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
