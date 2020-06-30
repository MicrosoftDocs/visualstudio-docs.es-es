---
title: 'CA2108: revisar la seguridad declarativa en los tipos de valor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03918353b66c36698b5d17b332da052b6d95c87a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544396"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Revisar la seguridad declarativa en los tipos de valores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|Identificador de comprobación|CA2108|
|Category|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un tipo de valor público o protegido está protegido por una petición de [datos y de modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o de [vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descripción de la regla
 Los tipos de valor se asignan y se inicializan por sus constructores predeterminados antes de que se ejecuten otros constructores. Si un tipo de valor está protegido por una petición o LinkDemand, y el llamador no tiene permisos que satisfagan la comprobación de seguridad, se producirá un error en cualquier constructor distinto del predeterminado y se producirá una excepción de seguridad. No se cancela la asignación del tipo de valor. se deja en el estado establecido por su constructor predeterminado. No asuma que un llamador que pase una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 No se puede corregir una infracción de esta regla a menos que quite la comprobación de seguridad del tipo y use comprobaciones de seguridad de nivel de método en su lugar. Tenga en cuenta que la corrección de esta infracción no impedirá que los llamadores con permisos inadecuados obtengan instancias del tipo de valor. Debe asegurarse de que una instancia del tipo de valor, en su estado predeterminado, no exponga información confidencial y no se pueda usar de forma dañina.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si cualquier llamador puede obtener instancias del tipo de valor en su estado predeterminado sin poner en peligro la seguridad.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una biblioteca que contiene un tipo de valor que infringe esta regla. Tenga en cuenta que el `StructureManager` tipo supone que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación muestra la debilidad de la biblioteca.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Constructor personalizado de estructura: error en la solicitud.** 
 **Nuevos valores SecuredTypeStructure 100 100** 
 **Nuevos valores SecuredTypeStructure 200 200**
## <a name="see-also"></a>Consulte también
 [Link solicita](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
