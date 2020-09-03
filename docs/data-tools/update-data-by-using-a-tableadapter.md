---
title: Actualizar datos mediante un TableAdapter
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f7ecca8c28ff355952907f1f0c49485117a25456
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281206"
---
# <a name="update-data-by-using-a-tableadapter"></a>Actualizar datos mediante un TableAdapter

Una vez que los datos del conjunto de datos se han modificado y validado, puede devolver los datos actualizados a una base de datos llamando al `Update` método de un [TableAdapter](../data-tools/create-and-configure-tableadapters.md). El `Update` método actualiza una sola tabla de datos y ejecuta el comando correcto (insertar, actualizar o eliminar) en función de la <xref:System.Data.DataRow.RowState%2A> de cada fila de datos de la tabla. Cuando un conjunto de elementos tiene tablas relacionadas, Visual Studio genera una clase TableAdapterManager que se usa para realizar las actualizaciones. La clase TableAdapterManager garantiza que las actualizaciones se realicen en el orden correcto en función de las restricciones Foreign Key definidas en la base de datos. Cuando se usan controles enlazados a datos, la arquitectura de enlace de datos crea una variable miembro de la clase TableAdapterManager denominada tableAdapterManager.

> [!NOTE]
> Al intentar actualizar un origen de datos con el contenido de un conjunto de datos, puede obtener errores. Para evitar errores, se recomienda colocar el código que llama al método del adaptador `Update` dentro de un `try` / `catch` bloque.

El procedimiento exacto para actualizar un origen de datos puede variar en función de las necesidades empresariales, pero incluye los pasos siguientes:

1. Llame al método del adaptador `Update` en un `try` / `catch` bloque.

2. Si se detecta una excepción, buscar la fila de datos que causó el error.

3. Reconciliar el problema en la fila de datos (mediante programación si puede, o presentando la fila no válida al usuario para su modificación) y, a continuación, vuelva a intentar la actualización ( <xref:System.Data.DataRow.HasErrors%2A> , <xref:System.Data.DataTable.GetErrors%2A> ).

## <a name="save-data-to-a-database"></a>Guardar datos en una base de datos

Llame al `Update` método de un TableAdapter. Pase el nombre de la tabla de datos que contiene los valores que se van a escribir en la base de datos.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para actualizar una base de datos mediante un TableAdapter

- Incluya el método del TableAdapter `Update` en un `try` / `catch` bloque. En el ejemplo siguiente se muestra cómo actualizar el contenido de la `Customers` tabla en `NorthwindDataSet` desde dentro de un `try` / `catch` bloque.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
