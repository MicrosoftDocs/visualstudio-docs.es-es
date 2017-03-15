---
title: "CA1028: El almacenamiento de la enumeraci&#243;n debe ser de tipo Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1028: El almacenamiento de la enumeraci&#243;n debe ser de tipo Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|Identificador de comprobación|CA1028|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El tipo subyacente de una enumeración pública no es <xref:System.Int32?displayProperty=fullName>.  
  
## Descripción de la regla  
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas.  De manera predeterminada, el tipo de datos <xref:System.Int32?displayProperty=fullName> se utiliza para almacenar el valor constante.  Aunque puede cambiar este tipo subyacente, no es necesario o ni se recomienda en la mayoría de los escenarios.  Observe que no se obtiene una mejora de rendimiento significativa utilizando un tipo de datos que es menor que <xref:System.Int32>.  Si no puede utilizar el tipo de datos predeterminado, debe utilizar uno de los tipos enteros conformes a Common Language Runtime \(CLR\), <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> o <xref:System.Int64> para garantizar que todos los valores de la enumeración se puedan representar en los lenguajes de programación conformes a CLS.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, a menos que existan problemas de compatibilidad o de tamaño, utilice <xref:System.Int32>.  Para situaciones donde <xref:System.Int32> no es bastante grande para contener los valores, utilice <xref:System.Int64>.  Si la compatibilidad con versiones anteriores requiere un tipo de datos menor, utilice <xref:System.Byte> o <xref:System.Int16>.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla únicamente si los problemas de compatibilidad con versiones anteriores lo requieren.  En las aplicaciones, no cumplir esta regla normalmente no produce problemas.  En bibliotecas, donde se requiere la interoperabilidad de lenguajes, no cumplir esta regla podría afectar de forma adversa a sus usuarios.  
  
## Ejemplo de infracción  
  
### Descripción  
 El ejemplo siguiente muestra dos enumeraciones que no utilizan el tipo de datos subyacente recomendado.  
  
### Código  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Ejemplo de cómo corregir  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción anterior cambiando el tipo de datos subyacentes a <xref:System.Int32>.  
  
### Código  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Reglas relacionadas  
 [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## Vea también  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>