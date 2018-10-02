---
title: 'CA1016: Marcar los ensamblados con AssemblyVersionAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7fbc3fa747171892066705ddc32a114cb34e1b02
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858180"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Marcar los ensamblados con AssemblyVersionAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|Identificador de comprobación|CA1016|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

El ensamblado no tiene un número de versión.

## <a name="rule-description"></a>Descripción de la regla

La identidad de un ensamblado se compone de la siguiente información:

- Nombre del ensamblado

- Número de versión

- culture

- Clave pública (para ensamblados con nombre seguro).

.NET Framework usa el número de versión para identificar de forma única un ensamblado y enlazar a tipos en ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar un número de versión al ensamblado mediante la <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributo. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia de esta regla para los ensamblados que se utilizan por parte de terceros, o en un entorno de producción.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un ensamblado que tiene el <xref:System.Reflection.AssemblyVersionAttribute> atributo aplicado.

 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]

## <a name="see-also"></a>Vea también

- [Versiones de los ensamblados](/dotnet/framework/app-domains/assembly-versioning)
- [Cómo: Crear una directiva de publicador](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)