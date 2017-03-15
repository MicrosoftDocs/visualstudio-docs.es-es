---
title: "Soluci&#243;n de problemas de excepciones: System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException (clase)"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Security.VerificationException
Si la directiva de seguridad requiere código para tener seguridad de tipos y el proceso de comprobación no puede comprobar que el código tiene seguridad de tipos, se produce una excepción <xref:System.Security.VerificationException>.  
  
## Sugerencias asociadas  
 Asegúrese de que la aplicación no carga dos versiones contradictorias de una biblioteca de clases.  
 Como parte del proceso de comprobación, se comprueba la seguridad de tipos de MSIL \(Lenguaje intermedio de Microsoft\) para garantizar que los objetos están aislados de forma segura entre sí y están, por tanto, seguros ante daños accidentales o malintencionados. Para más información, vea [Seguridad y protección de tipos](http://msdn.microsoft.com/es-es/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc).  
  
## Vea también  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)