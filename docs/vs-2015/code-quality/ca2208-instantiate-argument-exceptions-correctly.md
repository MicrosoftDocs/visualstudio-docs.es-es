---
title: 'CA2208: crear instancias de las excepciones de los argumentos correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535842"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Crear instancias de las excepciones del argumento correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|Identificador de comprobación|CA2208|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Las posibles causas son las siguientes:

- Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Descripción de la regla
 En lugar de llamar al constructor predeterminado, llame a una de las sobrecargas del constructor que permite proporcionar un mensaje de excepción más significativo. El mensaje de excepción debe dirigirse al desarrollador y explicar claramente la condición de error y cómo corregir o evitar la excepción.

 Las firmas de los constructores de cadena uno y dos de <xref:System.ArgumentException> y sus tipos derivados no son coherentes con respecto a `message` los `paramName` parámetros y. Asegúrese de que se llama a estos constructores con los argumentos de cadena correctos. Las firmas son las siguientes:

 <xref:System.ArgumentException>(cadena `message` )

 <xref:System.ArgumentException>(cadena `message` , cadena `paramName` )

 <xref:System.ArgumentNullException>(cadena `paramName` )

 <xref:System.ArgumentNullException>(cadena `paramName` , cadena `message` )

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName` )

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName` , cadena `message` )

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName` )

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName` , cadena `message` )

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a un constructor que tome un mensaje, un nombre de parámetro o ambos, y asegúrese de que los argumentos sean correctos para el tipo de <xref:System.ArgumentException> al que se está llamando.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla solo si se llama a un constructor con parámetros con los argumentos de cadena correctos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un constructor que crea incorrectamente instancias de una instancia del tipo ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige la infracción anterior mediante el cambio de los argumentos del constructor.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
