---
title: 'CA2101: especifique el cálculo de referencias para los argumentos de cadena P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57b7214058baf63ffa5e3ee2c9a982bf411b60e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652181"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|Identificador de comprobación|CA2101|
|Categoría|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un miembro de invocación de plataforma permite llamadores de confianza parcial, tiene un parámetro de cadena y no serializa explícitamente la cadena.

## <a name="rule-description"></a>Descripción de la regla
 Al convertir de Unicode a ANSI, es posible que no todos los caracteres Unicode puedan representarse en una página de códigos ANSI específica. La *asignación con ajuste* perfecto intenta resolver este problema sustituyendo un carácter por el carácter que no se puede representar. El uso de esta característica puede causar una posible vulnerabilidad de seguridad porque no se puede controlar el carácter elegido. Por ejemplo, el código malintencionado podría crear intencionadamente una cadena Unicode que contiene caracteres que no se encuentran en una página de códigos determinada, que se convierten en caracteres especiales del sistema de archivos, como '.. ' o '/'. Tenga en cuenta también que las comprobaciones de seguridad para los caracteres especiales se producen con frecuencia antes de que la cadena se convierta en ANSI.

 La asignación con ajuste perfecto es el valor predeterminado para la conversión no administrada, de WChar a MByte. A menos que se deshabilite explícitamente la asignación con ajuste perfecto, el código podría contener una vulnerabilidad de seguridad explotable debido a este problema.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, debe serializar explícitamente los tipos de datos de cadena.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe esta regla y, a continuación, muestra cómo corregir la infracción.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PinvokeAnsiUnicode/cs/FxCop.Security.PinvokeAnsiUnicode.cs#1)]
