---
title: 'CA2122: No exponer indirectamente métodos con peticiones de vínculo | Microsoft Docs'
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
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 563805fdd8ba8c30e9fb241cc24136ad0c9e9e06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912843"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: No exponer indirectamente métodos con peticiones de vínculos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|Identificador de comprobación|CA2122|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un miembro público o protegido tiene un [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) y se llama a un miembro que no realiza ninguna comprobación de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. Si un miembro `X` ningún demandas de seguridad de sus llamadores y las llamadas de código protegido por una petición de vínculo, un llamador sin el permiso necesario puede utilizar `X` para tener acceso al miembro protegido.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Agregar una seguridad [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o vincular a petición para el miembro de modo que ya no proporciona acceso no seguro al miembro protegido por solicitud de vínculo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no tiene acceso a las operaciones o los recursos que se pueden usar de forma destructiva sus llamadores.

## <a name="example"></a>Ejemplo
 Los ejemplos siguientes muestran una biblioteca que infringe la regla y una aplicación que muestra el punto débil de la biblioteca. La biblioteca de ejemplo proporciona dos métodos que juntos infringen la regla. El `EnvironmentSetting` método está protegido por una petición de vínculo para el acceso sin restricciones a las variables de entorno. El `DomainInformation` método no realiza ninguna petición de seguridad de sus llamadores antes de llamar a `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación llama al miembro de biblioteca no segura.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Valor de miembro no segura: seattle.corp.contoso.com**
## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [peticiones de vínculos](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



