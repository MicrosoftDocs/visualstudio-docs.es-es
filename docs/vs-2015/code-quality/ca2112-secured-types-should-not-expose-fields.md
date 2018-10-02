---
title: 'CA2112: Los tipos seguros no deberían exponer campos | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a904109e8308eb6984cc00222f2b7861bc0a4f6f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592376"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Los tipos seguros no deberían exponer campos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2112: los tipos seguros no deberían exponer campos](https://docs.microsoft.com/visualstudio/code-quality/ca2112-secured-types-should-not-expose-fields).

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|Identificador de comprobación|CA2112|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene campos públicos y está protegido por un [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descripción de la regla
 Si el código tiene acceso a una instancia de tipo que está protegida por una solicitud de vínculo, el código no cumplirá la solicitud para obtener acceso a los campos del tipo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, que los campos no públicos y agregue propiedades públicas o los métodos que devuelven los datos del campo. Comprobaciones de seguridad de LinkDemand en tipos de protegen el acceso a las propiedades y métodos del tipo. Sin embargo, la seguridad de acceso del código no es aplicable a los campos.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para problemas de seguridad y para un buen diseño, debe corregir las infracciones estableciendo el nonpublic campos públicos. Puede suprimir una advertencia de esta regla si el campo no contiene información que debe permanecer segura y no dependen del contenido del campo.

## <a name="example"></a>Ejemplo
 En el siguiente ejemplo se compone de un tipo de biblioteca (`SecuredTypeWithFields`) con campos no seguros, un tipo (`Distributor`) que puede crear instancias del tipo de biblioteca y las instancias pasadas errónea a tipos no tiene permiso para crearlos y código de aplicación puede leer los campos de la instancia, incluso aunque no tenga el permiso que protege el tipo.

 El siguiente código de biblioteca infringe la regla.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación no puede crear una instancia debido a la petición de vínculo que protege el tipo. La siguiente clase permite que la aplicación obtener una instancia del tipo protegido.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra cómo hacerlo, sin permiso para tener acceso a los métodos de un tipo seguro, código puede tener acceso a sus campos.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Crear una instancia de SecuredTypeWithFields. ** 
 **Campos de tipo segura: 22, 33**
**cambiar el campo de tipo protegido... ** 
 **Campos de objeto almacenado en caché: 99, 33**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Vea también
 [Las peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



