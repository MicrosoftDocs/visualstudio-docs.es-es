---
title: "Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolicyValidationException (excepción)"
  - "System.IdentityModel.Selectors.PolicyValidationException (excepción)"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.IdentityModel.Selectors.PolicyValidationException
Se produce una excepción <xref:System.IdentityModel.Selectors.PolicyValidationException> cuando no se puede validar la directiva proporcionada por el destinatario. Para obtener más información sobre los requisitos de la directiva, vea [A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkID=102401).  
  
 Cualquier contenido no válido de una directiva puede producir este error. Entre los problemas habituales con el contenido de las directivas se incluyen los siguientes:  
  
-   Tipo de clave no válido  
  
-   Tamaño de clave no válido  
  
-   XML no válido  
  
-   No se especifican notificaciones en la directiva \(debe especificarse al menos una notificación no opcional\)  
  
## Vea también  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)