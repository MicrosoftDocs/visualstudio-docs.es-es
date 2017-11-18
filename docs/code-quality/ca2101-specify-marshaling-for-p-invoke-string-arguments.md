---
title: "CA2101: Especifique cálculo de referencias para argumentos de cadena P Invoke | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a759662b35024add1666e99c89433f0b369676b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|Identificador de comprobación|CA2101|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Una invocación de plataforma permite llamadores parcialmente confiables, miembro tiene un parámetro de cadena y no serializa explícitamente la cadena.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Al convertir de Unicode a ANSI, es posible que no todos los caracteres Unicode se pueden representar en una página de códigos ANSI específica. *Asignación con ajuste perfecto* intenta solucionar este problema sustituyendo un carácter por el carácter que no se puede representar. El uso de esta característica puede causar una vulnerabilidad de seguridad porque no se puede controlar el carácter que se ha seleccionado. Por ejemplo, el código malintencionado podría crear intencionadamente una cadena Unicode que contiene caracteres que no se encuentran en una página de códigos determinada, que se convierten en caracteres especiales del sistema como '..' o '/'. Tenga en cuenta también que las comprobaciones de seguridad para los caracteres especiales con frecuencia se producen antes de que la cadena se convierte a ANSI.  
  
 Asignación con ajuste perfecto es el valor predeterminado para la conversión no administrada, WChar en MB. A menos que deshabilite explícitamente la asignación con ajuste perfecto, el código podría contener una vulnerabilidad de seguridad explotable debido a este problema.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, explícitamente calcular las referencias de tipos de datos de cadena.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que infringe esta regla y, a continuación, se muestra cómo corregir la infracción.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]