---
title: "Soluci&#243;n de problemas de excepciones: System.Data.OleDb.OleDbException | Microsoft Docs"
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
  - "OLEDB"
  - "OleDbException (clase)"
  - "excepciones, OLEDB"
ms.assetid: f50077cf-e411-41f0-b73e-19eef83036c1
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.OleDb.OleDbException
Se genera una excepción <xref:System.Data.OleDb.OleDbException> cuando un origen de datos de OLE DB devuelve una advertencia o un error.  
  
## Sugerencias asociadas  
 **Compruebe que se está conectando con las credenciales válidas.**  
 Asegúrese de que las credenciales que está proporcionando son válidas. Para obtener más información, consulta <xref:System.Data.OleDb.OleDbErrorCollection>.  
  
 **Compruebe que el nombre del servidor es correcto y que se está ejecutando.**  
 Asegúrese de que está utilizando el nombre del servidor correcto y que el servidor es alcanzable. Para obtener más información, consulta <xref:System.Data.OleDb.OleDbErrorCollection>.  
  
### Comentarios  
 Esta excepción se produce siempre que el Proveedor de datos de .NET Framework para OLE DB encuentra un error generado por el servidor.  
  
 Si la gravedad del error es demasiado grande, el servidor puede cerrar <xref:System.Data.OleDb.OleDbConnection>. Sin embargo, el usuario puede volver a abrir la conexión y continuar.  
  
## Vea también  
 <xref:System.Data.OleDb.OleDbException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)