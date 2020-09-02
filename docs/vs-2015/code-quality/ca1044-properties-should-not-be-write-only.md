---
title: 'CA1044: las propiedades no deben ser de solo escritura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ca0fb61c0973553ee6d410bc8b2718d19aeb28c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546866"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Las propiedades no deben ser de solo escritura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|Identificador de comprobación|CA1044|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 La propiedad pública o protegida tiene un descriptor de acceso set pero no tiene un descriptor de acceso get.

## <a name="rule-description"></a>Descripción de la regla
 Los descriptores de acceso get proporcionan acceso de lectura a una propiedad y los descriptores de acceso proporcionan acceso de escritura. Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura. Esto se debe a que permitir que un usuario establezca un valor y, a continuación, impedir que el usuario vea el valor no proporciona ninguna seguridad. Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un descriptor de acceso get a la propiedad. Como alternativa, si el comportamiento de una propiedad de solo escritura es necesario, considere la posibilidad de convertir esta propiedad en un método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Se recomienda encarecidamente que no se suprima una advertencia de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, `BadClassWithWriteOnlyProperty` es un tipo con una propiedad de solo escritura. `GoodClassWithReadWriteProperty` contiene el código corregido.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
