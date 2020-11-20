---
title: Objeto de proveedor no admitido
description: Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido. Vea información sobre este mensaje de Visual Studio (Object Relational Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f4f4a24e085cf4d268512ca90e5d1b3205abc9fe
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998167"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido

Object Relational **Designer** solo admite el proveedor de datos de .NET Framework para SQL Server ( <xref:System.Data.SqlClient> ). Aunque se puede hacer clic en **Aceptar** y continuar trabajando con objetos de un proveedor de base de datos no admitido, es posible que se produzca un comportamiento inesperado en tiempo de ejecución.

> [!NOTE]
> Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.

## <a name="options"></a>Opciones

- Haga clic en **Aceptar** para seguir designando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.

- Haga clic en **Cancelar** para detener la acción. Cree o use una conexión de datos diferente que use el proveedor de .NET Framework para SQL Server.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
