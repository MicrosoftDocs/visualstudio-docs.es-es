---
title: "CA1903: Usar solo API de la versi&#243;n de .NET Framework de destino | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseOnlyAPIFromTargetedFramework"
  - "CA1903"
helpviewer_keywords: 
  - "CA1903"
  - "UseOnlyApiFromTargetedFramework"
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# CA1903: Usar solo API de la versi&#243;n de .NET Framework de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseOnlyApiFromTargetedFramework|  
|Identificador de comprobación|CA1903|  
|Categoría|Microsoft.Portability|  
|Cambio problemático|Problemático: si se produce en la firma de un miembro o tipo externamente visible.<br /><br /> No problemático: si se produce en el cuerpo de un método.|  
  
## Motivo  
 Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido en el marco de destino del proyecto.  
  
## Descripción de la regla  
 Se han incluido nuevos miembros y tipos en los Service Pack 1 y 2 de .NET Framework 2.0, en los Service Pack 1 y 2 de .NET Framework 3.0 y en el Service Pack 1 de .NET Framework 3.5  Los proyectos diseñados para las versiones principales de .NET Framework pueden tomar dependencias involuntariamente en estas nuevas API.  Para evitar esta dependencia, esta regla se desencadena cada vez que se usa un miembro o tipo nuevo no incluido de forma predeterminada en la versión de .NET Framework de destino del proyecto.  
  
 **Dependencias de la versión de .NET Framework de destino y el Service Pack**  
  
|||  
|-|-|  
|Cuando la versión de .NET Framework de destino es|Se desencadena cuando se usan miembros presentados en|  
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|  
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|  
|.NET Framework 3.5|.NET Framework 3.5 SP1|  
|.NET Framework 4|N\/D|  
  
 Para cambiar la versión de .NET Framework de destino de un proyecto, vea [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
## Cómo corregir infracciones  
 Para quitar la dependencia del Service Pack, quite todos los usos del nuevo miembro o tipo.  Si se trata de una dependencia deliberada, deberá suprimir la advertencia o desactivar esta regla.  
  
## Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla si no se trata de una dependencia deliberada con respecto al Service Pack especificado.  En esta situación, la aplicación podría no ejecutarse en aquellos sistemas donde no esté instalado este Service Pack.  Si se trata de una dependencia deliberada, deberá suprimir la advertencia o desactivar esta regla.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra una clase que utiliza el tipo DateTimeOffset que solo está disponible en .NET 2.0 Service Pack 1.  Este ejemplo requiere que NET Framework 2.0 se haya seleccionado en la lista desplegable Versión de .NET Framework de destino de Propiedades del proyecto.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrige la infracción descrita previamente reemplazando los usos del tipo DateTimeOffset con el tipo DateTime.  
  
 [!code-cs[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]  
  
## Vea también  
 [Advertencias de portabilidad](../code-quality/portability-warnings.md)   
 [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)