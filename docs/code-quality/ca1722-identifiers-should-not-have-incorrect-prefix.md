---
title: 'CA1722: Los identificadores no deben tener un prefijo incorrecto'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5daf51cd8bef4910a327b8e261f15332ad6522da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921621"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Los identificadores no deben tener un prefijo incorrecto

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|Identificador de comprobación|CA1722|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un identificador tiene un prefijo incorrecto.

## <a name="rule-description"></a>Descripción de la regla
Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.

Los nombres de tipo no tienen un prefijo específico y no deben ir precedidos de un ' C '. Esta regla notifica las infracciones de los nombres de tipo como ' CMyClass ' y no notifica las infracciones de los nombres de tipo como ' cache '.

Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esta coherencia reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Quite el prefijo del identificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
[CA1715: Los identificadores deben tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)