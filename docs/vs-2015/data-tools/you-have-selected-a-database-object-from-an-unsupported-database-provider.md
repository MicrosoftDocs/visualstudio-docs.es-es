---
title: Ha seleccionado un objeto de base de datos de un proveedor de base de datos no admitidos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c225e00a6d303bff16e30fabd2f3e8e0e9d40ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581268"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Ha seleccionado un objeto de base de datos de un proveedor de bases de datos no admitido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [documentación de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
El [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) admite únicamente el proveedor de datos de .NET Framework para SQL Server (<xref:System.Data.SqlClient>). Aunque puede hacer clic en **Aceptar** y seguir trabajando con objetos de proveedores de base de datos no admitido, puede experimentar un comportamiento inesperado en tiempo de ejecución.  
  
> [!NOTE]
>  Se admiten únicamente las conexiones de datos que usan el proveedor de datos .NET Framework para SQL Server.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Haga clic en **Aceptar** para seguir diseñando las clases de entidad que se asignan a la conexión que usa el proveedor de base de datos no admitido. Puede que se produzca un comportamiento inesperado cuando se usan proveedores de base de datos no admitidos.  
  
     O bien  
  
-   Haga clic en **cancelar**.  
  
     Se detiene la acción. Cree o utilice una conexión de datos que use el Proveedor de .NET Framework para servidor SQL Server.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Proveedores de datos de .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)

