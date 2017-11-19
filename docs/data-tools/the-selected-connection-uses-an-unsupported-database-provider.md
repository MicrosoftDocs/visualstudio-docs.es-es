---
title: "La conexión seleccionada usa un proveedor de base de datos no admitido | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 956f6ab5180475bf0abb03e4353fe0343f876ae1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
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
