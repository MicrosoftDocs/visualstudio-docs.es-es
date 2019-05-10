---
title: La conexión seleccionada usa un proveedor de base de datos que no se admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5fab6be50a9b4c273a7bb911d8afde5cf65d7676
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460579"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>La conexión seleccionada usa un proveedor de base de datos que no se admite

Este mensaje aparece cuando se arrastran elementos que no usan el proveedor de datos de .NET Framework para SQL Server desde **Explorador de servidores** o **Database Explorer** hasta la [de LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

El **Object Relational Designer** admite conexiones de datos que usan el proveedor de .NET Framework para SQL Server. Solamente son válidas las conexiones a Microsoft SQL Server o Archivo de base de datos de Microsoft SQL Server.

Para corregir este error, agregue únicamente elementos de las conexiones de datos que usan el proveedor de datos de .NET Framework para SQL Server para la **Object Relational Designer**.

## <a name="see-also"></a>Vea también

- <xref:System.Data.SqlClient>
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
