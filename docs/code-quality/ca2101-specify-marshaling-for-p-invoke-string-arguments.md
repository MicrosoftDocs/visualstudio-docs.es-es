---
title: "CA2101: Especifique c&#225;lculo de referencias para argumentos de cadena P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2101: Especifique c&#225;lculo de referencias para argumentos de cadena P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|Identificador de comprobación|CA2101|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un miembro de invocación de plataforma permite llamadores que no son de plena confianza y no calcula explícitamente las referencias a la cadena.  
  
## Descripción de la regla  
 Cuando convierte de Unicode a ANSI, es posible que no todos los caracteres Unicode se puedan representar en una página de códigos ANSI concreta.  *Mejor asignación* intenta resolver este problema sustituyendo un carácter por el carácter que no se puede representar.  El uso de esta característica se puede producir una vulnerabilidad de seguridad potencial porque no se puede controlar el carácter que se elige.  Por ejemplo, el código malintencionado puede crear una cadena Unicode que contenga caracteres que no se encuentran en ninguna página de códigos concreta y que se convierten el caracteres especiales del sistema como '..' o '\/'.  Observe además que las comprobaciones de seguridad para los caracteres especiales normalmente aparecen antes de que la cadena se convierta a ANSI.  
  
 La mejor asignación es el valor predeterminado para la conversión no administrada, de WChar a Mbyte.  A menos que deshabilite explícitamente la mejor asignación, el código podría contener una vulnerabilidad de seguridad explotable debido a este problema.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, calcule las referencias de los tipos de datos de cadena explícitamente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que infringe esta regla y, a continuación, muestra cómo corregir la infracción.  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]