---
title: 'CA1811: Evitar código privado no solicitada | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6907ffdfc8fa7fec097ce1c1adf9eeabdd890ccc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293571"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Evitar código privado al que no se llama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|Identificador de comprobación|CA1811|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Miembro privado o interno (nivel de ensamblado) no tiene llamadores en el ensamblado, no es invocado por common language runtime y no se invoca un delegado. Esta regla no comprueba los miembros siguientes:

-   Miembros de interfaz explícita.

-   Constructores estáticos.

-   Constructores de serialización.

-   Los métodos marcados con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Miembros que son reemplazos.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla puede notificar falsos positivos si producen puntos de entrada que no se identifican actualmente por la lógica de la regla. Además, un compilador puede emitir código noncallable en un ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el código noncallable o agregue código que lo llama.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)



