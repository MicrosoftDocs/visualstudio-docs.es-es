---
title: Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b6eef41ebd3ae6fc08029a618cf276e22001235
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37116885"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido

El **Object Relational Designer** admite solo el proveedor de datos de .NET Framework para SQL Server (<xref:System.Data.SqlClient>). Aunque puede hacer clic en **Aceptar** y seguir trabajando con objetos de proveedores de base de datos no admitido, puede experimentar un comportamiento inesperado en tiempo de ejecución.

> [!NOTE]
> Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.

## <a name="to-correct-this-error"></a>Para corregir este error

- Haga clic en **Aceptar**.

   Puede seguir diseñando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.

    O bien

- Haga clic en **cancelar**.

   Se detiene la acción. Cree o utilice una conexión de datos que use el Proveedor de .NET Framework para servidor SQL Server.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)