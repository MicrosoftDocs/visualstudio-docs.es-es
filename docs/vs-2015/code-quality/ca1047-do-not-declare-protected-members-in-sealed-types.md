---
title: 'CA1047: No declarar miembros protegidos en tipos sealed | Microsoft Docs'
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
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8a9c61d3910a550f957b9940c1280f4fd2c17bdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591289"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1047: no declarar miembros protegidos en tipos sealed](https://docs.microsoft.com/visualstudio/code-quality/ca1047-do-not-declare-protected-members-in-sealed-types).

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|Identificador de comprobación|CA1047|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Es un tipo público `sealed` (`NotInheritable` en Visual basic) y declara un miembro protegido o un tipo anidado protegido. Esta regla no informa de las infracciones de <xref:System.Object.Finalize%2A> métodos, que deben seguir este patrón.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no puede heredar de un tipo sealed, lo que significa que los métodos protegidos en tipos sellados no se puede llamar.

 El compilador de C# emite una advertencia para este error.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar el nivel de acceso del miembro en privado o hacer que el tipo sea heredable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Lo que deja el tipo en su estado actual puede causar problemas de mantenimiento y no proporciona ninguna ventaja.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]



