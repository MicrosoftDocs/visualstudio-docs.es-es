---
title: "CA1025: Reemplaza argumentos repetitivos con una matriz de par&#225;metros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1025"
  - "ReplaceRepetitiveArgumentsWithParamsArray"
helpviewer_keywords: 
  - "ReplaceRepetitiveArgumentsWithParamsArray"
  - "CA1025"
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1025: Reemplaza argumentos repetitivos con una matriz de par&#225;metros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|Identificador de comprobación|CA1025|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método público o protegido de un tipo público tiene más de tres parámetros, y los últimos tres parámetros son el mismo tipo.  
  
## Descripción de la regla  
 Utilice una matriz de parámetros de argumentos repetidos cuando se conoce el número exacto de argumentos y los argumentos de variable sean del mismo tipo o puedan pasarse como si fueran del mismo tipo.  Por ejemplo, el método <xref:System.Console.WriteLine%2A> proporciona una sobrecarga de propósito general que utiliza una matriz de parámetros para aceptar cualquier número de argumentos <xref:System.Object>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace los argumentos repetidos con una matriz de parámetros.  
  
## Cuándo suprimir advertencias  
 Siempre es seguro suprimir una advertencia de esta regla; sin embargo, este diseño podría provocar problemas de uso.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-cs[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]