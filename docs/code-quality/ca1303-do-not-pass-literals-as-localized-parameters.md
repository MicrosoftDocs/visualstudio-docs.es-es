---
title: "CA1303: No pasar literales como par&#225;metros localizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: No pasar literales como par&#225;metros localizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|Identificador de comprobación|CA1303|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|No|  
  
## Motivo  
 Un método pasa un literal de cadena como parámetro a un constructor o método de la biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] y esa cadena debe ser localizable.  
  
 Esta advertencia se desencadena cuando una cadena literal se pasa como un valor a un parámetro o propiedad y uno o varios de los casos siguientes son verdaderos:  
  
-   El atributo <xref:System.ComponentModel.LocalizableAttribute> del parámetro o propiedad está establecido en true.  
  
-   El parámetro o el nombre de propiedad contiene "Text", "Message" o "Caption".  
  
-   El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".  
  
## Descripción de la regla  
 Los literales de cadena que se incrustan en el código fuente son difíciles de adaptar.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el literal de cadena con una cadena recuperada mediante una instancia de la clase <xref:System.Resources.ResourceManager>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la biblioteca de código no se adapta o si la cadena no se expone al usuario final o a un programador que utilice la biblioteca de códigos.  
  
 Los usuarios pueden eliminar ruido de los métodos que no deben pasar cadenas localizables ya sea cambiando el nombre del parámetro o de la propiedad, o marcando estos elementos como condicionales.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que produce una excepción cuando cualquiera de sus dos argumentos está fuera del intervalo.  En el primer argumento, se pasa una cadena literal al constructor de excepción, que infringe esta regla.  En el segundo argumento, se pasa correctamente al constructor una cadena recuperada mediante <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-cs[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## Vea también  
 [Recursos de aplicaciones de escritorio](../Topic/Resources%20in%20Desktop%20Apps.md)