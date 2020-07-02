---
title: 'CA1700: no nombrar los valores de enumeración &#39;&#39; reservado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545657"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: no asignar nombres a los valores de enumeración &#39;reservado&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|Identificador de comprobación|CA1700|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El nombre de un miembro de enumeración contiene la palabra "Reserved".

## <a name="rule-description"></a>Descripción de la regla
 Esta regla supone que un miembro de la enumeración con un nombre que contiene la palabra "reserved" no se utiliza actualmente pero hace de marcador de posición para que se pueda quitar o cambiar el nombre en una versión posterior. Quitar o cambiar el nombre de un miembro es un cambio importante. No debería esperar que los usuarios omitan un miembro simplemente porque su nombre contiene "reservado", ni puede confiar en que los usuarios lean o respeten la documentación. Además, dado que los miembros reservados aparecen en los exploradores de objetos y en los entornos de desarrollo integrado inteligente, pueden confundir los miembros que se usan realmente.

 En lugar de usar un miembro reservado, agregue un nuevo miembro a la enumeración en la versión futura. En la mayoría de los casos, la adición del nuevo miembro no es un cambio importante, siempre y cuando la adición no cause la modificación de los valores de los miembros originales.

 En un número limitado de casos, la adición de un miembro es un cambio importante incluso cuando los miembros originales conservan sus valores originales. Principalmente, el nuevo miembro no se puede devolver desde las rutas de acceso de código existentes sin interrumpir a los llamadores que usan una `switch` `Select` instrucción (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) en el valor devuelto que abarca toda la lista de miembros y que producen una excepción en el caso predeterminado. Una preocupación secundaria es que el código de cliente podría no controlar el cambio de comportamiento de métodos de reflexión como <xref:System.Enum.IsDefined%2A?displayProperty=fullName> . En consecuencia, si el nuevo miembro debe devolverse desde los métodos existentes o si se produce una incompatibilidad de aplicaciones conocida debido a un uso deficiente de la reflexión, la única solución sin interrupción es:

1. Agregue una nueva enumeración que contenga los miembros originales y nuevos.

2. Marque la enumeración original con el <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo.

   Siga el mismo procedimiento para cualquier tipo o miembro visible externamente que exponga la enumeración original.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite o cambie el nombre del miembro.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla para un miembro que se usa actualmente o para las bibliotecas que se han enviado previamente.

## <a name="related-rules"></a>Reglas relacionadas
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: No utilizar prefijos en valores de enumeración con el nombre del tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: El almacenamiento de la enumeración debe ser de tipo Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: Las enumeraciones deben tener un valor igual a cero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
