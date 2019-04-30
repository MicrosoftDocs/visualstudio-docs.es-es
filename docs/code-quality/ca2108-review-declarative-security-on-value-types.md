---
title: 'CA2108: Revisar la seguridad declarativa en los tipos de valores'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f4cac83c83b47fda5cf9cde85a3e14d857d2bc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545543"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Revisar la seguridad declarativa en los tipos de valores

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|Identificador de comprobación|CA2108|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un tipo de valor público o protegido está protegido por un [datos y modelado](/dotnet/framework/data/index) o [peticiones de vínculo](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descripción de la regla

Tipos de valor se asigna y se inicializan por sus constructores predeterminados antes de ejecutan otros constructores. Si un tipo de valor está protegido por Demand o LinkDemand y el llamador no tiene los permisos que satisfacen la comprobación de seguridad, cualquier constructor que no sea el valor predeterminado se producirá un error y se producirá una excepción de seguridad. No se desasigna el tipo de valor; se deja en el estado establecido mediante su constructor predeterminado. No suponga que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

No se puede corregir una infracción de esta regla a menos que quite la comprobación de seguridad del tipo y comprobaciones de seguridad de nivel de método de uso en su lugar. Corregir la infracción de esta manera no impide que los llamadores que tengan los permisos adecuados de obtención de instancias del tipo de valor. Debe asegurarse de que una instancia del tipo de valor, en su estado predeterminado, no expone información confidencial y no se puede usar de manera perjudicial.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Puede suprimir una advertencia de esta regla si un llamador puede obtener instancias del tipo de valor en su estado predeterminado sin suponer una amenaza de seguridad.

## <a name="example-1"></a>Ejemplo 1

El ejemplo siguiente muestra una biblioteca que contiene un tipo de valor que infringe esta regla. El `StructureManager` tipo supone que un llamador que pasa una instancia del tipo de valor tiene permiso para crear o tener acceso a la instancia.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Ejemplo 2

La aplicación siguiente muestra el punto débil de la biblioteca.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Vea también

- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)
