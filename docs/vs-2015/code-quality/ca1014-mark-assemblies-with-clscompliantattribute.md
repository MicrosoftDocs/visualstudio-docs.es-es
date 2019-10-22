---
title: 'CA1014: Marque los ensamblados con CLSCompliantAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9408a7b55c800a7979c39075afdf8e9e6e4c7cdb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663159"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Marcar los ensamblados con CLSCompliantAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|Identificador de comprobación|CA1014|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un ensamblado no tiene aplicado el atributo <xref:System.CLSCompliantAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Un buen diseño determina que todos los ensamblados indican explícitamente la conformidad con CLS con <xref:System.CLSCompliantAttribute>. Si el atributo no está presente en un ensamblado, el ensamblado no es compatible.

 Es posible que un ensamblado conforme a CLS contenga tipos o miembros de tipo que no sean compatibles.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado. En lugar de marcar todo el ensamblado como no conforme, debe determinar qué tipo o miembros de tipo no son compatibles y marcar estos elementos como tales. Si es posible, debe proporcionar una alternativa conforme a CLS para los miembros no conformes, de modo que la audiencia más amplia posible pueda acceder a toda la funcionalidad del ensamblado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Si no desea que el ensamblado sea compatible, aplique el atributo y establezca su valor en `false`.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un ensamblado que tiene aplicado el atributo <xref:System.CLSCompliantAttribute?displayProperty=fullName> que lo declara conforme a CLS.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Vea también
 [independencia del lenguaje <xref:System.CLSCompliantAttribute?displayProperty=fullName> y componentes independientes del lenguaje](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
