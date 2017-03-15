---
title: "Soluci&#243;n de problemas de excepciones: System.Data.Odbc.OdbcException | Microsoft Docs"
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
  - "EHOdbc"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "excepciones, ODBC"
  - "ODBC, excepciones"
  - "OdbcException (clase)"
ms.assetid: 5f2c2167-cf7b-4634-af86-44dc71eff02d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.Odbc.OdbcException
Se genera una excepción <xref:System.Data.Odbc.OdbcException> cuando un origen de datos de ODBC devuelve una advertencia o un error.  
  
## Sugerencias asociadas  
 **Compruebe que se está conectando con las credenciales válidas.**  
 Compruebe sus credenciales para asegurarse de que son válidas.  
  
 **Compruebe que el nombre del servidor es correcto y que se está ejecutando.**  
 Asegúrese de que está utilizando el nombre del servidor correcto y que el servidor es alcanzable.  
  
## Comentarios  
 Esta excepción se produce siempre que <xref:System.Data.Odbc.OdbcDataAdapter> encuentra un error generado por el servidor.  
  
 Si la gravedad del error es demasiado grande, el servidor puede cerrar <xref:System.Data.Odbc.OdbcConnection>. Sin embargo, el usuario puede volver a abrir la conexión y continuar.  
  
## Vea también  
 <xref:System.Data.Odbc.OdbcException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)