---
title: "Soluci&#243;n de problemas de excepciones: System.Net.Sockets.SocketException | Microsoft Docs"
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
  - "SocketException (clase)"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Net.Sockets.SocketException
Las clases <xref:System.Net.Sockets.SocketException> y <xref:System.Net.Sockets.Socket> producen una excepción <xref:System.Net.Dns> cuando se produce un error en la red.  
  
## Sugerencias asociadas  
 **Compruebe la propiedad ErrorCode para determinar por qué hubo un error de socket.**  
 El constructor predeterminado para la clase <xref:System.Net.Sockets.SocketException> establece la propiedad <xref:System.Net.Sockets.SocketException.ErrorCode%2A> en el último error de socket que se produjo en el sistema operativo.  
  
## Vea también  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Usar la capa de sockets seguros](../Topic/Using%20Secure%20Sockets%20Layer.md)