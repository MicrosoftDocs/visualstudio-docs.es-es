---
title: 'CA1409: Los tipos visibles a través de COM se deben poder crear'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4196cb91e1b866453de54347b8a67edd3dc2dc96
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921889"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Los tipos visibles a través de COM se deben poder crear

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|Identificador de comprobación|CA1409|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un tipo de referencia que está marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un constructor con parámetros público, pero no contiene un constructor público predeterminado (sin parámetros).

## <a name="rule-description"></a>Descripción de la regla
Los clientes COM no pueden crear un tipo sin un constructor predeterminado público. Sin embargo, los clientes COM todavía pueden tener acceso al tipo si hay otro medio disponible para crear el tipo y pasarlo al cliente (por ejemplo, mediante el valor devuelto de una llamada al método).

La regla omite los tipos que se derivan <xref:System.Delegate?displayProperty=fullName>de.

De forma predeterminada, los siguientes elementos son visibles para COM: ensamblados, tipos públicos, miembros de instancia pública en tipos públicos y todos los miembros de tipos de valor públicos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue un constructor predeterminado público o quite <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si se proporcionan otras maneras de crear y pasar el objeto al cliente COM.

## <a name="related-rules"></a>Reglas relacionadas
[CA1017: Marcar ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)