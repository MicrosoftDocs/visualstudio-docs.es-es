---
title: "Soluci&#243;n de problemas de excepciones: System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException (clase)"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Net.HttpListenerException
Se produce una excepción <xref:System.Net.HttpListenerException> cuando se produce un error al procesar una solicitud de Protocolo de transferencia de hipertexto.  
  
## Sugerencias asociadas  
 Compruebe si el prefijo URI que está intentando registrar ya está registrado.  
 Se producirá esta excepción en caso de que el prefijo URI ya esté registrado.  
  
 Asegúrese de que la solicitud HTTP sea válida.  
 La clase <xref:System.Net.HttpListener> y sus clases asociadas producen esta excepción cuando se produce un error durante la inicialización del objeto <xref:System.Net.HttpListener> o mientras se crea o se envía una respuesta a una solicitud HTTP.  
  
 Si está utilizando el método `HttpListenerPrefixCollection.Add`, compruebe que no se haya agregado aún el prefijo `uriPrefix`.  
 Se producirá esta excepción si otro objeto <xref:System.Net.HttpListener> ya ha agregado el prefijo `uriPrefix`.  
  
## Vea también  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)