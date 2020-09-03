---
title: 'CA2122: no exponer indirectamente métodos con peticiones de vínculo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544331"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: No exponer indirectamente métodos con peticiones de vínculos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|Identificador de comprobación|CA2122|
|Category|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un miembro público o protegido tiene una [petición de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) y lo llama un miembro que no realiza ninguna comprobación de seguridad.

## <a name="rule-description"></a>Descripción de la regla
 Una solicitud de vínculo sólo comprueba los permisos del llamador inmediato. Si un miembro `X` no realiza ninguna solicitud de seguridad de sus llamadores y llama al código protegido por una petición de vínculo, un llamador sin el permiso necesario puede utilizar `X` para tener acceso al miembro protegido.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Agregue datos de seguridad [y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o petición de vínculo al miembro para que ya no proporcione acceso no seguro al miembro protegido por petición de vínculo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir de forma segura una advertencia de esta regla, debe asegurarse de que el código no concede a sus llamadores acceso a las operaciones o recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 En los siguientes ejemplos se muestra una biblioteca que infringe la regla y una aplicación que muestra la debilidad de la biblioteca. La biblioteca de ejemplo proporciona dos métodos que juntos infringen la regla. El `EnvironmentSetting` método está protegido por una petición de vínculo para el acceso no restringido a las variables de entorno. El `DomainInformation` método no realiza ninguna petición de seguridad de sus llamadores antes de llamar a `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación llama al miembro de biblioteca no seguro.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Valor de miembro no seguro: seattle.corp.contoso.com**
## <a name="see-also"></a>Consulte también
 El vínculo de las [instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [exige](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
