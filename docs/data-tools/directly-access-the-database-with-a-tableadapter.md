---
title: Tener acceso directamente a la base de datos con un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b1a3b35cc491ed91e07316444c31cf4a29ef1517
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Tener acceso directamente a la base de datos con un TableAdapter
Además el `InsertCommand`, `UpdateCommand`, y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Estos métodos (`TableAdapter.Insert`, `TableAdapter.Update`, y `TableAdapter.Delete`) se puede llamar para manipular los datos directamente en la base de datos.

 Si no desea crear estos métodos directos, establezca el TableAdapter `GenerateDbDirectMethods` propiedad `false` en el **propiedades** ventana. Si ninguna de las consultas se agrega a un TableAdapter además de la consulta principal del TableAdapter, son consultas independientes que no generan estos métodos DbDirect.

## <a name="send-commands-directly-to-a-database"></a>Enviar comandos directamente a una base de datos
 Llame al método DbDirect de TableAdapter que realiza la tarea que intente llevar a cabo.

#### <a name="to-insert-new-records-directly-into-a-database"></a>Para insertar nuevos registros directamente en una base de datos

-   Llamar a del TableAdapter `Insert` método, pasando los valores de cada columna como parámetros. El siguiente procedimiento usa el `Region` tabla en la base de datos de Northwind como un ejemplo.

    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

#### <a name="to-update-records-directly-in-a-database"></a>Para actualizar registros directamente en una base de datos

-   Llamar a del TableAdapter `Update` método, pasando los valores nuevos y originales de cada columna como parámetros.

    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

#### <a name="to-delete-records-directly-from-a-database"></a>Para eliminar registros directamente desde una base de datos

-   Llamar a del TableAdapter `Delete` método, pasando los valores de cada columna como parámetros de la `Delete` método. El siguiente procedimiento usa el `Region` tabla en la base de datos de Northwind como un ejemplo.

    > [!NOTE]
    >  Si no tiene una instancia disponible, cree una instancia del TableAdapter que desea usar.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Vea también

- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)