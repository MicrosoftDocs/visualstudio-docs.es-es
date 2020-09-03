---
title: 'CA2226: los operadores deben tener sobrecargas simétricas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540574"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: Los operadores deben tener sobrecargas simétricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|Identificador de comprobación|CA2226|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo implementa el operador de igualdad o de desigualdad y no implementa el operador opuesto.

## <a name="rule-description"></a>Descripción de la regla
 No hay circunstancias en las que la igualdad o la desigualdad se aplican a las instancias de un tipo, y el operador opuesto es indefinido. Normalmente, los tipos implementan el operador de desigualdad devolviendo el valor negado del operador de igualdad.

 El compilador de C# emite un error para las infracciones de esta regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente los operadores de igualdad y desigualdad, o bien Quite el que está presente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. El tipo no funcionará de forma coherente con [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="related-rules"></a>Reglas relacionadas
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Invalidar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Invalidar el método GetHashCode al invalidar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Sobrecargar el operador equals al invalidar ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
