---
title: 'CA1721: Los nombres de propiedades no deberían coincidir con los métodos Get'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29db0561f15a16bf9b449f03f209feedf80dbd88
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Los nombres de propiedades no deberían coincidir con los métodos Get
|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|Identificador de comprobación|CA1721|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un miembro público o protegido comienza por 'Get' y en caso contrario, coincide con el nombre de una propiedad pública o protegida. Por ejemplo, un tipo que contiene un método denominado "GetColor" y una propiedad que se denomina 'Color' infringe esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Propiedades y métodos Get deberían tener nombres que distingan claramente su función.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo necesario para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente que la biblioteca se haya desarrollado por alguien que tenga experiencia en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre para que no coincide con el nombre de un método que tiene como prefijo 'Get'.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

> [!NOTE]
>  Es posible excluir esta advertencia si se produce el método Get mediante la implementación de interfaz IExtenderProvider.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un método y propiedad que infringen esta regla.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)