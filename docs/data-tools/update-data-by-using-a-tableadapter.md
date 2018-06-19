---
title: Actualizar datos utilizando un TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fba0258839af6675f07c0962ee4281516dce3295
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31921581"
---
# <a name="update-data-by-using-a-tableadapter"></a>Actualizar datos utilizando un TableAdapter

Después de modificar y validar los datos del conjunto de datos, puede devolver los datos actualizados a una base de datos mediante una llamada a la `Update` método de un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). El `Update` método actualiza una tabla de datos única y se ejecuta el comando correcto (INSERT, UPDATE o DELETE) basándose en el <xref:System.Data.DataRow.RowState%2A> de cada fila de datos en la tabla. Cuando un conjunto de datos con tablas relacionadas, Visual Studio genera una clase TableAdapterManager que usar para realizar las actualizaciones. La clase TableAdapterManager garantiza que las actualizaciones se realizan en el orden correcto basándose en las restricciones de clave externa que se definen en la base de datos. Cuando utilice controles enlazados a datos, la arquitectura de enlace de datos crea una variable de miembro de la clase de TableAdapterManager denominada tableAdapterManager.

> [!NOTE]
> Al intentar actualizar un origen de datos con el contenido de un conjunto de datos, puede obtener errores. Para evitar errores, se recomienda que coloque el código que llama el adaptador `Update` método dentro de un `try` / `catch` bloque.

 El procedimiento exacto para actualizar un origen de datos puede variar según las necesidades del negocio, pero incluye los siguientes pasos:

1.  Llame el adaptador `Update` método en un `try` / `catch` bloque.

2.  Si se detecta una excepción, buscar la fila de datos que causó el error.

3.  Resuelva el problema de los datos de fila (mediante programación si es posible, o presentando la fila incorrecta al usuario para la modificación) y, a continuación, inténtelo de nuevo la actualización (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Guardar datos en una base de datos

Llame a la `Update` método de un TableAdapter. Pase el nombre de la tabla de datos que contiene los valores que se escriban en la base de datos.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para actualizar una base de datos utilizando un TableAdapter

-   Incluya el TableAdapter`Update` método en un `try` / `catch` bloque. En el ejemplo siguiente se muestra cómo actualizar el contenido de la `Customers` tabla `NorthwindDataSet` desde una `try` / `catch` bloque.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)