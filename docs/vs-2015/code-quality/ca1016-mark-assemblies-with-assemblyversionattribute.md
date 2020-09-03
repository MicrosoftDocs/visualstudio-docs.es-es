---
title: 'CA1016: Marque los ensamblados con AssemblyVersionAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 97bd41e51c8d6b5415ffb91c5696c7055f46cf7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545410"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016: Marcar los ensamblados con AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|Identificador de comprobación|CA1016|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 El ensamblado no tiene un número de versión.

## <a name="rule-description"></a>Descripción de la regla
 La identidad de un ensamblado se compone de la siguiente información:

- Nombre del ensamblado

- Número de versión

- Referencia cultural

- Clave pública (para ensamblados con nombre seguro).

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] utiliza el número de versión para identificar de forma única un ensamblado y para enlazarse a los tipos de ensamblados con nombre seguro. El número de versión se utiliza junto con la versión y la directiva del fabricante. De forma predeterminada, las aplicaciones sólo se ejecutan con la versión de ensamblado con la que se compilaron.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un número de versión al ensamblado mediante el <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> atributo. Consulte el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla para los ensamblados utilizados por terceros o en un entorno de producción.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un ensamblado que tiene <xref:System.Reflection.AssemblyVersionAttribute> aplicado el atributo.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Consulte también
 [Control de versiones de ensamblado](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Cómo: crear una directiva de edición](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
