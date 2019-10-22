---
title: 'CA2112: los tipos seguros no deben exponer campos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c91a7c9833d3d9d5ae283c28ae4d437bd07734
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658745"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Los tipos seguros no deberían exponer campos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|Identificador de comprobación|CA2112|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene campos públicos y está protegido por una [petición de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descripción de la regla
 Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, haga que los campos sean no públicos y agregue propiedades o métodos públicos que devuelvan los datos de campo. Las comprobaciones de seguridad de LinkDemand en tipos protegen el acceso a las propiedades y los métodos del tipo. Sin embargo, la seguridad de acceso del código no se aplica a los campos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Tanto para los problemas de seguridad como para un buen diseño, debe corregir las infracciones haciendo que los campos públicos sean no públicos. Puede suprimir una advertencia de esta regla si el campo no contiene información que deba permanecer protegida y no se basa en el contenido del campo.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente se compone de un tipo de biblioteca (`SecuredTypeWithFields`) con campos no seguros, un tipo (`Distributor`) que puede crear instancias del tipo de biblioteca y las instancias de pasadas erróneas a tipos no tienen permiso para crearlas, y el código de aplicación que puede leer un los campos de la instancia aunque no tengan el permiso que protege el tipo.

 El código de biblioteca siguiente infringe la regla.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación no puede crear una instancia debido a la petición de vínculo que protege el tipo protegido. La siguiente clase permite a la aplicación obtener una instancia del tipo protegido.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación muestra cómo, sin permiso para tener acceso a los métodos de un tipo protegido, el código puede tener acceso a sus campos.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Crear una instancia de SecuredTypeWithFields.** 
**campos de tipo protegidos: 22, 33** 
**cambiar el campo del tipo protegido...** 
**campos de objeto en caché: 99, 33**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también
 [Link solicita](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
