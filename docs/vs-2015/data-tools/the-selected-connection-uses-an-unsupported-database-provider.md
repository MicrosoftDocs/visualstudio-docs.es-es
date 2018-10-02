---
title: La conexión seleccionada usa un proveedor de base de datos no admitidos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4e38bda495521bf81c6eb4b9a00a0f32620a71fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567057"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [la conexión seleccionada usa un proveedor de base de datos no admitido](https://docs.microsoft.com/visualstudio/data-tools/the-selected-connection-uses-an-unsupported-database-provider).  
  
  
Este mensaje aparece cuando se arrastran elementos que no usan el proveedor de datos de .NET Framework para SQL Server desde **Explorador de servidores**/**Database Explorer** hasta la [LINQ to SQL Herramientas de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).  
  
 El [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] admite únicamente conexiones de datos que usan el Proveedor de .NET Framework para servidor SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue únicamente elementos de las conexiones de datos que usen el proveedor de datos .NET Framework para servidor SQL Server al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Data.SqlClient>   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Proveedores de datos de .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Crear aplicaciones de datos](../data-tools/creating-data-applications.md)

