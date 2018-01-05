---
title: "CA2146: Los tipos deben ser al menos tan críticos como sus tipos base e interfaces | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6e2ed089ee94a6d88e51c9c69e93b515db7e7fa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Los tipos deben ser al menos tan críticos para la seguridad como sus interfaces y tipos base
|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|Identificador de comprobación|CA2146|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo transparente se deriva de un tipo que se marca con la <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>, o un tipo que se marca con la <xref:System.Security.SecuritySafeCriticalAttribute> atributo se deriva de un tipo que se marca con el <xref:System.Security.SecurityCriticalAttribute> atributo.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla se desencadena cuando un tipo derivado tiene un atributo de transparencia de seguridad que no es tan crítico como su tipo base o interfaz implementada. Solo los tipos críticos pueden derivar de los tipos base críticos o implementar interfaces críticas, y solo los tipos críticos o críticos para la seguridad pueden derivar de tipos base críticos para la seguridad o implementar interfaces críticas para la seguridad. Las infracciones de esta regla de transparencia de nivel 2 como resultado un <xref:System.TypeLoadException> para el tipo derivado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir esta infracción, marque el tipo derivado o que implementa con un atributo de transparencia es al menos tan crítico como el tipo base o interfaz.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]