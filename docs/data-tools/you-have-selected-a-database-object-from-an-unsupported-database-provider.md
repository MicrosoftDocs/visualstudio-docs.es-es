---
title: "Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
[!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\) admite únicamente el proveedor de datos .NET Framework para SQL Server \(<xref:System.Data.SqlClient>\).Aunque se puede hacer clic en **Aceptar** y continuar trabajando con objetos de un proveedor de base de datos no admitido, es posible que se produzca un comportamiento inesperado en tiempo de ejecución.  
  
> [!NOTE]
>  Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.  
  
### Para corregir este error  
  
-   Haga clic en **Aceptar** para seguir diseñando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido.Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.  
  
     O bien,  
  
-   Haga clic en **Cancelar**.  
  
     Se detiene la acción.Cree o utilice una conexión de datos que use el Proveedor de .NET Framework para servidor SQL Server.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Proveedores de datos .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)