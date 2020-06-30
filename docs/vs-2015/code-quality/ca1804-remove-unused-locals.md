---
title: 'CA1804: quitar variables locales no utilizadas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543889"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Quitar variables locales no utilizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|RemoveUnusedLocals|
|Identificador de comprobación|CA1804|
|Category|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un método declara una variable local, pero no utiliza la variable, excepto posiblemente como el destinatario de una instrucción de asignación. Para el análisis de esta regla, el ensamblado probado se debe compilar con información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o use la variable local. Tenga en cuenta que el compilador de C# que se incluye con [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] quita las variables locales no utilizadas cuando `optimize` se habilita la opción.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si la variable se emitió en el compilador. También es seguro suprimir una advertencia de esta regla o deshabilitar la regla si el rendimiento y el mantenimiento del código no son problemas principales.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran varias variables locales no usadas.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1809: Evitar las variables locales excesivas](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)
