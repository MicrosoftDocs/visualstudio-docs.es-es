---
title: Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: dae92f404bb9ecb23b77dbda33c329994b9ed15b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457879"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido

El **Object Relational Designer** admite solo el proveedor de datos de .NET Framework para SQL Server (<xref:System.Data.SqlClient>). Aunque se puede hacer clic en **Aceptar** y continuar trabajando con objetos de un proveedor de base de datos no admitido, es posible que se produzca un comportamiento inesperado en tiempo de ejecución.

> [!NOTE]
> Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.

## <a name="options"></a>Opciones

- Haga clic en **Aceptar** para seguir designando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.

- Haga clic en **cancelar** para detener la acción. Crear o usar una conexión de datos diferente que utiliza el proveedor de .NET Framework para SQL Server.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)