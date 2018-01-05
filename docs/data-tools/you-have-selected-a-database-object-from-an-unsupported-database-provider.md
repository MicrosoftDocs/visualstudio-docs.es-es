---
title: Ha seleccionado un objeto de base de datos de un proveedor de base de datos no admitido | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 85a8e5883a8d78297336016ac295f9b5d76ce337
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
Object Relational Designer admite únicamente el proveedor de datos de .NET Framework para SQL Server (<xref:System.Data.SqlClient>). Aunque puede hacer clic en **Aceptar** y continuar trabajando con objetos de proveedores de base de datos no compatible, puede experimentar un comportamiento inesperado en tiempo de ejecución.  
  
> [!NOTE]
>  Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Haga clic en **Aceptar**.

   Puede continuar diseñando las clases de entidad que se asignan a la conexión que utiliza el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.  
  
     O bien  
  
- Haga clic en **cancelar**.

   Se detiene la acción. Cree o utilice una conexión de datos que use el Proveedor de .NET Framework para servidor SQL Server.  
  
## <a name="see-also"></a>Vea también
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)