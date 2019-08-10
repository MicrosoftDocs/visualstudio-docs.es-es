---
title: 'CA1014: Marcar los ensamblados con CLSCompliantAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f11a93380f149648ece4ae6d71bc9c2f25df5191
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923119"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Marcar los ensamblados con CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|Identificador de comprobación|CA1014|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un ensamblado no tiene aplicado <xref:System.CLSCompliantAttribute?displayProperty=fullName> el atributo.

## <a name="rule-description"></a>Descripción de la regla
La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Un buen diseño determina que todos los ensamblados indican explícitamente <xref:System.CLSCompliantAttribute>la conformidad con CLS. Si el atributo no está presente en un ensamblado, el ensamblado no es compatible.

Es posible que un ensamblado conforme a CLS contenga tipos o miembros de tipo que no sean compatibles.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue el atributo al ensamblado. En lugar de marcar todo el ensamblado como no conforme, debe determinar qué tipo o miembros de tipo no son compatibles y marcar estos elementos como tales. Si es posible, debe proporcionar una alternativa conforme a CLS para los miembros no conformes, de modo que la audiencia más amplia posible pueda acceder a toda la funcionalidad del ensamblado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Si no desea que el ensamblado sea compatible, aplique el atributo y establezca su valor en `false`.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un ensamblado <xref:System.CLSCompliantAttribute?displayProperty=fullName> que tiene aplicado el atributo que lo declara como conforme a CLS.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Vea también

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)