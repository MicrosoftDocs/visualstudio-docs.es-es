---
title: 'CA1047: No declarar miembros protegidos en tipos sealed | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: abdde6524f179cff3a1dd368cf218a91499f5381
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: No declarar miembros protegidos en tipos sealed
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|Identificador de comprobación|CA1047|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Es un tipo público `sealed` (`NotInheritable` en Visual basic) y declara un miembro protegido o un tipo anidado protegido. Esta regla no informa de las infracciones de <xref:System.Object.Finalize%2A> métodos, que deben seguir este patrón.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los tipos declaran miembros protegidos para que los tipos heredados puedan obtener acceso o reemplazar el miembro. Por definición, no se puede heredar de un tipo sealed, lo que significa que los métodos protegidos en tipos sealed no se puede llamar.  
  
 El compilador de C# emite una advertencia para este error.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nivel de acceso del miembro privado o hacer que el tipo puede heredar.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Dejar el tipo en su estado actual puede causar problemas de mantenimiento y no proporciona ninguna ventaja.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]