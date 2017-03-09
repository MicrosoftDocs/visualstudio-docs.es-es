---
title: "Soluci&#243;n de problemas de excepciones: System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "StackOverflowException (clase)"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.StackOverflowException
Si la pila de ejecución se desborda debido a un número excesivo de llamadas anidadas a los métodos, se produce una excepción <xref:System.StackOverflowException>.  
  
## Sugerencias asociadas  
 Asegúrese de que no tiene un bucle infinito o recursividad infinita.  
 A menudo, un gran número de llamadas a método indican una recursividad muy profunda o ilimitada.  
  
## Comentarios  
 Las excepciones de desbordamiento de pila no se pueden detectar porque el código del control de excepciones puede requerir la pila. Cuando se produce un desbordamiento de pila en una aplicación normal, Common Language Runtime \(CLR\) finaliza el proceso.  
  
 Una aplicación que hospeda CLR puede cambiar el comportamiento predeterminado y especificar que CLR descargue el dominio de aplicación donde se produce la excepción, pero deja que continúe el proceso. Para obtener más información, consulta [ICLRPolicyManager \(Interfaz\)](../Topic/ICLRPolicyManager%20Interface.md).  
  
## Vea también  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Estructuras de bucles](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)