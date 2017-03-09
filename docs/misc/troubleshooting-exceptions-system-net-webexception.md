---
title: "Soluci&#243;n de problemas de excepciones: System.Net.WebException | Microsoft Docs"
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
  - "WebException (clase)"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Net.WebException
Si se produce un error al obtener acceso a la red mediante un protocolo conectable, se produce una excepción <xref:System.Net.WebException>.  
  
## Sugerencias asociadas  
 **Compruebe la propiedad Response de la excepción para determinar por qué hubo un error en la solicitud.**  
 Cuando un descendiente de la clase <xref:System.Net.WebException> produce una excepción <xref:System.Net.WebRequest>, la propiedad <xref:System.Net.WebException.Response%2A> proporciona la respuesta de Internet a la aplicación.  
  
 **Compruebe la propiedad Status de la excepción para determinar por qué hubo un error en la solicitud.**  
 La propiedad <xref:System.Net.WebException.Status%2A> de la excepción proporciona información de estado sobre el error. Para obtener más información, consulta <xref:System.Net.WebExceptionStatus>.  
  
 **Si se agota el tiempo de espera cuando a un servicio Web XML, establezca el valor de tiempo de espera de la llamada al servicio Web XML en infinito.**  
 Para obtener más información, consulta [Error: Se excedió el tiempo de espera de depuración de servicios Web](../debugger/error-timeout-while-debugging-web-services.md).  
  
## Vea también  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Cómo enviar datos mediante la clase WebRequest](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Cómo solicitar datos mediante la clase WebRequest](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Cómo: recuperar una WebResponse específica de protocolo que coincida con una WebRequest](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)