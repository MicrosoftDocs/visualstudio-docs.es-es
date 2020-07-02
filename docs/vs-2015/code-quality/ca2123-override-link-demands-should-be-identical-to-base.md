---
title: 'CA2123: la invalidación de las peticiones de vínculo debe ser idéntica a la base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a722eb95561a1a81b0d17b8876df8b4bac048b5c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544266"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Las peticiones de vínculos de invalidaciones deben ser idénticas a la base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|Identificador de comprobación|CA2123|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método público o protegido en un tipo público invalida un método o implementa una interfaz, y no tiene las mismas [peticiones de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) que la interfaz o el método virtual.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla compara un método con su método base, que es una interfaz o un método virtual de otro tipo y, a continuación, compara las solicitudes de vínculos en cada uno. Se detecta una infracción si el método o el método base tiene una petición de vínculo y el otro no.

 Si se infringe esta regla, un llamador malintencionado puede omitir la petición de vínculo simplemente llamando al método no seguro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique la misma petición de vínculo al método de anulación o a la implementación. Si esto no es posible, marque el método con una demanda completa o quite el atributo por completo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran varias infracciones de esta regla.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Consulte también
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [peticiones de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
