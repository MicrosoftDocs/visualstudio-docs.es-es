---
title: "CA1800: No convertir innecesariamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1800"
  - "DoNotCastUnnecessarily"
helpviewer_keywords: 
  - "DoNotCastUnnecessarily"
  - "CA1800"
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1800: No convertir innecesariamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|Identificador de comprobación|CA1800|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un método realiza conversiones de tipos duplicadas en uno de sus argumentos o variables locales.  Para obtener un análisis completo utilizando esta regla, el ensamblado probado se debe compilar mediante la información de depuración y el archivo de base de datos de programa asociado \(.pdb\) debe estar disponible.  
  
## Descripción de la regla  
 Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas.  Para obtener conversiones de tipos duplicadas de forma explícita, almacene el resultado de la conversión en una variable local y utilícela en lugar de las operaciones de conversión de tipos duplicadas.  
  
 Si el operador `is` de C\# se utiliza para comprobar si la conversión se ha realizado correctamente antes de realizar la conversión actual, considere comprobar el resultado del operador `as` en su lugar.  Esto proporciona la misma funcionalidad sin la operación de conversión implícita realizada por el operador `is`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, modifique la implementación del método para minimizar el número de operaciones de la conversión de tipos.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla, u omitir la regla, si el rendimiento no es importante.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método que infringe la regla mediante el operador `is` de C\#.  Un segundo método cumple la regla reemplazando el operador `is` con una comparación con el resultado del operador `as`, que disminuye el número de operaciones de conversión por iteración de dos a una.  
  
 [!code-cs[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente muestra un método, `start_Click`, con múltiples conversiones de tipos explícitas duplicadas, que infringe la regla, y un método, `reset_Click`, que cumple la regla almacenando la conversión en una variable local.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-cs[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## Vea también  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)