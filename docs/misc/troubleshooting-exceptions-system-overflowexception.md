---
title: "Soluci&#243;n de problemas de excepciones: System.OverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OverflowException (clase)"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.OverflowException
Cuando una operación aritmética o de conversión de un contexto protegido provoca un desbordamiento, se produce una excepción <xref:System.OverflowException>. El desbordamiento se produce cuando una operación genera un valor demasiado grande para el tipo de destino, infinito o No es un número \(NaN\).  
  
## Sugerencias asociadas  
 **Cuando realiza la conversión de un número, el valor debe ser un número menor que infinito.**  
 Un valor de origen no puede ser infinito o No es un número.  
  
 **Asegúrese de que no está dividiendo por cero.**  
 Dividir por cero normalmente producirá esta excepción.  
  
## Comentarios  
 En lenguajes que detectan el desbordamiento, <xref:System.OverflowException> es la excepción que se produce cuando aparece el desbordamiento. Por ejemplo, en C\#, la palabra clave `checked` se utiliza para detectar las condiciones de desbordamiento. Una excepción <xref:System.OverflowException> sólo se produce en un contexto protegido.  
  
 Para obtener un resultado de una conversión u operación aritmética de tipo decimal o integral que se encuentre fuera del intervalo del tipo de destino:  
  
-   En un contexto protegido, se produce un error de compilación si la operación es una expresión constante. De lo contrario, se produce una excepción <xref:System.OverflowException> si la operación se realiza en tiempo de ejecución.  
  
-   En un contexto sin comprobar, se produce un truncamiento del resultado al descartar los bits de orden superior que no caben en el tipo de destino.  
  
 Para obtener información sobre los intervalos de valores de los tipos de datos, vea [Tipos de datos](/dotnet/visual-basic/language-reference/data-types/data-type-summary), [Tabla de tipos enteros](/dotnet/csharp/language-reference/keywords/integral-types-table) o [Tabla de tipos de punto flotante](/dotnet/csharp/language-reference/keywords/floating-point-types-table).  
  
## Vea también  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)