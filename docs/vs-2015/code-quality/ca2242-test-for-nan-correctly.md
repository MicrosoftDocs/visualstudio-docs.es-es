---
title: 'CA2242: prueba para NaN correcta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546268"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Comprobar NaN correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TestForNaNCorrectly|
|Identificador de comprobación|CA2242|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Una expresión prueba un valor con <xref:System.Single.NaN?displayProperty=fullName> o <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Double.NaN?displayProperty=fullName>, que representa un valor no numérico, se produce cuando una operación aritmética no está definida. Cualquier expresión que comprueba la igualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `false` . Cualquier expresión que comprueba la desigualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `true` .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla y determinar con precisión si un valor representa <xref:System.Double.NaN?displayProperty=fullName> , use <xref:System.Single.IsNaN%2A?displayProperty=fullName> o <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos expresiones que prueban incorrectamente un valor en <xref:System.Double.NaN?displayProperty=fullName> y una expresión que usa correctamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
