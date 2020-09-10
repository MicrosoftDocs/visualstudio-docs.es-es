---
title: Proveedor de base de datos no admitido
description: La conexión seleccionada usa un proveedor de base de datos que no se admite
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9ff4120796a40da00e258026d8db84ba6e9dbb21
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89743267"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite

Este mensaje aparece cuando se arrastran elementos que no usan el proveedor de datos de .NET Framework para SQL Server de **Explorador de servidores** o **Explorador de bases de datos** en las [herramientas de LINQ to SQL de Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Object Relational **Designer** solo admite las conexiones de datos que usan el proveedor de .NET Framework para SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.

Para corregir este error, agregue solo los elementos de las conexiones de datos que usan el proveedor de datos de .NET Framework para SQL Server a Object Relational **Designer**.

## <a name="see-also"></a>Vea también

- <xref:System.Data.SqlClient>
- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
