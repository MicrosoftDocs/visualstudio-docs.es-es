---
title: 'CA1027: Marcar enumeraciones con FlagsAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b8cebc05fa58c589f07beed70ab222d31bc8553a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879225"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Marcar enumeraciones con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|Identificador de comprobación|CA1027|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Los valores de una enumeración pública son potencias de dos o combinaciones de otros valores que se definen en la enumeración, y el <xref:System.FlagsAttribute?displayProperty=fullName> atributo no está presente. Para reducir los falsos positivos, esta regla no notifica una infracción para las enumeraciones que tienen valores contiguos.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas. Aplicar <xref:System.FlagsAttribute> a una enumeración cuando se pueda combinar con sentido sus constantes con nombre. Por ejemplo, considere la posibilidad de una enumeración de los días de la semana en una aplicación que realiza un seguimiento de los recursos del día en que están disponibles. Si la disponibilidad de cada recurso se codifica mediante el uso de la enumeración que tiene <xref:System.FlagsAttribute> este momento, cualquier combinación de días que se puede representar. Sin el atributo, se puede representar un solo día de la semana.

 Para los campos que almacenan las enumeraciones combinables, los valores de enumeración individuales se tratan como grupos de bits en el campo. Por lo tanto, estos campos se conocen a veces como *campos de bits*. Para combinar valores de enumeración para el almacenamiento en un campo de bits, utilice los operadores booleanos condicionales. Para probar un campo de bits para determinar si existe un valor de enumeración específico, use los operadores lógicos booleanos. Para que un campo de bits almacenar y recuperar valores de enumeración combinado correctamente, cada valor que se define en la enumeración debe ser una potencia de dos. A menos que esto es así, los operadores lógicos booleanos no podrá extraer los valores de enumeración individuales que se almacenan en el campo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar <xref:System.FlagsAttribute> a la enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si no desea que los valores de enumeración sean combinables.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `DaysEnumNeedsFlags` es una enumeración que cumple los requisitos para usar <xref:System.FlagsAttribute>, pero no la tiene. El `ColorEnumShouldNotHaveFlag` enumeración no tiene valores que son potencias de dos, pero se especifica incorrectamente <xref:System.FlagsAttribute>. Esto infringe la regla [CA2217: no marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.FlagsAttribute?displayProperty=fullName>



