---
title: "Soluci&#243;n de problemas de excepciones: System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "SqlException (clase)"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Soluci&#243;n de problemas de excepciones: System.Data.SqlClient.SqlException
Cuando SQL Server devuelve una advertencia o un error, se genera una excepción <xref:System.Data.SqlClient.SqlException>.  
  
## Sugerencias asociadas  
 **Compruebe que se está conectando con las credenciales válidas.**  
 Asegúrese de que las credenciales que está proporcionando son válidas. Para obtener más información, consulta [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md).  
  
 **Compruebe que el nombre del servidor es correcto y que se está ejecutando.**  
 Asegúrese de que está utilizando el nombre del servidor correcto y que el servidor es alcanzable.  
  
### Comentarios  
 Esta excepción se produce siempre que el proveedor de datos de .NET Framework para SQL Server encuentra un error generado por el servidor.  
  
 Los mensajes con un nivel de gravedad de 10 o menos son informativos e indican problemas ocasionados por errores en la información proporcionada por un usuario. Los errores con un nivel de gravedad entre 11 y 16 los genera el usuario y él mismo puede corregirlos. Los niveles de gravedad entre 17 y 25 indican errores de software o hardware. Cuando se produce un error de nivel 17, 18 o 19, puede seguir trabajando, aunque tal vez no pueda ejecutar una instrucción determinada.  
  
 La conexión <xref:System.Data.SqlClient.SqlConnection> permanece abierta cuando el nivel de gravedad es 19 o inferior. Cuando el nivel de gravedad es 20 o superior, normalmente el servidor cierra la conexión <xref:System.Data.SqlClient.SqlConnection>. Sin embargo, el usuario puede volver a abrir la conexión y continuar. En ambos casos, el método que ejecuta el comando genera una excepción <xref:System.Data.SqlClient.SqlException>.  
  
 Para obtener información sobre los mensajes de advertencia e informativos enviados por SQL Server, consulte la sección Solución de problemas de Libros en pantalla de SQL Server.  
  
## Vea también  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)