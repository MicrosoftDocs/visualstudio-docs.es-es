---
title: 'CA1505: Evite código que no | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee836af1ee0030c3eea56e12ea5fe767c4b7255b
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591685"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitar el código difícil de mantener
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1505: Evite código que no](https://docs.microsoft.com/visualstudio/code-quality/ca1505-avoid-unmaintainable-code).

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|Identificador de comprobación|CA1505|
|Categoría|Microsoft.Maintainability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo o método tiene un valor del índice de mantenimiento bajo.

## <a name="rule-description"></a>Descripción de la regla
 El índice de mantenimiento se calcula mediante el uso de las siguientes métricas: líneas de código, el volumen del programa y complejidad ciclomática. Volumen del programa es una medida de la dificultad de comprensión de un tipo o método que se basa en el número de operadores y operandos en el código. Complejidad ciclomática es una medida de la complejidad estructural del tipo o método. Puede aprender más acerca de las métricas de código en [medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y sería un buen candidato para volver a diseñar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir esta infracción, vuelva a diseñar el tipo o método e intente dividir más corta y tipos o métodos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Excluir esta advertencia cuando un tipo o método se sigue considerando fácil de mantener a pesar de su gran tamaño o cuando no se puede dividir el tipo o método.

## <a name="see-also"></a>Vea también
 [Las advertencias de mantenimiento](../code-quality/maintainability-warnings.md) [medir la complejidad y mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



