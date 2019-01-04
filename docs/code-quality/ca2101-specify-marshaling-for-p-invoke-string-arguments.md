---
title: 'CA2101: Especificar serialización de argumentos de cadena P-Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 778668f799f325aee98334e243a0501a185a9ceb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915654"
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Especificar serialización en argumentos de cadena P/Invoke

|||
|-|-|
|TypeName|SpecifyMarshalingForPInvokeStringArguments|
|Identificador de comprobación|CA2101|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una invocación de plataforma permite llamadores parcialmente confiables, miembro tiene un parámetro de cadena y no serializa explícitamente la cadena.

## <a name="rule-description"></a>Descripción de la regla
 Al convertir de Unicode a ANSI, es posible que no todos los caracteres Unicode se pueden representar en una página de códigos ANSI específica. *Asignación con ajuste perfecto* intenta solucionar este problema sustituyendo un carácter el carácter que no se puede representar. El uso de esta característica puede provocar una posible vulnerabilidad de seguridad porque no se puede controlar el carácter que se elige. Por ejemplo, código malintencionado deliberadamente podría crear una cadena Unicode que contiene caracteres que no se encuentran en una página de códigos determinada, se convierten en caracteres especiales del sistema como '..' o '/'. Tenga en cuenta también que las comprobaciones de seguridad para los caracteres especiales con frecuencia se producen antes de la cadena se convierte a ANSI.

 Asignación con ajuste perfecto es el valor predeterminado para la conversión no administrado, WChar en MB libres. A menos que deshabilite explícitamente una asignación con ajuste perfecto, el código podría contener una vulnerabilidad de seguridad explotable debido a este problema.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, debe serializar explícitamente los tipos de datos de cadena.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que infringe esta regla y, a continuación, se muestra cómo corregir la infracción.

 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]