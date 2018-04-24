---
title: La conexión seleccionada usa un proveedor de base de datos que no se admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2f4d2ce764f4824fdcff897c1dab542a53f80e0f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite

Este mensaje aparece cuando se arrastran elementos que no utilizan el proveedor de datos de .NET Framework para SQL Server desde **Explorador de servidores**/**el Explorador de base de datos** en el [LINQ to SQL Herramientas de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

El [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] admite únicamente conexiones de datos que usan el Proveedor de .NET Framework para servidor SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.

Para corregir este error, agregue únicamente elementos de las conexiones de datos que utilizan el proveedor de datos de .NET Framework para SQL Server para el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Vea también

- <xref:System.Data.SqlClient>
- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
