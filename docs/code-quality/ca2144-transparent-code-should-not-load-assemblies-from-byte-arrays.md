---
title: 'CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33edff9b22559799cef4ad7e03058a5eb212182b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232007"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: El código transparente no debe cargar ensamblados desde matrices de bytes

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|Identificador de comprobación|CA2144|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un método transparente carga un ensamblado desde una matriz de bytes mediante uno de los métodos siguientes:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Descripción de la regla
La revisión de seguridad del código transparente no es tan exhaustiva como la revisión de seguridad del código crítico, porque el código transparente no puede realizar acciones que afectan a la seguridad. Los ensamblados cargados desde una matriz de bytes podrían no distinguirse en el código transparente, y esa matriz de bytes podría contener código importante crítico para la seguridad, que no hace falta auditar. Por lo tanto, el código transparente no debe cargar ensamblados de una matriz de bytes.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, marque el método que está cargando el ensamblado <xref:System.Security.SecurityCriticalAttribute> con el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
La regla se desencadena en el código siguiente porque un método transparente carga un ensamblado desde una matriz de bytes.

[!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]