---
title: 'CA2208: Crear instancias de las excepciones del argumento correctamente'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab379305eae593a1c2f14f5c2ec860d398af2eaf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Crear instancias de las excepciones del argumento correctamente
|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|Identificador de comprobación|CA2208|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Posibles causas son las siguientes situaciones:

-   Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de <xref:System.ArgumentException>.

-   Se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de <xref:System.ArgumentException>.

## <a name="rule-description"></a>Descripción de la regla
 En lugar de llamar al constructor predeterminado, llame a una de las sobrecargas del constructor que permite a un mensaje de excepción más significativo que se proporcione. El mensaje de excepción debería dirigirse al desarrollador y explicar con claridad la condición de error y cómo corregir o evitar la excepción.

 Las firmas de los constructores de cadena de uno y dos de <xref:System.ArgumentException> y sus tipos derivados no son coherentes con respecto a la `message` y `paramName` parámetros. Asegúrese de que se llama a estos constructores con los argumentos de cadena correctos. Las firmas son los siguientes:

 <xref:System.ArgumentException>(cadena `message`)

 <xref:System.ArgumentException>(cadena `message`, cadena `paramName`)

 <xref:System.ArgumentNullException>(cadena `paramName`)

 <xref:System.ArgumentNullException>(cadena `paramName`, cadena `message`)

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName`)

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName`, cadena `message`)

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName`)

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName`, cadena `message`)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llama a un constructor que toma un mensaje, un nombre de parámetro o ambos y asegúrese de que los argumentos sean correctos para el tipo de <xref:System.ArgumentException> que se va a llamar.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla sólo si se llama a un constructor parametrizado con los argumentos de cadena correctos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un constructor que incorrectamente crea una instancia del tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior mediante el cambio de los argumentos de constructor.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]