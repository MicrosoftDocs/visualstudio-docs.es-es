---
title: 'CA1405: Tipos bases de tipos visibles COM deben ser visibles para COM | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f284c0e6e57a2ca359e765992db3f2d599fec328
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705744"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|Identificador de comprobación|CA1405|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|DependsOnFix|

## <a name="cause"></a>Motivo
 Un tipo visible del modelo de objetos componentes (COM) se deriva de un tipo que no es visible para COM.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo visible COM agrega miembros en una nueva versión, debe cumplir las instrucciones estrictas para evitar que los clientes COM que se enlazan a la versión actual. Un tipo que no es visible para COM se da por supuesto que no tiene que seguir estas reglas de control de versiones de COM cuando agrega nuevos miembros. Sin embargo, si un visibles para COM tipo deriva del tipo visible COM y expone una interfaz de clase de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (valor predeterminado), todos los miembros públicos del tipo base (a menos que se marcado específicamente como COM invisibles, que sería redundante) se expone a COM. Si el tipo base agrega a nuevos miembros en una versión posterior, todos los clientes COM que se enlazan a la interfaz de clase del tipo derivado que se interrumpa. Los tipos visibles COM deben derivar solo de los tipos visibles COM para reducir la posibilidad de que los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, hacer que los tipos base visibles para COM o el tipo derivado COM sea invisible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName> [Introducción a la interfaz de clase](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interoperar con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
