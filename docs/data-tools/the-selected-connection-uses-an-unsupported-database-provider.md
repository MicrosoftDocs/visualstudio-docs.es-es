---
title: La conexión seleccionada usa un proveedor de base de datos no admitido | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 199bd6ba18f9ac2e7eecbc13868c8c4bc8e829f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite
Este mensaje aparece cuando se arrastran elementos que no utilizan el proveedor de datos de .NET Framework para SQL Server desde **Explorador de servidores**/**el Explorador de base de datos** en el [LINQ to SQL Herramientas de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] admite únicamente conexiones de datos que usan el Proveedor de .NET Framework para servidor SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue únicamente elementos de las conexiones de datos que usen el proveedor de datos .NET Framework para servidor SQL Server al [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## <a name="see-also"></a>Vea también
<xref:System.Data.SqlClient>  
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
