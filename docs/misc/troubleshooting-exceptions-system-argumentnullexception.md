---
title: "Soluci&#243;n de problemas de excepciones: System.ArgumentNullException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "ArgumentNullException (clase)"
ms.assetid: 5f21413c-d997-47c6-9b06-3d85a719d51b
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.ArgumentNullException
Una excepción <xref:System.ArgumentNullException> se produce cuando se pasa una referencia NULL \(`Nothing` en Visual Basic\) a un método que no lo acepta como un argumento válido.  
  
## Sugerencias asociadas  
 **Compruebe los argumentos para asegurarse de que no son NULL \(Nothing en Visual Basic\).**  
 Una referencia NULL es una referencia a un objeto que no existe, a menudo porque no se ha creado mediante programación ninguna instancia del objeto.  
  
## Comentarios  
 <xref:System.ArgumentNullException> se comporta idénticamente a <xref:System.ArgumentException>. Se proporciona de manera que el código de aplicación puede diferenciar entre excepciones producidas por los argumentos NULL y las producidas por argumentos que no son NULL. Para errores producidos por argumentos que no son NULL, vea [Solución de problemas de excepciones: System.ArgumentOutOfRangeException](../misc/troubleshooting-exceptions-system-argumentoutofrangeexception.md).  
  
## Vea también  
 <xref:System.ArgumentNullException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)