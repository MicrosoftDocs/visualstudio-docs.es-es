---
title: 'CA1903: usar solo la API de la plataforma de destino | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fa0d771d99ac8e7a4f4091db90a607cce970bc38
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917829"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Usar solo API de la versión de .NET Framework de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1903: use only API from Target Framework](/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|Identificador de comprobación|CA1903|
|Categoría|Microsoft. portabilidad|
|Cambio problemático|Problemático: cuando se desencadena con la firma de un miembro o tipo visible externamente.<br /><br /> No problemático: cuando se desencadena en el cuerpo de un método.|

## <a name="cause"></a>Motivo
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
|.NET Framework 4|N/A|

 Para cambiar el marco de trabajo de destino de un proyecto, vea establecer [como destino una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para quitar la dependencia del Service Pack, quite todos los usos del nuevo miembro o tipo. Si se trata de una dependencia deliberada, suprima la advertencia o desactive esta regla.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla si no se trata de una dependencia deliberada en el Service Pack especificado. En esta situación, es posible que la aplicación no se ejecute en sistemas sin este Service Pack instalado. Suprima la advertencia o desactive esta regla si se trata de una dependencia deliberada.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una clase que usa el tipo DateTimeOffset que solo está disponible en el Service Pack 1 de .NET 2,0. En este ejemplo se requiere que se haya seleccionado .NET Framework 2,0 en la lista desplegable plataforma de destino en las propiedades del proyecto.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción descrita previamente reemplazando los usos del tipo DateTimeOffset con el tipo DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Vea también
 [Advertencias de portabilidad](../code-quality/portability-warnings.md) que tienen [como destino una versión de .NET Framework específica](../ide/targeting-a-specific-dotnet-framework-version.md)
