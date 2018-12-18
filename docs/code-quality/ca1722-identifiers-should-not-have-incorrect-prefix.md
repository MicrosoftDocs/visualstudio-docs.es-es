---
title: 'CA1722: Los identificadores no deberían tener el prefijo incorrecto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ff21b8f3c12cfa9fb3dc3ef03ca2ba2040f3769
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857624"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Los identificadores no deberían tener el prefijo incorrecto

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|Identificador de comprobación|CA1722|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un identificador tiene un prefijo incorrecto.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.

 Los nombres de tipo no tienen un prefijo específico y no se deberían prefijar con una 'C'. Esta regla notifica las infracciones de nombres de tipo como 'CMyClass' y no notifica las infracciones para nombres de tipo como 'Cache'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esta coherencia reduce la curva de aprendizaje necesario para las nuevas bibliotecas de software y aumenta la confianza del cliente que la biblioteca fue desarrollada por alguien que tenga experiencia en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el prefijo de identificador.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1715: Los identificadores deberían tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)