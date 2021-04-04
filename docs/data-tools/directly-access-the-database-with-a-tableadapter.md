---
title: Acceder directamente a la base de datos con un TableAdapter
description: Acceder directamente a una base de datos con un TableAdapter mediante métodos como INSERT, Update y DELETE para manipular los datos directamente en la base de datos.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 30248632eacde07cfcc94213aeeb75ecac8dcf70
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215921"
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

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet15":::

### <a name="to-update-records-directly-in-a-database"></a>Para actualizar registros directamente en una base de datos

- Llame al método del TableAdapter `Update` , pasando los valores nuevos y originales de cada columna como parámetros.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet18":::

### <a name="to-delete-records-directly-from-a-database"></a>Para eliminar registros directamente de una base de datos

- Llame al método del TableAdapter `Delete` , pasando los valores de cada columna como parámetros del `Delete` método. En el procedimiento siguiente se utiliza la `Region` tabla de la base de datos Northwind como ejemplo.

    > [!NOTE]
    > Si no tiene una instancia disponible, cree una instancia del TableAdapter que desee usar.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb" id="Snippet21":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs" id="Snippet21":::

## <a name="see-also"></a>Consulte también

- [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
