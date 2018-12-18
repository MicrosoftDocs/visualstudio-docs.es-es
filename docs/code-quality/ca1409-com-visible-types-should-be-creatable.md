---
title: 'CA1409: Los tipos visibles COM se deben poder crear'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 817c2215245412faf0bb30d46aec40a953f239b5
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546855"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Los tipos visibles COM se deben poder crear

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|Identificador de comprobación|CA1409|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia marcado específicamente como visible para el modelo de objetos componentes (COM) contiene un constructor parametrizado público pero no contiene un constructor público predeterminado (sin parámetros).

## <a name="rule-description"></a>Descripción de la regla
 Los clientes COM no puede crear un tipo sin un constructor predeterminado público. Sin embargo, el tipo puede aún tener acceso a los clientes COM si hay otros medios crear el tipo y pasarlo al cliente (por ejemplo, mediante el valor devuelto de una llamada al método).

 La regla omite los tipos derivados de <xref:System.Delegate?displayProperty=fullName>.

 De forma predeterminada, los siguientes son visibles para COM: ensamblados, tipos públicos, los miembros de instancia públicos en tipos públicos y todos los miembros de tipos de valor público.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue un constructor predeterminado público o quite el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> del tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si se proporcionan otras formas de crear y pasar el objeto para el cliente COM.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1017: Marque los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vea también

- [Habilitar tipos de .NET para la interoperación](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)