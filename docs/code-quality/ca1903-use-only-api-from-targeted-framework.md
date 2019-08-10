---
title: 'CA1903: Usar solo API de la versión de .NET Framework de destino'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d972198898dd1a4cafa5280c129db38bb3e4982
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921298"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Usar solo API de la versión de .NET Framework de destino

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|Identificador de comprobación|CA1903|
|Categoría|Microsoft. portabilidad|
|Cambio problemático|Problemático: cuando se desencadena con la firma de un miembro o tipo visible externamente.<br /><br /> No problemático: cuando se desencadena en el cuerpo de un método.|

## <a name="cause"></a>Causa
Un miembro o tipo está utilizando un miembro o tipo que se presentó en una Service Pack que no se incluyó con el marco de trabajo de destino del proyecto.

## <a name="rule-description"></a>Descripción de la regla
Los nuevos miembros y tipos se incluyeron en .NET Framework 2,0 Service Pack 1 y 2, .NET Framework 3,0 Service Pack 1 y 2 y .NET Framework 3,5 Service Pack 1. Los proyectos que tienen como destino las versiones principales del .NET Framework pueden tomar dependencias de estas nuevas API de forma involuntaria. Para evitar esta dependencia, esta regla se desencadena en los usos de los nuevos miembros y tipos que no se incluyeron de forma predeterminada con la plataforma de destino del proyecto.

**Dependencias de Service Pack y de la plataforma de destino**

|||
|-|-|
|Cuando la plataforma de destino es|Se desencadena en los usos de los miembros introducidos en|
|.NET Framework 2.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|.NET Framework 3,5|.NET Framework 3.5 SP1|
|.NET Framework 4|N/D|

Para cambiar el marco de trabajo de destino de [un proyecto, consulte Cómo: Establecer una versión de .NET como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para quitar la dependencia del Service Pack, quite todos los usos del nuevo miembro o tipo. Si se trata de una dependencia deliberada, suprima la advertencia o desactive esta regla.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla si no se trata de una dependencia deliberada en el Service Pack especificado. En esta situación, es posible que la aplicación no se ejecute en sistemas sin este Service Pack instalado. Suprima la advertencia o desactive esta regla si se trata de una dependencia deliberada.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra una clase que usa el tipo DateTimeOffset que solo está disponible en el Service Pack 1 de .NET 2,0. En este ejemplo se requiere que se haya seleccionado .NET Framework 2,0 en la lista desplegable plataforma de destino en las propiedades del proyecto.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se corrige la infracción descrita previamente reemplazando los usos del tipo DateTimeOffset con el tipo DateTime.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Vea también

- [Portability Warnings](../code-quality/portability-warnings.md)
- [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md)