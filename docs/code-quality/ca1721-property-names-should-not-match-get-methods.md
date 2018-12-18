---
title: 'CA1721: Los nombres de propiedades no deberían coincidir con los métodos Get'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 26f6e23a340ec018f766477f0bdce089a43ca3e4
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549682"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Los nombres de propiedades no deberían coincidir con los métodos Get

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|Identificador de comprobación|CA1721|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un miembro público o protegido empieza por 'Get' y en caso contrario, coincide con el nombre de una propiedad pública o protegida. Por ejemplo, un tipo que contiene un método que se denomina 'GetColor' y una propiedad que se denomina 'Color' infringe esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Propiedades y métodos Get deberían tener nombres que distingan claramente su función.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esta coherencia reduce el tiempo necesario para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente que la biblioteca fue desarrollada por alguien que tenga experiencia en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre para que no coincide con el nombre de un método que va precedido de 'Get'.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

> [!NOTE]
> Si se produce el método Get implementando IExtenderProvider (interfaz), se puede excluir esta advertencia.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un método y propiedad que infringen esta regla.

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)