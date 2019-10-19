---
title: 'CA1800: no convertir innecesariamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663104"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: No convertir innecesariamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|Identificador de comprobación|CA1800|
|Categoría|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método realiza conversiones duplicadas en uno de sus argumentos o variables locales. Para realizar un análisis completo de esta regla, el ensamblado probado se debe compilar con la información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. En el caso de operaciones de conversión duplicadas explícitas, almacene el resultado de la conversión en una variable local y use la variable local en lugar de las operaciones de conversión duplicada.

 Si el C# operador `is` se usa para comprobar si la conversión se realizará correctamente antes de que se realice la conversión real, considere la posibilidad de probar el resultado del operador `as` en su lugar. Esto proporciona la misma funcionalidad sin la operación de conversión implícita que realiza el operador `is`.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, modifique la implementación del método para minimizar el número de operaciones de conversión.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla o pasar por alto la regla por completo si el rendimiento no es un problema.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe la regla mediante el C# operador `is`. Un segundo método cumple la regla reemplazando el operador `is` por una prueba con el resultado del operador `as`, lo que reduce el número de operaciones de conversión por iteración de dos a uno.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `start_Click`, que tiene varias conversiones explícitas duplicadas, que infringe la regla, y un método, `reset_Click`, que cumple la regla almacenando la conversión en una variable local.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Vea también
 [tal y como](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [está](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
