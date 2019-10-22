---
title: Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitidas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a4407eba52ec3940b70ffab220ef354af90e9d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657787"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) solo admite el proveedor de datos de .NET Framework para SQL Server (<xref:System.Data.SqlClient>). Aunque se puede hacer clic en **Aceptar** y continuar trabajando con objetos de un proveedor de base de datos no admitido, es posible que se produzca un comportamiento inesperado en tiempo de ejecución.

> [!NOTE]
> Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.

### <a name="to-correct-this-error"></a>Para corregir este error

- Haga clic en **Aceptar** para seguir designando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.

     o bien

- Haga clic en **Cancelar**.

     Se detiene la acción. Cree o utilice una conexión de datos que use el Proveedor de .NET Framework para servidor SQL Server.

## <a name="see-also"></a>Vea también
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [proveedores de datos .NET Framework](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)