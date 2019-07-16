---
title: 'CA1903: Usar solo API de .NET framework de destino | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 146563dfa358367e7c22f8ad37564b85d64eaf1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189081"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Usar solo API de la versión de .NET Framework de destino
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio, consulte [CA1903: Usar solo API de .NET framework de destino](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).  
  
|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|Identificador de comprobación|CA1903|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: cuando se produce en la firma de un tipo o miembro visible externamente.<br /><br /> Indivisible - cuando se desencadena en el cuerpo de un método.|  
  
## <a name="cause"></a>Causa  
 Un miembro o tipo utiliza un miembro o tipo que se introdujo en un service pack que no se incluyó en .NET framework de destino del proyecto.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Se han incluido nuevos miembros y tipos en .NET Framework 2.0 Service Pack 1 y 2, Service Pack 1 y 2 de .NET Framework 3.0 y .NET Framework 3.5 Service Pack 1. Los proyectos que tienen como destino las versiones principales de .NET Framework pueden tomar dependencias involuntariamente en estas nuevas API. Para evitar esta dependencia, esta regla se desencadena en los usos de los nuevos miembros y tipos que no se incluyeron con .NET framework de destino del proyecto de forma predeterminada.  
  
 **.NET Framework de destino y las dependencias del módulo de servicio**  
  
|||  
|-|-|  
|Cuando es la plataforma de destino|Se desencadena en los usos de los miembros que se introdujo en|  
|.NET Framework 2.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3,5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N/D|  
  
 Para cambiar la plataforma de destino de un proyecto, vea [como destino una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para quitar la dependencia en el service pack, quite todos los usos del nuevo miembro o tipo. Si se trata de una dependencia deliberada, suprimir la advertencia o desactivar esta regla.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla si no se trata de una dependencia deliberada en el service pack especificado. En esta situación, la aplicación podría no ejecutarse en sistemas sin este service pack instalado. Suprimir la advertencia o desactivar esta regla si se trata de una dependencia deliberada.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra una clase que utiliza el tipo DateTimeOffset que solo está disponible en .NET 2.0 Service Pack 1. Este ejemplo requiere que .NET Framework 2.0 se ha seleccionado en la lista desplegable de .NET Framework de destino en las propiedades del proyecto.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente corrige la infracción descrita anteriormente reemplazando los usos del tipo DateTimeOffset con el tipo de fecha y hora.  
  
 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]  
  
## <a name="see-also"></a>Vea también  
 [Advertencias de portabilidad](../code-quality/portability-warnings.md)   
 [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)
