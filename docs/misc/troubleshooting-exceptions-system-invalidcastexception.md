---
title: "Soluci&#243;n de problemas de excepciones: System.InvalidCastException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "InvalidCastException (clase)"
ms.assetid: a855dfe1-5c06-45a6-9c2f-c9e799ccf8f0
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.InvalidCastException
Cuando se produce un error durante una conversión de referencia explícita, se produce una excepción <xref:System.InvalidCastException>. Las conversiones de referencia son conversiones de un tipo de referencia a otro. A pesar de que pueden cambiar el tipo de la referencia, nunca cambian el tipo o valor del destino de la conversión. La conversión de objetos de un tipo a otro es una causa frecuente de esta excepción.  
  
## Sugerencias asociadas  
 **Compare los tipos de origen con los tipos de destino para asegurarse de que la conversión es válida.**  
 Para obtener información sobre las conversiones compatibles con el sistema, vea <xref:System.Convert>.  
  
## Comentarios  
 Para que una conversión de referencia explícita sea correcta, el valor de origen debe ser Null \(`Nothing` en Visual Basic\) o el tipo de objeto al que hace referencia el argumento de origen debe poder convertirse al tipo de destino mediante una conversión de referencia implícita.  
  
 Cuando una aplicación de Visual Basic 6.0 con una llamada a un evento personalizado en un control de usuario se actualiza a una nueva versión de Visual Basic y se ejecuta, es posible que esta excepción se produzca con la información adicional, "La conversión especificada no es válida". Para corregir este error, encuentre la línea de código siguiente en  `Form1`:  
  
 `Call UserControl11_MyCustomEvent(UserControl11, New UserControl1.MyCustomEventEventArgs(5))`  
  
 Y reemplácela con:  
  
 `Call UserControl11_MyCustomEvent(UserControl11(0), New UserControl1.MyCustomEventEventArgs(5))`  
  
## Vea también  
 <xref:System.InvalidCastException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Cómo: Convertir un objeto en otro tipo en Visual Basic](../Topic/How%20to:%20Convert%20an%20Object%20to%20Another%20Type%20in%20Visual%20Basic.md)   
 [Convertir cadenas en tipos de datos de .NET Framework](../Topic/Converting%20Strings%20to%20.NET%20Framework%20Data%20Types.md)   
 [Cómo: Implementar conversiones definidas por el usuario entre structs](../Topic/How%20to:%20Implement%20User-Defined%20Conversions%20Between%20Structs%20\(C%23%20Programming%20Guide\).md)