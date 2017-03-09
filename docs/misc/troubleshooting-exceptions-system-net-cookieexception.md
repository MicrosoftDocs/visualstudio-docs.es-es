---
title: "Soluci&#243;n de problemas de excepciones: System.Net.CookieException | Microsoft Docs"
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
  - "CookieException (clase)"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Net.CookieException
Cuando se comete un error al agregar una cookie a un contenedor de cookies, se produce una excepción <xref:System.Net.CookieException>.  
  
## Sugerencias asociadas  
 **Asegúrese de que el tamaño de la cookie no supere el máximo permitido por el contenedor de cookies.**  
 Esta excepción se produce cuando se intenta agregar una <xref:System.Net.Cookie> cuya longitud es mayor que el valor de <xref:System.Net.CookieContainer.MaxCookieSize%2A> a un objeto <xref:System.Net.CookieContainer>. El tamaño máximo predeterminado de la cookie es de 4.096 bytes.  
  
 **Al establecer la propiedad Name para una cookie, asegúrese de que el valor no sea una referencia nula ni una cadena vacía.**  
 La propiedad <xref:System.Net.Cookie.Name%2A> debe inicializarse antes de utilizar una instancia de la clase <xref:System.Net.Cookie>. Los caracteres siguientes están reservados y no pueden utilizarse para este valor de atributo: signo igual, punto y coma, coma, nueva línea \(\\n\), retorno de carro \(\\r\), tabulación \(\\t\). El signo de dólar \($\) no puede ser el primer carácter.  
  
 **Al establecer la propiedad Port para una cookie, asegúrese de que el valor sea válido y esté entre comillas dobles.**  
 El atributo <xref:System.Net.Cookie.Port%2A> restringe los puertos a los que se puede enviar una cookie. El valor predeterminado es sin restricción. Al establecer la propiedad en una cadena vacía \(""\), el puerto se restringe al que se utiliza en la respuesta HTTP. De lo contrario, el valor debe ser una cadena entre comillas que contenga los valores de puerto delimitados con comas.  
  
 **Al establecer la propiedad Value para una cookie, asegúrese de que el valor no sea nulo.**  
 Los caracteres siguientes están reservados y no pueden utilizarse para esta propiedad: punto y coma, coma.  
  
## Vea también  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)