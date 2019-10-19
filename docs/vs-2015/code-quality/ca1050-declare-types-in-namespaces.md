---
title: 'CA1050: declarar tipos en espacios de nombres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c56de70daeabd05215f68024339d5855686d529b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653829"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Declare tipos en espacios de nombres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|Identificador de comprobación|CA1050|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido se define fuera del ámbito de un espacio de nombres con nombre.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos se declaran en los espacios de nombres para evitar conflictos de nombres y como una manera de organizar los tipos relacionados en una jerarquía de objetos. Los tipos que están fuera de un espacio de nombres con nombre se encuentran en un espacio de nombres global al que no se puede hacer referencia en el código.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, coloque el tipo en un espacio de nombres.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Aunque nunca tenga que suprimir una advertencia de esta regla, es seguro hacerlo cuando el ensamblado nunca se usará junto con otros ensamblados.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una biblioteca que tiene un tipo declarado incorrectamente fuera de un espacio de nombres y un tipo con el mismo nombre declarado en un espacio de nombres.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación usa la biblioteca que se definió anteriormente. Tenga en cuenta que el tipo que se declara fuera de un espacio de nombres se crea cuando el nombre `Test` no está calificado por un espacio de nombres. Tenga en cuenta también que para tener acceso al tipo de `Test` en `Goodspace`, se requiere el nombre del espacio de nombres.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
