---
title: 'CA1804: Quitar variables locales no utilizadas | Microsoft Docs'
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
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b2d54383061d9d033ad368b05121e794f761f219
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591290"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Quitar variables locales no utilizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1804: quitar variables locales no utilizadas](https://docs.microsoft.com/visualstudio/code-quality/ca1804-remove-unused-locals).

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|Identificador de comprobación|CA1804|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método declara una variable local pero no utiliza la variable excepto posiblemente como destinatario de una instrucción de asignación. Para el análisis por esta regla, el ensamblado probado debe compilarse con información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
 Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o use la variable local. Tenga en cuenta que el compilador de C# que se incluye con [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] quita sin usar las variables locales cuando el `optimize` está habilitada.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si la variable generó el compilador. También es seguro suprimir una advertencia de esta regla, o para deshabilitar la regla, si el rendimiento y mantenimiento del código no son principales preocupaciones.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra varias variables locales no usadas.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1809: Evitar variables locales excesivas](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)



