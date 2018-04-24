---
title: 'CA1720: Los identificadores no deben contener nombres de tipo'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8a981dc4c8ccd016836ea55b2ecd624e781c5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Los identificadores no deben contener nombres de tipo
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|Identificador de comprobación|CA1720|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un parámetro de un miembro visible externamente contiene un nombre de tipo de datos.

 -o bien-

 El nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje.

## <a name="rule-description"></a>Descripción de la regla
 Nombres de parámetros y miembros mejor sirven para comunicar su significado que to describir su tipo, que se espera que se proporcionan con las herramientas de desarrollo. Para los nombres de miembros, si se debe utilizar un nombre de tipo de datos, utilice un nombre independiente del lenguaje en lugar de una específica del lenguaje. Por ejemplo, en lugar del nombre de tipo de C# 'int', utilice el nombre de tipo de datos independiente del lenguaje Int32.

 Cada token que conforma el nombre del parámetro o miembro se compara con los siguientes nombres de tipo de datos específico del lenguaje, en mayúsculas y minúsculas:

-   Bool

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

-   Sin signo

-   Firmado

-   Float

-   Float32

-   Float64

 Además, los nombres de parámetro también se comparan con los siguientes nombres de tipo de datos independiente del lenguaje, en mayúsculas y minúsculas:

-   Object

-   obj

-   Booleano

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

-   PTR

-   Puntero

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Doble

-   Decimal

-   GUID

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 **Si se produce en un parámetro:**

 Reemplace el identificador de tipo de datos en el nombre de parámetro con un término que describa mejor su significado o un término más genérico, como 'value'.

 **Si se produce en un miembro:**

 Reemplace el identificador de tipo de datos específico del lenguaje en el nombre del miembro por un término que describa mejor su significado, un equivalente independiente del lenguaje o un término más genérico, como 'value'.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 El uso ocasional de nombres de parámetros y miembros basados en tipos podría ser adecuado. Sin embargo, para el nuevo desarrollo, no conoce se producen escenarios donde se debe suprimir una advertencia de esta regla. Para las bibliotecas que tienen anterior enviado, es posible que deba suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)