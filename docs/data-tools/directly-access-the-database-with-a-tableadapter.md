---
title: Acceder directamente a la base de datos con un TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 22d84e9b4beafd64cc629a295bcfa7f9f67afb6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282571"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>Acceder directamente a la base de datos con un TableAdapter

Además de los `InsertCommand` `UpdateCommand` TableAdapters, y `DeleteCommand` , se crean con métodos que se pueden ejecutar directamente en la base de datos. Puede llamar a estos métodos ( `TableAdapter.Insert` , `TableAdapter.Update` y `TableAdapter.Delete` ) para manipular los datos directamente en la base de datos.

Si no desea crear estos métodos directos, establezca la propiedad del TableAdapter en `GenerateDbDirectMethods` `false` en la ventana **propiedades** . Si se agregan consultas a un TableAdapter además de a la consulta principal del TableAdapter, son consultas independientes que no generan estos `DbDirect` métodos.

## <a name="send-commands-directly-to-a-database"></a>Enviar comandos directamente a una base de datos

Llame al `DbDirect` método TableAdapter que realiza la tarea que está intentando realizar.

### <a name="to-insert-new-records-directly-into-a-database"></a>Para insertar nuevos registros directamente en una base de datos

- Llame al método del TableAdapter `Insert` , pasando los valores de cada columna como parámetros. En el procedimiento siguiente se utiliza la `Region` tabla de la base de datos Northwind como ejemplo.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]

### <a name="to-update-records-directly-in-a-database"></a>Para actualizar registros directamente en una base de datos

- Llame al método del TableAdapter `Update` , pasando los valores nuevos y originales de cada columna como parámetros.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]

### <a name="to-delete-records-directly-from-a-database"></a>Para eliminar registros directamente de una base de datos

- Llame al método del TableAdapter `Delete` , pasando los valores de cada columna como parámetros del `Delete` método. En el procedimiento siguiente se utiliza la `Region` tabla de la base de datos Northwind como ejemplo.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]

## <a name="see-also"></a>Vea también

- [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
