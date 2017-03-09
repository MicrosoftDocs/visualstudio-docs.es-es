---
title: "Soluci&#243;n de problemas de excepciones: System.ArgumentOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
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
  - "ArgumentOutOfRangeException (clase)"
ms.assetid: f53c58d9-7c4e-407f-93d3-1e59d90d98f5
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ArgumentOutOfRangeException
Cuando se invoca un método y al menos uno de los argumentos que se pasan a dicho método no es una referencia nula \(<xref:System.ArgumentOutOfRangeException> en Visual Basic\) y no contiene un valor válido, se produce una excepción `Nothing`.  
  
## Sugerencias asociadas  
 **Asegúrese de que todos los argumentos de este método tengan valores válidos, tal como lo define el método invocado.**  
 Los argumentos que no son referencias nulas deben contener valores válidos.  
  
 **Si está trabajando con una colección, asegúrese de que el índice sea menor que el tamaño de la colección.**  
 El índice debe estar dentro del intervalo de tamaño de la colección y no puede superar el intervalo de tamaño ni ser menor que cero. Para obtener más información, consulta [Colecciones](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
 **Cuando utilice los métodos sobrecargados de dos argumentos FindString o FindExactString con ComboBox o ListBox, compruebe el parámetro startIndex**.  
 Es posible que se produzca esta excepción si `startIndex` es igual al valor de índice del último elemento de la lista asociada. Para evitar esto, pase 0 como parámetro `startIndex` o utilice `FindString` de un argumento o el método `FindStringExact`. Para obtener más información, vea [CComboBox::FindString](../Topic/CComboBox::FindString.md) o [CListBox::FindString](../Topic/CListBox::FindString.md).  
  
## Vea también  
 <xref:System.ArgumentOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)