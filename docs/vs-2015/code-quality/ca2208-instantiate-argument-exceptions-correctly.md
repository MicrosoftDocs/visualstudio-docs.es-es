---
title: 'CA2208: Crear instancias de las excepciones del argumento correctamente | Microsoft Docs'
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
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 55789b7d5b4b1e462b715649b7583299b9f02e6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825613"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Crear instancias de las excepciones del argumento correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|Identificador de comprobación|CA2208|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Posibles causas son las siguientes situaciones:

-   Se realiza una llamada al constructor predeterminado (sin parámetros) de un tipo de excepción que es o deriva de [System.ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o deriva de [System.ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Descripción de la regla
 En lugar de llamar al constructor predeterminado, llame a una de las sobrecargas del constructor que permite que un mensaje de excepción más significativo que se proporcione. El mensaje de excepción debe dirigirse al desarrollador y explicar con claridad la condición de error y cómo corregir o evitar la excepción.

 Las firmas de los constructores de cadena de uno y dos de <xref:System.ArgumentException> y sus tipos derivados no son coherentes con respecto a la `message` y `paramName` parámetros. Asegúrese de que se llama a estos constructores con los argumentos de la cadena correcta. Las firmas son como sigue:

 <xref:System.ArgumentException>(cadena `message`)

 <xref:System.ArgumentException>(cadena `message`, cadena `paramName`)

 <xref:System.ArgumentNullException>(cadena `paramName`)

 <xref:System.ArgumentNullException>(cadena `paramName`, cadena `message`)

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName`)

 <xref:System.ArgumentOutOfRangeException>(cadena `paramName`, cadena `message`)

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName`)

 <xref:System.DuplicateWaitObjectException>(cadena `parameterName`, cadena `message`)

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a un constructor que toma un mensaje, un nombre de parámetro o ambos y asegúrese de que los argumentos son adecuados para el tipo de <xref:System.ArgumentException> que se llama.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla solo si se llama a un constructor parametrizado con los argumentos de la cadena correcta.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un constructor que crea una instancia de una instancia del tipo ArgumentNullException incorrectamente.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente corrige la infracción anterior mediante el cambio de los argumentos de constructor.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]



