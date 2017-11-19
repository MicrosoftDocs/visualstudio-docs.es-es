---
title: "CA2122: No exponer indirectamente métodos con peticiones de vínculo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 00222c71e537856d420c6472efb104a8c928237e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: No exponer indirectamente métodos con peticiones de vínculos
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|Identificador de comprobación|CA2122|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un miembro público o protegido tiene un [peticiones de vínculo](/dotnet/framework/misc/link-demands) y llama a un miembro que no realiza ninguna comprobación de seguridad.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. Si un miembro `X` no hace ninguna petición de seguridad de sus llamadores y llama al código protegido por una petición de vínculo, un llamador sin el permiso necesario puede utilizar `X` para obtener acceso al miembro protegido.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Agregar una seguridad [datos y modelado](/dotnet/framework/data/index) o petición de vínculo al miembro para que ya no proporciona acceso no seguro al miembro protegido por solicitud de vínculo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que el código no concede a sus llamadores acceso a las operaciones o recursos que se pueden usar de forma destructiva.  
  
## <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran una biblioteca que infringe la regla y una aplicación que muestra la debilidad de la biblioteca. La biblioteca de ejemplos proporciona dos métodos que juntos infringen la regla. El `EnvironmentSetting` método está protegido por una petición de vínculo de acceso sin restricciones a las variables de entorno. El `DomainInformation` método no realiza ninguna petición de seguridad de sus llamadores antes de llamar a `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 La aplicación siguiente llama al miembro de biblioteca no seguro.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
 **Valor de miembro no segura: seattle.corp.contoso.com**   
## <a name="see-also"></a>Vea también  
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Peticiones de vínculo](/dotnet/framework/misc/link-demands)   
 [Datos y modelado](/dotnet/framework/data/index)