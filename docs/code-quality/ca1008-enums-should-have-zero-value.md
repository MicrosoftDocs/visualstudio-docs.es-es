---
title: "CA1008: Las enumeraciones deben tener un valor igual a cero | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1008: Las enumeraciones deben tener un valor igual a cero
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|Identificador de comprobación|CA1008|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No problemático: cuando le solicitan que agregue un valor **None** a una enumeración sin marca. Problemático: cuando le solicitan que cambie el nombre o que quite cualquier valor de enumeración.|  
  
## Motivo  
 Una enumeración sin un <xref:System.FlagsAttribute?displayProperty=fullName> aplicado no define un miembro que tiene un valor de cero; o una enumeración que tiene un <xref:System.FlagsAttribute> aplicado define un miembro que tiene un valor de cero pero su nombre no es "None" o la enumeración define varios miembros con valor cero.  
  
## Descripción de la regla  
 El valor predeterminado de una enumeración no inicializada, igual que otros tipos de valor, es cero.  Una enumeración con atributo y sin marcas debería definir un miembro que tiene el valor de cero de modo que el valor predeterminado sea un valor válido de la enumeración.  Si es necesario, denomine el miembro "None".  De lo contrario, asigne el valor cero al miembro que se utiliza más frecuentemente.  Tenga en cuenta que, de forma predeterminada, si el valor del primer miembro de la enumeración no se establece en la declaración, su valor es cero.  
  
 Si una enumeración a la que se le haya aplicado <xref:System.FlagsAttribute> define un miembro con valor cero, su nombre debe ser "None" para indicar que no se han establecido valores en la enumeración.  Utilizando un miembro con valor cero para cualquier otro propósito que no sea el uso de <xref:System.FlagsAttribute> en el que los operadores bit a bit AND y OR no son útiles con el miembro.  Esto implica que sólo se debería asignar el valor cero a un miembro.  Tenga en cuenta que si hay varios miembros que tienen el valor cero en una enumeración con atributos y marcas, `Enum.ToString()` devuelve resultados incorrectos para los miembros que no tienen valor cero.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla para las enumeraciones con atributo y sin marcas, defina un miembro que tenga el valor de cero; esto no es un cambio importante.  Para las enumeraciones con atributo y marcas que definen un miembro con valor cero, denomine el miembro "None" y elimine cualquier miembro que tenga un valor de cero; éste es un cambio importante.  
  
## Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla excepto para enumeraciones con atributo y marcadores que se hayan distribuido previamente.  
  
## Ejemplo  
 El ejemplo siguiente muestra dos enumeraciones que cumplen la regla, y una enumeración `BadTraceOptions`, que la infringe.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## Reglas relacionadas  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: No nombrar valores de enumeración como 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.Enum?displayProperty=fullName>