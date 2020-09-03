---
title: 'CA1405: los tipos base de tipo visible COM deben ser visibles para COM | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779d3ec1ed520d5d48043f90e7cb6272553012a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535049"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Los tipos base de tipos visibles a través de COM deben ser visibles a través de COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|Identificador de comprobación|CA1405|
|Category|Microsoft. Interoperability|
|Cambio problemático|DependsOnFix|

## <a name="cause"></a>Causa
 Un tipo visible del modelo de objetos componentes (COM) deriva de un tipo que no es visible para COM.

## <a name="rule-description"></a>Descripción de la regla
 Cuando un tipo visible para COM agrega miembros en una nueva versión, debe cumplir instrucciones estrictas para evitar la interrupción de los clientes COM que se enlazan a la versión actual. Un tipo que no es visible para COM presupone que no tiene que seguir estas reglas de control de versiones COM cuando agrega nuevos miembros. Sin embargo, si un tipo visible COM deriva del tipo COM invisible y expone una interfaz de clase de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ClassInterfaceType> (el valor predeterminado), todos los miembros públicos del tipo base (a menos que se marquen específicamente como com invisible, que serían redundantes), se exponen a com. Si el tipo base agrega nuevos miembros en una versión posterior, los clientes COM que se enlazan a la interfaz de clase del tipo derivado podrían interrumpirse. Los tipos visibles para COM solo se deben derivar de tipos visibles para COM para reducir la posibilidad de interrumpir los clientes COM.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que los tipos base COM sean visibles o el tipo derivado de COM invisible.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/cs/FxCop.Interoperability.ComBaseTypes.cs#1)]
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComBaseTypes/vb/FxCop.Interoperability.ComBaseTypes.vb#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>[Introducción a la interfaz de clase](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [interoperando con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
