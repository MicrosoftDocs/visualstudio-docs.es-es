---
title: "Soluci&#243;n de problemas de excepciones: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SqlCeInvalidDatabaseFormatException (excepción)"
  - "System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException (excepción)"
ms.assetid: f5ca1f40-4619-4523-807e-d5b20bfb05b0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException
Se produce una excepción `System.Data.SqlServerCe.SqlCeInvalidDatabaseFormatException` cuando SQL Server Compact abre un archivo de base de datos creado en una versión anterior del producto.  
  
## Comentarios  
 Puede actualizar el archivo de base de datos utilizando [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] o el objeto `System.Data.SqlServerCe.SqlCeEngine.Upgrade` de la API.  
  
 Para más información, vea [Biblioteca de clases de SQL Server Compact 3.5](http://go.microsoft.com/fwlink/?LinkID=102595).  
  
## Vea también  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)