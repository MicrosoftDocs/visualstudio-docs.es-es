---
title: 'CA1725: Los nombres de parámetro deben coincidir con la declaración base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54a7926cd0bf8eb2ebf526c1f19a00c71960900c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917693"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Los nombres de parámetro deben coincidir con la declaración base

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|Identificador de comprobación|CA1725|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un parámetro en un reemplazo de método visible externamente no coincide con el nombre del parámetro en la declaración del método base, o el nombre del parámetro en la declaración del método de interfaz.

## <a name="rule-description"></a>Descripción de la regla
 El uso del mismo nombre para un parámetro en una jerarquía de reemplazo aumenta la utilidad de los reemplazos de método. Cuando el nombre de un parámetro en un método derivado es distinto del nombre de la declaración base, puede resultar difícil determinar si el método es un reemplazo del método base o una nueva sobrecarga del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el nombre del parámetro para que coincida con la declaración base. La solución es un cambio importante para los métodos COM visibles.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia de esta regla excepto para los métodos visibles COM en las bibliotecas que se han enviado anteriormente.