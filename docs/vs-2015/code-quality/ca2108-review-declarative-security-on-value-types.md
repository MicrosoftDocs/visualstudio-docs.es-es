---
title: 'CA2108: Revisar la seguridad declarativa en los tipos de valor | Microsoft Docs'
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
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 49159696edd713c85a44e48ee0e79ccd5acf2753
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284588"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Revisar la seguridad declarativa en los tipos de valor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|Identificador de comprobación|CA2108|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo de valor público o protegido está protegido por un [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descripción de la regla
 Tipos de valor se asigna y se inicializan por sus constructores predeterminados antes de ejecutan otros constructores. Si un tipo de valor está protegido por Demand o LinkDemand y el llamador no tiene los permisos que satisfacen la comprobación de seguridad, cualquier constructor que no sea el valor predeterminado se producirá un error y se producirá una excepción de seguridad. No se desasigna el tipo de valor; se deja en el estado establecido mediante su constructor predeterminado. No suponga que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 No se puede corregir una infracción de esta regla a menos que quite la comprobación de seguridad del tipo y comprobaciones de seguridad de nivel de método de uso en su lugar. Tenga en cuenta que corregir la infracción de esta manera no impedirá que los llamadores que tengan los permisos adecuados de obtención de instancias del tipo de valor. Debe asegurarse de que una instancia del tipo de valor, en su estado predeterminado, no expone información confidencial y no se puede usar de manera perjudicial.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si un llamador puede obtener instancias del tipo de valor en su estado predeterminado sin suponer una amenaza de seguridad.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una biblioteca que contiene un tipo de valor que infringe esta regla. Tenga en cuenta que el `StructureManager` tipo supone que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra el punto débil de la biblioteca.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **Constructor personalizado de estructura: error en la solicitud. ** 
 **Nuevos valores SecuredTypeStructure 100 100**
**SecuredTypeStructure 200 200 de nuevos valores**
## <a name="see-also"></a>Vea también
 [Las peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



