---
title: "CA1820: Comprobar si las cadenas est&#225;n vac&#237;as mediante la longitud de cadena | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1820: Comprobar si las cadenas est&#225;n vac&#237;as mediante la longitud de cadena
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|Identificador de comprobación|CA1820|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una cadena se compara con la cadena vacía utilizando <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 La comparación de cadenas utilizando la propiedad <xref:System.String.Length%2A?displayProperty=fullName> o el método <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> es significativamente más rápida que si se utilizara <xref:System.Object.Equals%2A>.  Esto es porque <xref:System.Object.Equals%2A> ejecuta de forma significativa más instrucciones de MSIL que <xref:System.String.IsNullOrEmpty%2A> o el número de instrucciones ejecutado para recuperar el valor de propiedad <xref:System.String.Length%2A> y compararlo con cero.  
  
 Debería ser consciente de que <xref:System.Object.Equals%2A> y <xref:System.String.Length%2A> \=\= 0 se comportan de manera diferente para las cadenas nulas.  Si intenta obtener el valor de la propiedad <xref:System.String.Length%2A> en una cadena nula, el Common Language Runtime produce una <xref:System.NullReferenceException?displayProperty=fullName>.  Si realiza una comparación entre una cadena vacía y una nula, el Common Language Runtime no produce una excepción, sino que la comparación devuelve `false`.  La comprobación de cadenas nulas no afecta significativamente al rendimiento relativo de estos dos enfoques.  Cuando el destino es [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilice el método <xref:System.String.IsNullOrEmpty%2A>.  De lo contrario, utilice la comparación <xref:System.String.Length%2A> \=\= siempre que sea posible.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, modifique la comparación para utilizar la propiedad <xref:System.String.Length%2A> y comprobar la cadena nula.  Si el destino es [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilice el método <xref:System.String.IsNullOrEmpty%2A>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el rendimiento no supone un problema.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran las diferentes técnicas que se utilizan para buscar una cadena vacía.  
  
 [!code-cs[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]