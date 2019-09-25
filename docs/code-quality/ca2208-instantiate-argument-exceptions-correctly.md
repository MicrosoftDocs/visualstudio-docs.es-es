---
title: 'CA2208: Crear instancias de las excepciones del argumento correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231644"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Crear instancias de las excepciones del argumento correctamente

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|Identificador de comprobación|CA2208|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Las posibles causas son las siguientes:

- Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de, <xref:System.ArgumentException>.

- Un argumento de cadena incorrecto se pasa a un constructor con parámetros de un tipo de excepción que es o deriva de, <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descripción de la regla

En lugar de llamar al constructor predeterminado, llame a una de las sobrecargas del constructor que permite proporcionar un mensaje de excepción más significativo. El mensaje de excepción debe dirigirse al desarrollador y explicar claramente la condición de error y cómo corregir o evitar la excepción.

Las firmas de los constructores de cadena uno y dos de <xref:System.ArgumentException> y sus tipos derivados no son coherentes con respecto a la `message` posición `paramName` y los parámetros. Asegúrese de que se llama a estos constructores con los argumentos de cadena correctos. Las firmas son las siguientes:

- <xref:System.ArgumentException>(cadena `message`)
- <xref:System.ArgumentException>(cadena `message`, cadena `paramName`)
- <xref:System.ArgumentNullException>(cadena `paramName`)
- <xref:System.ArgumentNullException>(cadena `paramName`, cadena `message`)
- <xref:System.ArgumentOutOfRangeException>(cadena `paramName`)
- <xref:System.ArgumentOutOfRangeException>(cadena `paramName`, cadena `message`)
- <xref:System.DuplicateWaitObjectException>(cadena `parameterName`)
- <xref:System.DuplicateWaitObjectException>(cadena `parameterName`, cadena `message`)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, llame a un constructor que tome un mensaje, un nombre de parámetro o ambos, y asegúrese de que los argumentos sean correctos <xref:System.ArgumentException> para el tipo de al que se está llamando.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla solo si se llama a un constructor con parámetros con los argumentos de cadena correctos.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra un constructor que crea incorrectamente una instancia de <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

En el código siguiente se corrige la infracción anterior mediante el cambio de los argumentos del constructor.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1507: Usar nombre en lugar de cadena](ca1507.md)