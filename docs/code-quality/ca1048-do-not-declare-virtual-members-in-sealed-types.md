---
title: 'CA1048: No declarar miembros virtuales en tipos sealed | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b2b74ca86101949275e418968e577ca2b7c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: No declarar miembros virtuales en tipos sealed
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|Identificador de comprobación|CA1048|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público está sellado y declara un método que es `virtual` (`Overridable` en Visual Basic) y no final. Esta regla no informa de las infracciones para los tipos de delegado, que deben seguir este patrón.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los tipos declaran los métodos como virtuales para que los tipos heredados puedan reemplazar la implementación del método virtual. Por definición, no se puede heredar de un tipo sealed, pasa a un método virtual en un tipo sealed no tenga sentido.  
  
 Los compiladores de Visual Basic .NET y C# no permiten tipos infringir esta regla.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, haga que el método no virtual o hacer que el tipo puede heredar.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. Dejar el tipo en su estado actual puede causar problemas de mantenimiento y no proporciona ninguna ventaja.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe esta regla.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]