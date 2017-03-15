---
title: "CA1406: Evite argumentos Int64 para clientes Visual Basic 6 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: Evite argumentos Int64 para clientes Visual Basic 6
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|Identificador de comprobación|CA1406|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo marcado específicamente como visible para el Modelo de objetos componentes \(COM\) declara un miembro que utiliza un argumento <xref:System.Int64?displayProperty=fullName>.  
  
## Descripción de la regla  
 Los clientes COM de Visual Basic 6 no pueden tener acceso a los enteros de 64 bits.  
  
 De manera predeterminada, son visibles para COM: ensamblados, tipos públicos, miembros de instancia públicos de tipos públicos y todos los miembros de tipos de valor públicos.  Sin embargo, para reducir los falsos positivos, esta regla requiere que la visibilidad del tipo para COM se establezca explícitamente; el ensamblado que contiene se debe marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> establecido en `false` y el tipo se tiene que marcar con el <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `true`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla para un parámetro que siempre se pueda expresar como integral de 32 bits, cambie el tipo de parámetro a <xref:System.Int32?displayProperty=fullName>.  Si el valor del parámetro podría ser mayor que el valor que se puede expresar como un integral de 32 bits, cambie el tipo de parámetro a <xref:System.Decimal?displayProperty=fullName>.  Tenga en cuenta que <xref:System.Single?displayProperty=fullName> y <xref:System.Double?displayProperty=fullName> pierden precisión en los intervalos superiores del tipo de datos <xref:System.Int64>.  Si no se pretende que este miembro sea visible para COM, márquelo con el atributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> establecido en `false`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si tiene la certeza de que los clientes COM de Visual Basic 6 no van a tener acceso al tipo.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe la regla.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Reglas relacionadas  
 [CA1413: Evite campos no públicos en tipos de valor visibles para COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Evite miembros estáticos en tipos visibles para COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Long \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/long-data-type)