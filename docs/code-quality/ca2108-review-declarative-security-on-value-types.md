---
title: 'CA2108: Revisar la seguridad declarativa en los tipos de valor'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d07245724d70b5bc6ba69deae4311dcb2a10056
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Revisar la seguridad declarativa en los tipos de valor
|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|Identificador de comprobación|CA2108|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo de valor público o protegido está protegido por un [datos y modelado](/dotnet/framework/data/index) o [peticiones de vínculo](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descripción de la regla
 Tipos de valor se asignan y se inicializó sus constructores predeterminados antes de ejecutan otros constructores. Si un tipo de valor está protegido por una petición o LinkDemand y el llamador no tiene permisos que satisfacen la comprobación de seguridad, cualquier constructor distinto se producirá un error en el valor predeterminado y se producirá una excepción de seguridad. No se desasigna el tipo de valor; se mantiene en el estado establecido por su constructor predeterminado. No suponga que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 No se puede corregir una infracción de esta regla a menos que quite la comprobación de seguridad del tipo y comprobaciones de seguridad de nivel de método de uso en su lugar. Tenga en cuenta que corregir la infracción de esta manera no impedirá que los llamadores con permisos inadecuados obtengan instancias del tipo de valor. Debe asegurarse de que una instancia del tipo de valor, en su estado predeterminado, no exponga información confidencial y no se puede usar de manera perjudicial.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Puede suprimir una advertencia de esta regla si un llamador puede obtener instancias del tipo de valor en su estado predeterminado sin suponer una amenaza para la seguridad.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una biblioteca que contiene un tipo de valor que infringe esta regla. Tenga en cuenta que el `StructureManager` tipo supone que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente muestra la debilidad de la biblioteca.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

 Este ejemplo produce el siguiente resultado:

 **Constructor de estructura personalizado: error en la solicitud. ** 
 **Nuevos valores SecuredTypeStructure 100 100**
**SecuredTypeStructure 200 200 de nuevos valores**
## <a name="see-also"></a>Vea también
 [Las peticiones de vínculo](/dotnet/framework/misc/link-demands) [datos y modelado](/dotnet/framework/data/index)