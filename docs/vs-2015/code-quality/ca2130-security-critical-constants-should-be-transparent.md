---
title: 'CA2130: Las constantes críticas de seguridad deben ser transparentes | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d3b5389bb080dee6e550c4bc0e6c035fd15db2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996249"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Las constantes críticas para la seguridad deben ser transparentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|Identificador de comprobación|CA2130|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un campo constante o un miembro de enumeración se marca con el <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Descripción de la regla
 El cumplimiento de la transparencia no se exige para los valores constantes porque los compiladores alinean los valores constantes para que no se requiera ninguna búsqueda en tiempo de ejecución. Los campos constantes deberían ser transparentes en seguridad de modo que los revisores del código no supongan que el código transparente no puede tener acceso a la constante.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical del campo o valor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En los ejemplos siguientes, el valor de enumeración `EnumWithCriticalValues.CriticalEnumValue` y la constante `CriticalConstant` emitía esta advertencia. Para corregir los problemas, quite el [`SecurityCritical`] atributo para hacerlos seguridad transparente.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
