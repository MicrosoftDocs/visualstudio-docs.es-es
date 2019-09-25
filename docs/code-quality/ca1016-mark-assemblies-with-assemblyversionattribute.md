---
title: 'CA1016: Marcar los ensamblados con AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 140037b025db88230762bc0d540d933cec7a5119
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236307"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Marcar los ensamblados con AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|Identificador de comprobación|CA1016|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

El ensamblado no tiene un número de versión.

## <a name="rule-description"></a>Descripción de la regla

La identidad de un ensamblado se compone de la siguiente información:

- Nombre del ensamblado

- Número de versión

- culture

- Clave pública (para ensamblados con nombre seguro).

.NET usa el número de versión para identificar de forma única un ensamblado y enlazar a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue un número de versión al ensamblado mediante <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> el atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla para los ensamblados utilizados por terceros o en un entorno de producción.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un ensamblado <xref:System.Reflection.AssemblyVersionAttribute> que tiene aplicado el atributo.

[!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
[!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
[!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Vea también

- [Control de versiones de los ensamblados](/dotnet/framework/app-domains/assembly-versioning)
- [Cómo: Crear una directiva de edición](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)