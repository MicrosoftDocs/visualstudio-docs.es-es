---
title: "CA1720: Los identificadores no deben contener nombres de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1720"
  - "IdentifiersShouldNotContainTypeNames"
helpviewer_keywords: 
  - "IdentifiersShouldNotContainTypeNames"
  - "CA1720"
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1720: Los identificadores no deben contener nombres de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainTypeNames|  
|Identificador de comprobación|CA1720|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un parámetro de un miembro visible externamente contiene un nombre de tipo de dato.  
  
 O bien  
  
 El nombre de un miembro visible externamente contiene un nombre de tipo de dato específico del lenguaje.  
  
## Descripción de la regla  
 Es mejor utilizar los nombres de parámetros y miembros para comunicar su significado que para describir el tipo al que pertenecen, ya que esta información suelen proporcionarla las herramientas de desarrollo.  En los nombres de miembros, si es necesario utilizar un nombre de tipo de datos, utilice un nombre independiente del lenguaje en lugar de uno específico del lenguaje.  Por ejemplo, en lugar de utilizar el nombre de tipo de C\# 'int', utilice el nombre de tipo de datos independiente del lenguaje Int32.  
  
 Cada token que conforma el nombre del miembro o parámetro se compara con los siguientes nombres de tipos de datos específicos del lenguaje sin hacer distinción entre mayúsculas y minúsculas:  
  
-   Valor bool.  
  
-   WChar  
  
-   Int8  
  
-   UInt8  
  
-   Short  
  
-   UShort  
  
-   Valor int.  
  
-   UInt  
  
-   Integer  
  
-   UInteger  
  
-   Long  
  
-   ULong  
  
-   Unsigned  
  
-   Signed  
  
-   Float  
  
-   Float32  
  
-   Float64  
  
 Además, los nombres de un parámetro también se comparan con los siguientes nombres de tipos de datos independientes del lenguaje sin hacer distinción entre mayúsculas y minúsculas:  
  
-   Objeto  
  
-   Obj  
  
-   Boolean  
  
-   Char  
  
-   String  
  
-   SByte  
  
-   Byte  
  
-   UByte  
  
-   Int16  
  
-   UInt16  
  
-   Int32  
  
-   UInt32  
  
-   Int64  
  
-   UInt64  
  
-   IntPtr  
  
-   Ptr  
  
-   Puntero  
  
-   UInptr  
  
-   UPtr  
  
-   UPointer  
  
-   Single  
  
-   Double  
  
-   Decimal  
  
-   Guid  
  
## Cómo corregir infracciones  
 **Si se produce en un parámetro:**  
  
 Sustituya el identificador del tipo de dato del nombre del parámetro por un término que describa mejor su significado o por un término más genérico, como 'valor.'  
  
 **Si se produce en un miembro:**  
  
 Sustituya el identificador de tipo de dato específico del lenguaje del nombre del miembro por un término que describa mejor su significado, un término equivalente independiente del lenguaje o un término más genérico, como 'valor.'  
  
## Cuándo suprimir advertencias  
 Es posible que en ocasiones sea conveniente utilizar nombres de parámetros y miembros basados en tipos.  Sin embargo, para el nuevo desarrollo, no se da ningún escenario conocido donde se deba suprimir ninguna advertencia de esta regla.  Es posible que deba suprimir una advertencia de esta regla en las bibliotecas distribuidas anteriormente.  
  
## Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)