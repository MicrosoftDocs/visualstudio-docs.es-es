---
title: 'CA1016: Marcar los ensamblados con AssemblyVersionAttribute | Microsoft Docs'
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
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 72e079f08eb04a68185800e77b815464045259bb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591122"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Marcar los ensamblados con AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1016: marcar los ensamblados con AssemblyVersionAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca1016-mark-assemblies-with-assemblyversionattribute).

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

-   Nombre del ensamblado

-   Número de versión

-   culture

-   Clave pública (para ensamblados con nombre seguro).

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] utiliza el número de versión para identificar de forma única un ensamblado y para enlazarse a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar un número de versión al ensamblado mediante la <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributo. Vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla para los ensamblados que se utilizan por parte de terceros, o en un entorno de producción.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un ensamblado que tiene el <xref:System.Reflection.AssemblyVersionAttribute> atributo aplicado.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Vea también
 [Control de versiones de ensamblado](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Cómo: crear una directiva de publicador](http://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)



