---
title: 'CA1800: No convertir innecesariamente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed2769bae5cf99fdaf8545e8ad0ac2a60a58b038
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854910"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: No convertir innecesariamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|Identificador de comprobación|CA1800|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método realiza conversiones de tipos duplicadas en uno de sus argumentos o variables locales. Para el análisis completo por esta regla, se debe generar el ensamblado probado utilizando la información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. Para las operaciones de conversión explícita de duplicados, almacena el resultado de la conversión en una variable local y use la variable local en lugar de las operaciones de conversión duplicadas.

 Si C# `is` operador se usa para comprobar si la conversión se realizará correctamente antes de realiza la conversión real, considere la posibilidad de probar el resultado de la `as` operador en su lugar. Esto proporciona la misma funcionalidad sin la operación de conversión implícita que se realiza mediante el `is` operador.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, modifique la implementación del método para minimizar el número de operaciones de conversión.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla u omitir completamente, la regla si el rendimiento no constituye un problema.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que infringe la regla mediante el uso de C# `is` operador. Un segundo método cumple la regla reemplazando el `is` operador con una prueba con el resultado de la `as` operador, lo que disminuye el número de operaciones de conversión por iteración de dos a uno.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método, `start_Click`, que tiene varias conversiones explícitas duplicadas, lo que infringe la regla y un método, `reset_Click`, que cumple la regla almacenando la conversión en una variable local.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Vea también
 [como](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [es](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)



