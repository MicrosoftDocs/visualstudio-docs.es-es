---
title: 'CA2123: Las peticiones de vínculos de invalidaciones deben ser idénticas a la base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b5bd062ca37ae477f5ab7d52d56fd7e4b4fb71b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232493"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Las peticiones de vínculos de invalidaciones deben ser idénticas a la base

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|Identificador de comprobación|CA2123|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un método público o protegido en un tipo público invalida un método o implementa una interfaz, y no tiene las mismas [peticiones de vínculo](/dotnet/framework/misc/link-demands) que la interfaz o el método virtual.

## <a name="rule-description"></a>Descripción de la regla
Esta regla compara un método con su método base, que es una interfaz o un método virtual de otro tipo y, a continuación, compara las solicitudes de vínculos en cada uno. Se detecta una infracción si el método o el método base tiene una petición de vínculo y el otro no.

Si se infringe esta regla, un llamador malintencionado puede omitir la petición de vínculo simplemente llamando al método no seguro.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, aplique la misma petición de vínculo al método o la implementación de invalidación. Si esto no es posible, marque el método con una demanda completa o quite el atributo por completo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran varias infracciones de esta regla.

[!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)