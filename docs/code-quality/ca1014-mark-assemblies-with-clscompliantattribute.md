---
title: 'CA1014: Marcar los ensamblados con CLSCompliantAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 273eee55db6ea9c8cbd57573da1ec82a804a21d2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940036"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Marcar los ensamblados con CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|Identificador de comprobación|CA1014|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un ensamblado no tiene el <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado a él.

## <a name="rule-description"></a>Descripción de la regla
 La Common Language Specification (CLS) define las restricciones de nomenclatura, los tipos de datos y las reglas a las que los ensamblados deben ajustarse si se van a utilizar los lenguajes de programación. Un buen diseño determina que todos los ensamblados indican explícitamente la conformidad con CLS <xref:System.CLSCompliantAttribute>. Si el atributo no está presente en un ensamblado, el ensamblado no es compatible.

 Es posible que un ensamblado conforme a CLS contenga tipos o miembros de tipo que no son compatibles.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado. En lugar de marcar el ensamblado completo como no conforme, debe determinar qué tipo o miembros de tipo no son compatibles y marcan estos elementos como tales. Si es posible, debe proporcionar una alternativa conforme a CLS para los miembros no conformes para que el público más amplio posible puede tener acceso a toda la funcionalidad del ensamblado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Si no desea que el ensamblado sea compatible, aplique el atributo y establezca su valor en `false`.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un ensamblado que tiene el <xref:System.CLSCompliantAttribute?displayProperty=fullName> atributo aplicado que lo declara como conforme a CLS.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Vea también

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)