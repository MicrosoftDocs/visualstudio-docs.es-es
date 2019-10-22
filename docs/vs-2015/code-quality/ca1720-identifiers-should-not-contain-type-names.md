---
title: 'CA1720: los identificadores no deben contener nombres de tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34ebe4848bbbe49b9a67449795f0aea7d104af8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671638"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720: Los identificadores no deben contener nombres de tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|Identificador de comprobación|CA1720|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de un parámetro de un miembro visible externamente contiene un nombre de tipo de datos.

 o bien

 El nombre de un miembro visible externamente contiene un nombre de tipo de datos específico del lenguaje.

## <a name="rule-description"></a>Descripción de la regla
 Los nombres de los parámetros y los miembros se utilizan mejor para comunicar su significado que describir su tipo, que se espera que proporcionen las herramientas de desarrollo. En el caso de los nombres de los miembros, si se debe usar un nombre de tipo de datos, use un nombre independiente del lenguaje en lugar de uno específico del lenguaje. Por ejemplo, en lugar del nombre C# de tipo ' int ', use el nombre del tipo de datos independiente del lenguaje, Int32.

 Cada token discreto en el nombre del parámetro o miembro se comprueba con los siguientes nombres de tipos de datos específicos del lenguaje, sin distinción entre mayúsculas y minúsculas:

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Valor int.

- UInt

- Integer

- UInteger

- Long

- ULong

- Sin signo

- Firmado

- Float

- Float32

- Float64

  Además, los nombres de un parámetro también se comprueban con los siguientes nombres de tipos de datos independientes del lenguaje, de modo que no se distingue entre mayúsculas y minúsculas:

- Object

- Obj

- Booleano

- Char

- String

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Anota

- Puntero

- UInptr

- UPtr

- UPointer

- Single

- Doble

- Decimal

- GUID

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 **Si se desencadena en un parámetro:**

 Reemplace el identificador de tipo de datos en el nombre del parámetro por un término que describa mejor su significado o un término más genérico, como ' valor '.

 **Si se desencadena en un miembro:**

 Reemplace el identificador de tipo de datos específico del lenguaje en el nombre del miembro por un término que describa mejor su significado, un equivalente independiente del lenguaje o un término más genérico, como ' valor '.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 El uso ocasional de los nombres de los parámetros y miembros basados en tipos puede ser adecuado. Sin embargo, para el nuevo desarrollo, no se produce ningún escenario conocido en el que debe suprimir una advertencia de esta regla. En el caso de las bibliotecas que se enviaron anteriormente, es posible que tenga que suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719: Los nombres de parámetro no deberían coincidir con los nombres de miembro](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
