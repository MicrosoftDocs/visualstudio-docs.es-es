---
title: "La conexi&#243;n seleccionada usa un proveedor de bases de datos no admitido | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La conexi&#243;n seleccionada usa un proveedor de bases de datos no admitido
Este mensaje aparece al arrastrar elementos que no usan el proveedor de datos .NET Framework para servidor SQL Server desde el **Explorador de servidores**\/**Explorador de bases de datos** hasta el [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] admite únicamente conexiones de datos que usan el Proveedor de .NET Framework para servidor SQL Server.Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.  
  
### Para corregir este error  
  
-   Agregue únicamente elementos de las conexiones de datos que usen el proveedor de datos .NET Framework para servidor SQL Server al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Vea también  
 <xref:System.Data.SqlClient>   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/es-es/360c340d-e5a6-4a7e-a569-e95d500be43d)   
 [Proveedores de datos .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Crear aplicaciones de datos](../data-tools/creating-data-applications.md)