---
title: La conexión seleccionada usa un proveedor de base de datos no admitidos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0a242cfb937d53be8a9acb61d9523c28544eef8f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662067"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este mensaje aparece cuando se arrastran elementos que no usan el proveedor de datos de .NET Framework para SQL Server desde **Explorador de servidores**/**Database Explorer** hasta la [LINQ to SQL Herramientas de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] admite únicamente conexiones de datos que usan el Proveedor de .NET Framework para servidor SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue únicamente elementos de las conexiones de datos que usen el proveedor de datos .NET Framework para servidor SQL Server al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.SqlClient>   
 [Proveedores de datos de .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)