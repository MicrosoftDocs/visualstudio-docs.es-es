---
title: Tener acceso directamente a la base de datos con un TableAdapter | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a592a185ad3dd01f881526e0b9471e3f5e969a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178456"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Acceder directamente a la base de datos con un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Además el `InsertCommand`, `UpdateCommand`, y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Estos métodos (`TableAdapter.Insert`, `TableAdapter.Update`, y `TableAdapter.Delete`) se puede llamar para manipular los datos directamente en la base de datos.  
  
 Si no desea crear estos métodos directos, establezca el TableAdapter `GenerateDbDirectMethods` propiedad `false` en el **propiedades** ventana. Si las consultas se agregan a un TableAdapter además de la consulta principal del TableAdapter, son consultas independientes que no generan estos DbDirect (métodos).  
  
## <a name="sendcommandsdirectly-to-a-database"></a>Sendcommandsdirectly a una base de datos  
 Llame al método DbDirect de TableAdapter que realiza la tarea que intente llevar a cabo.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>Para insertar nuevos registros directamente en una base de datos  
  
-   Llamar a del TableAdapter `Insert` método, pasando los valores para cada columna como parámetros. El siguiente procedimiento usa la `Region` muestra un ejemplo de tabla en la databaseas de Northwind.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>Para actualizar registros directamente en una base de datos  
  
-   Llamar a del TableAdapter `Update` método, pasando los valores nuevos y originales de cada columna como parámetros.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>Para eliminar registros directamente desde una base de datos  
  
-   Llamar a del TableAdapter `Delete` método, pasando los valores de cada columna como parámetros de la `Delete` método. El siguiente procedimiento usa la `Region` muestra un ejemplo de tabla en la databaseas de Northwind.  
  
    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

