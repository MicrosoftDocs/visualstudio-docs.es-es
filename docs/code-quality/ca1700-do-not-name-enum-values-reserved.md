---
title: "CA1700: No nombrar valores de enumeraci&#243;n como &#39;Reserved&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1700"
  - "DoNotNameEnumValuesReserved"
helpviewer_keywords: 
  - "DoNotNameEnumValuesReserved"
  - "CA1700"
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1700: No nombrar valores de enumeraci&#243;n como &#39;Reserved&#39;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNameEnumValuesReserved|  
|Identificador de comprobación|CA1700|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un miembro de enumeración contiene la palabra "reserved".  
  
## Descripción de la regla  
 Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior.  Quitar o cambiar el nombre de un miembro es un cambio importante.  No se debe esperar que los usuarios omitan un miembro porque contenga la palabra "reserved", ni se puede confiar en que los usuarios lean o apliquen la documentación.  Además, puesto que los miembros reservados aparecen en los Examinadores de objetos y en los entornos de desarrollo integrados, pueden provocar confusiones sobre qué miembros se están utilizando actualmente.  
  
 En lugar de utilizar un miembro reservado, agregue un nuevo miembro a la enumeración en la versión futura.  En la mayoría de los casos, agregar un nuevo miembro no supone un cambio importante, siempre que la inclusión no provoque cambios en los valores de los miembros originales.  
  
 En un número reducido de casos la inclusión de un miembro es un cambio importante incluso cuando los miembros originales mantienen sus valores originales.  Principalmente, las rutas de acceso a código no pueden devolver el nuevo miembro sin llamadores importantes que utilicen una instrucción `switch` \(`Select` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) en el valor devuelto que abarca la lista completa de miembros que producen una excepción en el caso predeterminado.  Un aspecto secundario es que el código de cliente no podría controlar el cambio de comportamiento de los métodos de reflexión como <xref:System.Enum.IsDefined%2A?displayProperty=fullName>.  En consecuencia, si los métodos existentes deben devolver el nuevo miembro o se produce una incompatibilidad de la aplicación conocida debido al uso de una reflexión deficiente, la única solución no problemática es:  
  
1.  Agregar una nueva enumeración que contiene los miembros originales y nuevos.  
  
2.  Marque la enumeración original con el atributo <xref:System.ObsoleteAttribute?displayProperty=fullName>.  
  
 Siga el mismo procedimiento para cualquiera de los tipos visibles externamente o miembros que exponen la enumeración original.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite o cambie el nombre del miembro.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla para un miembro que se usa actualmente o para bibliotecas distribuidas previamente.  
  
## Reglas relacionadas  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)