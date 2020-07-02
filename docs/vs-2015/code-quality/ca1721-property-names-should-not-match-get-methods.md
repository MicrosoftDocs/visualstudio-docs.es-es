---
title: 'CA1721: los nombres de propiedad no deben coincidir con los métodos Get | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 77ec48a1164c7065ba5033ef51eb704b8361dc1c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544461"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Los nombres de propiedades no deben coincidir con los métodos get
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|Identificador de comprobación|CA1721|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El nombre de un miembro público o protegido comienza con ' get ' y, de lo contrario, coincide con el nombre de una propiedad pública o protegida. Por ejemplo, un tipo que contiene un método denominado ' GetColor ' y una propiedad denominada ' color ' infringe esta regla.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos y las propiedades Get deben tener nombres que diferencien claramente su función.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo necesario para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre para que no coincida con el nombre de un método que tiene el prefijo ' get '.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

> [!NOTE]
> Esta advertencia se puede excluir si el método get se debe a la implementación de la interfaz IExtenderProvider.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un método y una propiedad que infringen esta regla.

 [!code-csharp[FxCop.Naming.GetMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/cs/FxCop.Naming.GetMethod.cs#1)]
 [!code-vb[FxCop.Naming.GetMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod/vb/FxCop.Naming.GetMethod.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
