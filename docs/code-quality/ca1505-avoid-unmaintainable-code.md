---
title: 'CA1505: Evitar el código | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4338b73aab38b1d63f4d4015c3a1fe1e1d292932
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitar el código difícil de mantener
|||  
|-|-|  
|TypeName|AvoidUnmantainableCode|  
|Identificador de comprobación|CA1505|  
|Categoría|Microsoft.Maintainability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo o método tiene un valor del índice de mantenimiento bajo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El índice de mantenimiento se calcula utilizando las métricas siguientes: líneas de código, el volumen de programa y complejidad ciclomática. Volumen del programa es una medida de la dificultad de descripción de un tipo o método que se basa en el número de operadores y operandos en el código. Complejidad ciclomática es una medida de la complejidad estructural del tipo o método. Puede aprender más acerca de las métricas de código en [medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).  
  
 Un índice de mantenimiento bajo indica que un tipo o método resulta probablemente difícil de mantener y sería una buena candidata a diseñar.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir esta infracción, volver a diseñar el tipo o método e intente dividirlo en tipos acotará y delimitará o métodos.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Excluir esta advertencia cuando un tipo o método todavía se considera que se pueda mantener a pesar de su gran tamaño o cuando no se puede dividir el tipo o método.  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)   
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)