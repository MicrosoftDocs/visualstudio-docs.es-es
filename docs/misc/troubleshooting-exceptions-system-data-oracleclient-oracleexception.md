---
title: "Soluci&#243;n de problemas de excepciones: System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "OracleException (clase)"
  - "Oracle"
  - "excepciones, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.OracleClient.OracleException
Se genera una excepción <xref:System.Data.OracleClient.OracleException> cuando la base de datos de Oracle o el Proveedor de datos de .NET Framework para Oracle devuelve una advertencia o un error.  
  
## Sugerencias asociadas  
 **Compruebe que se está conectando con las credenciales válidas.**  
 Asegúrese de que las credenciales que está proporcionando son válidas.  
  
 **Compruebe que el nombre del servidor es correcto y que se está ejecutando.**  
 Asegúrese de que está utilizando el nombre del servidor correcto y que el servidor es alcanzable.  
  
## Comentarios  
 Esta excepción se produce siempre que <xref:System.Data.OracleClient.OracleDataAdapter> encuentra un error generado por el servidor.  
  
 Si la gravedad del error es demasiado grande, el servidor puede cerrar <xref:System.Data.OracleClient.OracleConnection>. Sin embargo, el usuario puede volver a abrir la conexión y continuar.  
  
## Vea también  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)