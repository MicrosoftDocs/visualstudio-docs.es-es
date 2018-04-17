---
title: 'CA2123: Las peticiones de vínculo de invalidación deben ser idénticas al basar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c23bdf9246855fc4a91d5cd5f748f8f8fb17a67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Las peticiones de vínculos de reemplazo deberían ser idénticas a la base
|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|Identificador de comprobación|CA2123|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método público o protegido en un tipo público reemplaza a un método o implementa una interfaz y no tiene el mismo [peticiones de vínculo](/dotnet/framework/misc/link-demands) como la interfaz o un método virtual.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Esta regla compara un método con su método base, que es una interfaz o un método virtual de otro tipo y, a continuación, compara las solicitudes de vínculos en cada uno. Se notifica una infracción si el método o el método base tiene una petición de vínculo y el otro no.  
  
 Si se infringe esta regla, un llamador malintencionado puede omitir la petición de vínculo simplemente llamando al método no seguro.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, aplique la misma petición de vínculo para el método de reemplazo o la implementación. Si esto no es posible, marque el método con una demanda completa o quite el atributo por completo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra distintas infracciones de esta regla.  
  
 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Peticiones de vínculo](/dotnet/framework/misc/link-demands)