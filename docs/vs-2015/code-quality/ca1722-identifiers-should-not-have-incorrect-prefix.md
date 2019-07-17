---
title: 'CA1722: Los identificadores no deberían tener el prefijo incorrecto | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0c9aa6600578da0d9868df2ecff9992bff9e818c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191245"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Los identificadores no deben tener un prefijo incorrecto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Los nombres de tipo no tienen un prefijo específico y no se deberían prefijar con una 'C'. Esta regla notifica las infracciones de nombres de tipo como 'CMyClass' y no notifica las infracciones para nombres de tipo como 'Cache'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el prefijo de identificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1715: Los identificadores deberían tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)
