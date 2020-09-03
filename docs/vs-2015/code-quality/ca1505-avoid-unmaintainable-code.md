---
title: 'CA1505: evitar código que no se pueda mantener | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0f2f731b1ac0d87b59c7690d0cf57ade3570ed5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547828"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitar código que no se puede mantener
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidUnmantainableCode|
|Identificador de comprobación|CA1505|
|Category|Microsoft. mantenibilidad|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo o método tiene un valor del índice de mantenimiento bajo.

## <a name="rule-description"></a>Descripción de la regla
 El índice de mantenimiento se calcula con las siguientes métricas: líneas de código, volumen de programa y complejidad ciclomática. El volumen de programa es una medida de la dificultad de comprender un tipo o un método que se basa en el número de operadores y operandos del código. La complejidad ciclomática es una medida de la complejidad estructural del tipo o método. Puede obtener más información sobre las métricas de código al [medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un índice de mantenimiento bajo indica que un tipo o un método probablemente es difícil de mantener y sería un buen candidato para rediseñar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, vuelva a diseñar el tipo o método e intente dividirlo en tipos o métodos más pequeños y más centrados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Excluya esta advertencia cuando un tipo o método se siga considerando manteniéndose a pesar de su gran tamaño o cuando el tipo o el método no se puedan dividir.

## <a name="see-also"></a>Consulte también
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md) que [miden la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
