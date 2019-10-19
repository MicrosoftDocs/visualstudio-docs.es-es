---
title: 'CA1011: considere pasar los tipos base como parámetros | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663250"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considere pasar los tipos base como parámetros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|Identificador de comprobación|CA1011|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una declaración de método incluye un parámetro formal que es un tipo derivado y el método solo llama a los miembros del tipo base del parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Cuando se usa el argumento dentro del cuerpo del método, el método específico que se ejecuta depende del tipo del argumento. Si no se requiere la funcionalidad adicional proporcionada por el tipo derivado, el uso del tipo base permite un uso más amplio del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla

- Si el método requiere la funcionalidad específica que proporciona el tipo derivado

   \- o -

- para aplicar que solo el tipo derivado, o un tipo más derivado, se pasa al método.

  En estos casos, el código será más robusto debido a la comprobación de tipos segura proporcionada por el compilador y el tiempo de ejecución.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `ManipulateFileStream`, que solo se puede usar con un objeto <xref:System.IO.FileStream>, que infringe esta regla. Un segundo método, `ManipulateAnyStream`, satisface la regla reemplazando el parámetro <xref:System.IO.FileStream> mediante un <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
